## 一、canvas画布

#### 1、什么是SVG？ 

​	SVG是一种可伸缩的矢量图型，它基于XML并用于描述图形的语言； 

​	不同于用像素来描绘的矩阵图像（JPG、PNG、GIF），SVG是和分辨率无关的； 

​	SVG图像可以通过JS和DOM操作来创建和操控； 

​	SVG有自己庞大的语法和较大的复杂度，我们这里只是了解下有这种图像格式；

#### 2、基本概念

canvas：画布，h5新标签；

1. canvas本身没有任何外观，只是在文档中创建了一个画板；
2. ie9之前的版本不支持canvas；
3. 画布的宽度和高度要用canvas的属性设置，不要直接在css里面定义；
4. 画布的`getContext()`方法返回一个“绘制上下文”对象； 
   绝大多数的画布绘制API来自这个对象；
   也就是说画布元素和他的上下文对象是两个完全不同的概念；
   调用该方法时，传递的参数是“2d”，也就是`getContext('2d')`，可以在画布上绘制二维图像；
   3d绘制就相对比较复杂了，具体实现还在规范中；

#### 3、**画布的尺寸和坐标：** 

–     画布以左上角(0, 0)为坐标原点；

–     往右为X轴的坐标不断增大；

–     往下为Y轴的坐标不断增大；

#### 4、绘制线段和填充多边形：

​	1.绘制线段的API是上下文对象的方法；

​	2.beginPath：开始定义一条新的路径；

​	3.moveTo：开始定义一条新的子路径，该方法确定了线段的起点；

​	4.lineTo：将上面定义的线段起点和指定的新的点连接起来；

​	5.到这里只是规划好了思路，还没有在画布上画出任何图形；

​	6.fill()：填充区域，此时只是填充，起点和终点并没有连接起来；

​	7.closePath：会把起点和终点连接起来；

​	8.stroke()：开始绘制图形，当前路径下的所有子路经都会绘制出来；

​	9.如果要接着绘制新的路径，记得调用beginPath()方法；

#### 5、矩形的绘制

（1）rect()：在当前子路经添加一条弧线；

​	语法：context.rect(x,y,width,height);

​	四个参数： 起点坐标x,y：左上角坐标； 宽度width：矩形的宽度； 高度height：矩形的高度；

（2）strokeRect()方法可以直接绘制一个矩形；

​	语法：context.strokeRect(x,y,width,height);

#### 6、图形属性

图形属性：画布API给上下文对象定义了15个图形属性：

| 属性                     | 含义                                                         |
| ------------------------ | ------------------------------------------------------------ |
| lineWidth                | 线段的宽度                                                   |
| strokeStyle              | 勾勒线段时的颜色、渐变或图案等样式                           |
| lineCap                  | 如何渲染线段的末端，三个值：butt（默认，向线条的每个末端添加平直的边缘）、round（向线条的每个末端添加圆形线帽）、square（向线条的每个末端添加正方形线帽） |
| lineJoin                 | 如何渲染线段的顶点，三个值：bevel（创建斜角）、round（创建圆角）、miter（默认值，创建尖角） |
| miterLimit               | 紧急倾斜定点的最大长度（只有当 lineJoin 属性为 "miter" 时，miterLimit 才有效）；如果斜接长度超过 miterLimit 的值，边角会以 lineJoin 的 "bevel" 类型来显示。 |
| fillStyle                | 填充时候的颜色、渐变或图案等样式                             |
| font                     | 绘制文本时的字体（context.font = '40px sans-serif';）        |
| globalAlpha              | 绘制像素时候要添加的透明度                                   |
| globalCompositeOperation | 如何合并新的像素点和下面的像素点                             |
| textAlign                | 文本水平对齐方式                                             |
| textBaseline             | 文本垂直对齐方式                                             |
| shadowBlur               | 阴影的清晰或模糊程度                                         |
| shadowColor              | 下拉阴影的颜色                                               |
| shadowOffsetX            | 阴影的水平偏移量                                             |
| shadowOffsetY            | 阴影的垂直偏移量                                             |

#### 7、曲线的绘制和填充

arc()：在当前子路经添加一条弧线；

语法：context.arc(x,y,r,sAngle,eAngle,counterclockwise);

| 参数               | 描述                                                         |
| :----------------- | :----------------------------------------------------------- |
| *x*                | 圆的中心的 x 坐标。                                          |
| *y*                | 圆的中心的 y 坐标。                                          |
| *r*                | 圆的半径。                                                   |
| *sAngle*           | 起始角，以弧度计。（弧的圆形的三点钟位置是 0 度）。          |
| *eAngle*           | 结束角，以弧度计。                                           |
| *counterclockwise* | 可选。规定应该逆时针还是顺时针绘图。False = 顺时针，true = 逆时针。 |

