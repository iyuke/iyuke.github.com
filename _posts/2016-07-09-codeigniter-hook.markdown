---
layout:    	 	post
title:      	CodeIgniter 钩子
subtitle:   	CodeIgniter Hooks
card-image: 	
date:       	2016-07-09 23:00:00
tags:       	code
post-card-type: article
---

## 简介

CodeIgniter 在启动的过程中，可以在某个地方让它自动的执行自己编写的函数，完成一个特定的功能，或者说成是脚本，这个时候就需要 CodeIgniter 中的钩子扩展。突然觉得和 Spring 中的 AOP 面向切面（Aspect）很类似，就是说在系统执行的什么时候会自动的执行其他功能代码，例如Before(前) 、
After-returning(返回后) 、After-throwing(抛出后)、Introduction(引入)。

## 启用钩子

1. 在 application/config/config.php 文件里找到 $config['enable_hooks'] = FALSE,将 FALSE 改 TRUE ，启动钩子。

	```php
	$config['enable_hooks'] = TRUE;
	```

2. 在 application/hooks 文件夹(没有自已新建)新建一任意文件名 TestHook.php 。

	```php
	<?php
	class TestHook{
	    function display(){
	          echo "Hello Hook";
	    }
	}
	?>
	```

3. 回到 application/config/hooks.php 里添加几行代码如下：

	```php
	$hook['pre_controller'] = array(
	    'class'    => 'MyClass',
	    'function' => 'Myfunction',
	    'filename' => 'Myclass.php',
	    'filepath' => 'hooks',
	    'params'   => array('beer', 'wine', 'snacks')
	);
	// 注意
	// 这里可以同时定义多个钩子，只需要另起一段编写类似的代码即可。
	// 只需要将钩子数组变成二维数组即可。
	```

Demo:

>
```php
// TestHook.php
<?php
class TestHook{
    function display(){
          echo "Hello Hook";
    }
}
?>
```
>
```php
// application/config/hooks.php
$hook['post_controller'][] = array(
	'class' => 'TestHook',
	'function' => 'display',
	'filename' => 'TestHook.php',
	'filepath' => 'hooks',
	'params'   => array()
);
```

**注意：**

* class 你希望调用的类名，如果你更喜欢使用过程式的函数的话，这一项可以留空。
* function 你希望调用的方法或函数的名称。
* filename 包含你的类或函数的文件名。
* filepath 包含你的脚本文件的目录名。 注意： 你的脚本必须放在 application/ 目录里面，所以 filepath 是相对 application/ 目录的路径，举例来说，如果你的脚本位于 application/hooks/ ，那么 filepath 可以简单的设置为 'hooks' ，如果你的脚本位于 application/hooks/utilities/ ， 那么 filepath 可以设置为 'hooks/utilities' ，路径后面不用加斜线。
* params 你希望传递给你脚本的任何参数，可选。

## 挂钩点

* pre_system 在系统执行的早期调用，这个时候只有 基准测试类 和 钩子类 被加载了， 还没有执行到路由或其他的流程。
* pre_controller 在你的控制器调用之前执行，所有的基础类都已加载，路由和安全检查也已经完成。
* post_controller_constructor 在你的控制器实例化之后立即执行，控制器的任何方法都还尚未调用。
* post_controller 在你的控制器完全运行结束时执行。
* display_override 覆盖 \_display() 方法，该方法用于在系统执行结束时向浏览器发送最终的页面结果。 这可以让你有自己的显示页面的方法。注意你可能需要使用 $this->CI =& get_instance() 方法来获取 CI 超级对象，以及使用 $this->CI->output->get_output() 方法来 获取最终的显示数据。
* cache_override 使用你自己的方法来替代 输出类 中的 \_display_cache() 方法，这让你有自己的缓存显示机制。
* post_system 在最终的页面发送到浏览器之后、在系统的最后期被调用。
