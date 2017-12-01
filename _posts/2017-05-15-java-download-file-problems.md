---
layout:         post
title:          记一次文件下载的尬途
subtitle:       
card-image:     
date:           2017-05-15 19:00:00
tags:           code
post-card-type: article
---

这两天有个需求就是说将线上的信息通过计算后导入到 Excel 文件中，之后并可提供下载，下载后这个文件就不需要存在服务器上了，只要用户成功下载后，文件爱怎么样怎么样。

好吧开始做吧。


## Java 文件下载

初步打算做法如下：

1. 异步请求（需求所需，不是重点），通过 java 计算，将数据写入到 Excel 文件，并保存到服务器；
2. 然后下载文件；

哦，除了计算，写入到有 47 列的 Excel 文件麻烦点，好像没什么了。。。开始码代码了。

1. 首先将文件写入到服务器的磁盘下；
2. 然后发起一个 http 请求从服务器上下载文件，简单代码如下：

    ```java
    /**
     * 文件下载
     *
     * @param uniqueId
     * @param response
     * @return
     */
    @RequestMapping(value = "/excels/{uniqueId}/download")
    public HttpServletResponse download(
            @PathVariable(value = "uniqueId") String uniqueId, HttpServletRequest request, HttpServletResponse response) {

        // ...

        File file = fileService.getFile(uniqueId);

        try {
            InputStream fis = new BufferedInputStream(new FileInputStream(file));
            byte[] buffer = new byte[fis.available()];
            fis.read(buffer);
            fis.close();
            response.reset();
            response.addHeader("Content-Disposition", "attachment;filename=" + new String(file.getName()));
            response.addHeader("Content-Length", "" + file.length());
            OutputStream toClient = new BufferedOutputStream(response.getOutputStream());
            response.setContentType("application/octet-stream");
            toClient.write(buffer);
            toClient.flush();
            toClient.close();
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            file.delete();
        }

        return response;
    }
    ```
3. 客户端发起一个 get 请求就可以将文件下载下来了，在日常环境和预发环境表现都是正常的；
4. 然后我就正式上线了，结果出问题了，有时候无法下载成功。

## 无法成功下载文件

那什么问题呢？

突然意识到，日常和预发环境都是一台机器，那么无论怎么读写文件都是在同一台机器上进行操作，而正式环境有两台机器，挂在一个 vip 下，那么我在请求计算数据的时候，会将 Excel 文件写入到一台服务器 A 中，那么第二次请求下载的时候，nginx 不一定会将请求转到写入文件的机器 A 上，可能是 A，也可能是 B，当请求到了B 服务器上，那么查找文件就自然不存在了。

考虑到这个文件的量不大，每个文件大的也就几 M，没有必要再引入文件服务器上，为了减少不必要的依赖，维护，那么就用 mysql 了，反正两台服务器访问的数据都是一个。

然后新建一个有关文件的表 t_files，大概表结果如下：

```
id, unique_id, name, content, create_time, create_by, deleted, update_time, udpate_by
```

那么在 mysql 里存储文件的时候又不能存储文件的路径，因为不一定文件会存在哪台机器上，还会出现那个问题，所以就将文件 Base64 编码后写入到 content 中，下次读取文件的时候再将 content decode 一下写入到文件中，这里 content 字段采用 TEXT 类型，那事实证明是可行的，但是我发现有的文件在下载后，无法正常打开，损坏了，原因是 TEXT 类型的字段存储长度过小，无法完整的存下信息。

```
LANGTEXT：4294967295/3=1431655765个汉字，14亿，存储空间占用：4294967295/1024/1024/1024=4G的数据；
MEDIUMTEXT:16777215/3=5592405个汉字，560万，存储空间占用：16777215/1024/1024=16M的数据；
TEXT：65535/3=21845个汉字，约20000，存储空间占用：65535/1024=64K的数据；
```
因为计算后的生成的文件之前也说过不会有超过 10M 的，就选择了 MEDIUMTEXT 类型，恩，就这样解决了刚刚的那个问题。

那在写代码的时候出现了一个问题，问题是，当我将文件 Base64 编码后，可以成功写入数据库，这里查找 t_files 我是根据 unique_id 作为主键进行查找的，但是我无法获取 content 内容，其他信息正常，只有 content 为空。我是使用 mybatis 作为 ORM 进行查询的，然后查看对应的 mapper.xml 文件后发现，对于 TEXT 类型的字段，和其他 VARCHAR 类型的字段是有区别的，mybatis 自动对 TEXT 类型进行了特殊处理，无法查找。解决办法如下：

1. 可以自己手写对应的 mapper 文件，生成对应的 SQL 语句；
2. 通过主键 id 进行查询 selectByPrimaryKey(id) 就可以将信息全部查到，这里我先通过 unique_id 将对象查出，然后又根据 id 重新查找了一次，解决了上面的问题。

好了，正式上线了。

**哦，是时候找个机会学习下集群、分布式的问题了。**