#### 8、绘制文本信息

| 方法                                                         | 描述                       |
| ------------------------------------------------------------ | -------------------------- |
| [fillText()](http://www.w3school.com.cn/tags/canvas_filltext.asp) | 在画布上绘制“被填充的”文本 |
| [strokeText()](http://www.w3school.com.cn/tags/canvas_stroketext.asp) | 在画布上绘制文本（无填充） |

​	三个参数： 绘制的内容； 起点x坐标； 起点y坐标；

​	文本颜色使用fillStyle属性指定；

​	文本字体使用font属性指定，和CSS一致；

​	textAlign属性指定水平方向对齐方式，可选值：start、left等，textBaseline则指定垂直方向，可选值：top、hanging等，参考下图：

![1559025843493](assets\1559025843493.png)



#### 9、图片

图片：

​	drawImage()：将原图片像素的内容复制到画布上；

​	第一个参数是源图片，可以是img元素或Image构造函数创建的屏幕外图片对象；

​	三个参数时： 指定图片绘制的x、y坐标；

​	五个参数时： 指定图片绘制的x、y坐标，以及图片的宽度、高度；

​	九个参数时： 裁剪的对象 裁剪的位置（x,y）; 裁剪的宽度和高度(w,h); 裁剪后图片绘制的位置(x,y); 图片显示出来的宽度和高度(w,h);

| 参数      | 描述                                         |
| --------- | -------------------------------------------- |
| *img*     | 规定要使用的图像、画布或视频。               |
| *sx*      | 可选。开始剪切的 x 坐标位置。                |
| *sy*      | 可选。开始剪切的 y 坐标位置。                |
| *swidth*  | 可选。被剪切图像的宽度。                     |
| *sheight* | 可选。被剪切图像的高度。                     |
| *x*       | 在画布上放置图像的 x 坐标位置。              |
| *y*       | 在画布上放置图像的 y 坐标位置。              |
| *width*   | 可选。要使用的图像的宽度。（伸展或缩小图像） |
| *height*  | 可选。要使用的图像的高度。（伸展或缩小图像） |

#### 10、清除画布指定元素

clearRect() 方法清空给定矩形内的指定像素 ；

JavaScript 语法：

```
context.clearRect(x,y,width,height);
```

| 参数     | 描述                         |
| -------- | ---------------------------- |
| *x*      | 要清除的矩形左上角的 x 坐标  |
| *y*      | 要清除的矩形左上角的 y 坐标  |
| *width*  | 要清除的矩形的宽度，以像素计 |
| *height* | 要清除的矩形的高度，以像素计 |

## 二、数据存储

#### 1、客户端存储-概念

1. web应用允许使用浏览器提供的API将数据存储在客户端电脑上；
2. 客户端存储遵守“同源策略”，不同的站点页面之间不能相互读取彼此的数据；
3. 在同一个站点的不同页面之间，存储的数据是共享的；
4. 数据的存储有效期可以是临时的，比如关闭浏览器数据就销毁； 也可以是永久的，可以在客户端电脑上存储任意时间；
5. 在使用数据存储是需要考虑安全问题，比如银行卡账号密码；
6. 数据的存储方式也有很多种，后面我们会一一讲到

#### 2、cookie

创建cookie：

​	document.cookie = 'age=20'； 

​	document.cookie = 'name=刘桐;max-age=' + 24 * 60 * 60 ；//指定cookie有效期

获取cookie：

 	var  myCookie = document.cookie；



```js
		//创建cookie
		function setCookie(cname, cvalue, exdays) {
            var d = new Date();
            d.setTime(d.getTime() + (exdays * 24 * 60 * 60 * 1000));
            var expires = "expires=" + d.toGMTString();
            document.cookie = cname + "=" + cvalue + "; " + expires+";path=/";
        }
        setCookie("name", 123,3)

		//获取cookie
        function getCookie(cname) {
            var name = cname + "=";
            var ca = document.cookie.split(';');
            for (var i = 0; i < ca.length; i++) {
                var c = ca[i].trim();
                if (c.indexOf(name) == 0) { return c.substring(name.length, c.length); }
            }
            return "";
        }
		//打印所有cookie
        console.log(document.cookie)

		//判断是否有某个cookie
        function checkCookie() {
            var user = getCookie("username");
            if (user != "") {
                alert("欢迎 " + user + " 再次访问");
            }
            else {
                user = prompt("请输入你的名字:", "");
                if (user != "" && user != null) {
                    setCookie("username", user, 30);
                }
            }
        }
```



#### 3、localStorage和sessionStorage

localStorage和sessionStorage是window的两个属性，他们代表同一个Storage对象；

localStorage和sessionStorage的API：

​	setItem()：将对应的名字和值传递进去，可以实现数据存储；

​	getItem()：将名字传递进去，可以获取对应的值；

​	removeItem()：将名字传递进去，可以删除对应的值；

​	clear()：删除所有的缓存值，不需要参数；

​	length：属性，获取键值对总数；

​	key()：传入位置数，获取存储的值的名字；

#### 4、localStorage：永久性保存

​	setItem(string key, value); //保存 
​	getItem(string key);//获取 
​	clear();//清空 
​	removeItem(sring key)//根据键得到值

#### 5、sessionStorage:关闭浏览器数据就自动全部删除

​	sessionStorage.length ：​返回一个整数，表示存储在 sessionStorage 对象中的数据项(键值对)数量。
​	sessionStorage.key(int index) ：返回当前 sessionStorage 对象的第index序号的key名称。若没有返null。
​	sessionStorage.getItem(string key) ：返回键名(key)对应的值(value)。若没有返回null。
​	sessionStorage.setItem(string key, string value) ：该方法接受一个键名(key)和值(value)作为参数，将键值对添加到存储中；如果键名存在，则更新其对应的值。
​	sessionStorage.removeItem(string key) ：将指定的键名(key)从 sessionStorage 对象中移除。
​	sessionStorage.clear() ：清除 sessionStorage 对象所有的项。

#### 6、localStorage和sessionStorage区别

localStorage和sessionStorage存储数据的有效期和作用域不同：

（1）localStorage

​	localStorage：存储的数据是永久的，当然用户可以清除这些缓存数据的； 比如清除历史记录就可以清除这些数据；

​	localStorage的作用域限制在文档源； 文档源由协议、域名、端口三者来确定；下面的URL就拥有不同的文档源：

​	http://www.hqyj.com    //协议http，域名www.hqyj.com

​	https://www.hqyj.com    //协议https，和上面不同

​	http://www.farsight.com.cn/    //和上面域名不同

​	http://www.farsight.com.cn:81/    //和上面端口不同，默认端口是80

​	这种情况下，localStorage存储的数据是不能相互访问的； 即便他们来自同一台服务器；

​	localStorage同源的文档之间可以相互访问和修改相同名称的数据；

​	localStorage受浏览器厂商的限制，chrome下存储的数据，360浏览器下不可访问； 会得到‘Invalid Date’；

（2）sessionStorage

​	sessionStorage存储的数据在窗口或标签关闭时，数据就会丢失； 在一个标签前进后退时数据不会丢失，这样我们就可以获取上次访问时产生的相关信息； 随着现代浏览器越来越强大，具体的声明周期还和浏览器功能有关；

​	sessionStorage在localStorage的同源策略基础上，有更严格的限制：

​	他还被限制在窗口中，意思是同一个窗口或标签页的不同页面之间可以共享sessionStorage；

​	但是不同的窗口或标签页之间不能共享sessionStorage，即便他们是同一个页面地址；

​	窗口是指顶级窗口，如果是多个iframe，他们之间共享sessionStorage；

#### 7、localStorage、sessionStorage、cookie三者的区别

（1）存储大小

​	cookie数据大小不能超过4k ； 

​	sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大；

（2）有效时间

​	localStorage 存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；

​	sessionStorage 数据在当前浏览器窗口关闭后自动删除；

​	cookie 设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭；

（3）数据与服务器之间的交互方式

​	cookie的数据会自动的传递到服务器，服务器端也可以写cookie到客户端；

​	sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存；
（4）作用域

​	localStorage的作用域限制在文档源的；

​	localStorage同源的文档之间可以相互访问和修改相同名称的数据；

​	localStorage受浏览器厂商的限制，chrome下存储的数据，360浏览器下不可访问； 会得到‘Invalid Date’；

​	sessionStorage在localStorage的同源策略基础之上，还有更严格的限制：

​		他还被限制在窗口中，意思是同一个窗口或标签页的不同页面之间可以共享sessionStorage；

​		但是不同的窗口或标签页之间不能共享sessionStorage，即便他们是同一个页面地址；

​		这里的窗口是顶级窗口，如果里面有多个iframe，他们之间共享sessionStorage；

