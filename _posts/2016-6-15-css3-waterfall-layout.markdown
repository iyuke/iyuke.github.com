---
layout:    		post
title:    	  	CSS3多列布局实现瀑布流
subtitle:   
card-image: 	https://ww1.sinaimg.cn/mw690/906cb9dbgw1fayoq6tylaj20ue0ggn35.jpg
date:       	2016-06-15 21:00:00
tags:       	code
post-card-type: image
---

HTML代码如下：

```html
<div class="container" id="container"></div>
<div id="imageContainer" class="container"></div>
```

CSS代码如下：

```css
		.container {
            padding : 20px;
            margin: 20px;

            border-bottom: 1px solid #EEEEEE;

            -webkit-column-count: 5;
            -webkit-column-gap: 10px;
            -webkit-column-rule: 5px;

            -moz-column-count: 5;
            -moz-column-gap: 20px;
            -moz-column-rule: 5px;

            /* ie */
             column-count: 5;
             column-gap: 20px;
             column-rule: 5px;
        }

        hr {
            margin : 20px 0;
            line-height : 20px;
        }

        .container .unit {
            margin-top : 10px;
        }

        .container .unit img {
            width : 100%;
            border-radius: 5px;
        }
```

JS代码如下：

```js
		var M = {};
		M.util = {
			bgColorArray : [
					'#00CCCC','#33FF99','#6600FF','#666699','#660099','#9933FF','#993333','#99CC66','#CC3333','#CC33FF',
				],
			imgArray : [
				'http://ebay01.qiniudn.com/0dd7912397dda144d679b625b0b7d0a20cf48631.jpg-medium',
				'http://ebay01.qiniudn.com/37d12f2eb9389b506e32b4588735e5dde6116eee.jpg-medium',
				'http://ebay01.qiniudn.com/472309f79052982227ecebc7d5ca7bcb0b46d4d3.jpg-medium',
				'http://ebay01.qiniudn.com/4e4a20a4462309f7d7426b97700e0cf3d7cad602.jpg-medium',
				'http://ebay01.qiniudn.com/63d0f703918fa0ec42ebb209249759ee3d6ddb82.jpg-medium',
				'http://ebay01.qiniudn.com/63d0f703918fa0ec4f8db709249759ee3d6ddb68.jpg-medium',
				'http://ebay01.qiniudn.com/730e0cf3d7ca7bcb2248eab7bc096b63f624a872.jpg-medium',
				'http://ebay01.qiniudn.com/7c1ed21b0ef41bd511e9caa553da81cb39db3d2c.jpg-medium',
				'http://ebay01.qiniudn.com/8326cffc1e178a8245d04e45f403738da877e863.jpg-medium',
				'http://ebay01.qiniudn.com/8694a4c27d1ed21b38d780e0af6eddc451da3f9c.jpg-medium'
			]
		};

		M.render = {
			renderColorBox : function() {
				var container = document.getElementById('container');

				var total = 10;
				var htmlArray = [];
				for (var i = 0; i < total; i++) {
					htmlArray.push('<div class="unit"></div>');
				};

				container.innerHTML = htmlArray.join('');

				var units = document.getElementsByClassName('unit');
				for (var length = units.length ,i = length - 1; i >= 0; i--) {
					var baseNumber = Math.floor(Math.random()*3+2);
					var unit = units[i];
					var finalHeight = baseNumber*50+'px';
					unit.style.height = finalHeight;
					unit.style.lineHeight = finalHeight;
					unit.style.backgroundColor = M.util.bgColorArray[i%10];		
				}
			},

			renderImageBox: function() {

				var imageContainer = document.getElementById('imageContainer');

				var containerHtmlArray = [];
				for (var imgLen = M.util.imgArray.length,i = imgLen - 1; i >= 0; i--) {
					containerHtmlArray.push('<div class="unit"><img src="' + M.util.imgArray[i]+'"></div>');
				};
				imageContainer.innerHTML = containerHtmlArray.join('');
			},
			render: function() {
				this.renderColorBox();
				this.renderImageBox();
			}
		};

		M.render.render();
```

效果如下：

![](https://ww1.sinaimg.cn/large/906cb9dbgw1f9ilrtrxm6j21kw0xutjw.jpg)
![](https://ww1.sinaimg.cn/large/906cb9dbgw1f9ilsf934oj21kw0xuarc.jpg)

---

转自[CSS3多列布局实现瀑布流](http://codepen.io/markahcn/pen/qJdHK)
