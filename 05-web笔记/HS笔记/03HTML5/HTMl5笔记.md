# 1、初始html5

### 1.1、HTML5新标签与特性

**注：兼容性 ie9以上**

HTML5，即超文本标记语言(HTML)第五次重大修改。HTML 5草案的前身名为Web Applications 1.0。於2004年被WHATWG提出，於2007年被W3C接纳，并成立了新的HTML工作团队。2008年1月22日，W3C发布了最新的HTML5工作草案，HTML工作组包括AOL、Apple、Google、IBM、 Microsoft、Mozilla、Nokia、Opera等数百个开发上。HTML5中增加了许多新特性，例如嵌入音频、视频和图片的函数、客户端存储数据、交互式文档等，通过制定如何处理所有HTML元素以及如何从错误中恢复的精确规则，HTML5进一步增强了互动性，并有效减少了开发成本。

​        设计目的：HTML5 的设计目的是为了在移动设备上支持多媒体。

​        手机端下载flash的速度和流量与pc端差距比较大，影响用户体验，由此出现一个类似微型操作系统的浏览器，支持更多新元素。

​        HTML5规范：结构标签进行页面布局，注意结构的语义化，并注意页面大纲的层级结构

​        HTML5新特性：新的特殊内容元素、新的表单控件，用于媒介回放的video和audio元素

判断浏览器是否支持HTML5：

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title></title>
        <style>
            table {width: 100%;}
        </style>
		<script>
        window.onload = function() {
            if (window.applicationCache) {
                alert("你的浏览器支持HTML5");
            } else {
                alert("你的浏览器不支持HTML5");
            }
        }
   		</script>
    </head>
    <body>
        
    </body>
</html>
```

### 1.2、字符设定

- <meta http-equiv="charset" content="utf-8">：HTML与XHTML中建议这样去写
- <meta charset="utf-8">：HTML5的标签中建议这样去写

### 1.3、结束标签的规范

​       不写结束标签不会报错，body也可以省略，但是不推荐

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
	</head>
	<body>
		<div>div1
		<div>div2
		<div>div3
		<div>div4
		<div>div5
		<div>div6
		<div>div7
		<div>div8
		<div>div9
		<div>div10
	
</html>
```



### 1.4、语义化标签的由来

在之前的HTML页面中，大家基本上都是用了Div+CSS的布局方式。而搜索引擎去抓取页面的内容的时候，它只能猜测你的某个Div内的内容是文章内容容器，或者是导航模块的容器，或者是作者介绍的容器等等。也就是说整个HTML文档结构定义不清晰，HTML5中为了解决这个问题，专门添加了：页眉、页脚、导航、文章内容等跟结构相关的结构元素标签。

<img src="./图片/01.png">

为了得到更好的结构，引入了下面的标签：

- section： 这个标签表示一个通用的文档或者应用程序节。它可以和 h1-h6 一起使用来表示文档结构。
- article： 这个标签表示文档内容的一个独立块，比如博客条目或者报纸上的文章。
- aside： 这个标签表示与页面其他部分略微相关的内容块。
- header： 这个标签表示一个节的头部。
- footer： 这个标签表示一个节的脚注，可以包含作者，版权等信息。
- nav： 这个标签表示用于导航文档的节。nav--navigation
- dialog： 这个标签可以用于标记会话。
- figure： 这个标签可以用于关联标题和某些嵌入内容，比如图表和视频。

# 2、常用新标签

HTML5的语义化标签以及属性，可以让开发者非常方便地实现清晰的web页面布局 

### 2.1、结构划分

- **header** 页眉 主要用于页面的头部的信息介绍，也可用于板块头部

- **footer**页脚  页面的底部 或者 版块底部

- **nav**导航 （包含链接的的一个列表）

- **article**：定义页面独立的内容区域,,article适用于独立性强的内容，如本身就是一篇文章、博客，或者用户的评论等 

- **section**：定义文档的节（section、区段），每个 <section> 一般都有一个主题思想，但未必一定要有 <h> 元素。

- **aside**：定义突出的引用、广告、侧边栏。

  ```html
  <header> 语义 :定义页面的头部  页眉</header>
  <nav>  语义 :定义导航栏 </nav> 
  <footer> 语义: 定义 页面底部 页脚</footer>
  <article> 语义:  定义文章</article>
  <section> 语义： 定义区域</section>
  <aside> 语义： 定义其所处内容之外的内容 侧边</aside>
  ```

  ![1553438865851](assets/1553438865851.png)

   [更多标签参考](http://www.w3school.com.cn/html5/html5_reference.asp)

  **总结**

  有了新的结构性的标签的标准，让HTML文档更加清晰，可阅读性更强。

### 2.2、语义化标签

- **datalist**:<datalist> 标签定义选项列表。请与 input 元素配合使用该元素，来定义 input 可能的值。datalist 及其选项不会被显示出来，它仅仅是合法的输入值列表。请使用 input 元素的 list 属性来绑定 datalist。

```html
<input list="cars" />
<datalist id="cars">
	<option value="BMW">
	<option value="Ford">
	<option value="Volvo">
</datalist>
```

- **time**:time标签对于布局是没有任何影响的，我们直接用一个span也一样可以实现。

```html
月份显示：
<time datetime="2014-3-21">2014年3月21日</time>

具体时间显示（采用24小时制）：
<time datetime="16:30">下午4点半</time>

结合显示（中间隔一个空格）：
<time datetime="2018-3-21 16:30">2018-3-21 16:30</time>

```

- **address**：代表联系信息，以斜体呈现。

```
<footer>
		<address>
			For more details, contact
			<a href=mailto:maym_cd@hqyj.com>马云</a>
		</address>
</footer>
```

- **mark**: 使用mark标签元素，可以高亮显示文档中的文字以达到醒目的效果。 

```html
<!DOCTYPE html>
  <html>
  <head>
 <meta charset=utf-8>
 	<title>使用Mark元素高亮显示文本</title>
      <style>
          mark {
              background-color:#00ff90; font-weight:bold;
          }
      </style>
 
 </head>
 <body>
 
     <article>
         <header>
             <h1>百科</h1>
         </header>
         <p>百度百科是一部内容开放、自由的网络<mark>百科</mark>全书,旨在创造一个涵盖所有领域知识,服务所有互联网用户的中文知识性<mark>百科</mark>全书。在这里你可以参与词条编辑,分享贡献你的知识</p>
     </article>
 </body>
 </html>
```

- **progress**  :表示定义一个进度条，用途很广泛，可以用在文件上传的进度显示，文件下载的进度显示，也可以作为一种loading的加载状态条使用。 

```html
<progress value='70' max='100'></progress>
```



### 2.3、新增的input type属性值：

<!-- 注释：Internet Explorer、Firefox 或者 Chrome 不支持 <input type="datetime"> 元素，Safari 中部分支持。Opera 12 以及更早的版本中完全支持。 -->

| **类型**     | **使用示例**            | **含义**             |
| ------------ | ----------------------- | -------------------- |
| **email**    | <input type="email">    | 输入邮箱格式         |
| **tel**      | <input type="tel">      | 输入手机号码格式     |
| **url**      | <input type="url">      | 输入url格式          |
| **number**   | <input type="number">   | 输入数字格式         |
| **search**   | <input type="search">   | 搜索框（体现语义化） |
| **range**    | <input type="range">    | 自由拖动滑块         |
| **time**     | <input type="time">     | 小时分钟             |
| **date**     | <input type="date">     | 年月日               |
| **datetime** | <input type="datetime"> | 时间                 |
| **month**    | <input type="month">    | 月年                 |
| **week**     | <input type="week">     | 星期 年              |

兼容性http://www.w3school.com.cn/html5/html_5_form_input_types.asp



### 2.4、常用新属性

#### 2.4.1、新增的input type属性值

之前用到的type类型有:text、password、radio、checkbox、button、submit、reset、image、file

下述新增特性须与form标签、提交动作组合使用，才能完成类型校验。

| 类型            | 使用示例                | 含义                                                         |
| --------------- | ----------------------- | ------------------------------------------------------------ |
| **email**       | <input type="email">    | 输入邮箱格式，如：字符**<u>@</u>**字符                       |
| **url**         | <input type="url">      | 输入url格式，如：英文字符<u>**://**</u>字符                  |
| **number**      | <input type="number">   | 输入数字格式，只能是数字；属性：min,max,step                 |
| **search**      | <input type="search">   | 搜索框（自带清空按钮）                                       |
| **range**       | <input type="range">    | 自由拖动滑块，值默认0~100                                    |
| **time**        | <input type="time">     | 小时分钟                                                     |
| **date**        | <input type="date">     | 年月日                                                       |
| **datetime**    | <input type="datetime"> | 时间，也可用作 datetime-local，无显视格式限制                |
| **month**       | <input type="month">    | 年月                                                         |
| **week**        | <input type="week">     | 星期 年                                                      |
| **color**       | <input type="color">    | 颜色（选择基本颜色后启动选择器，确定特定颜色后，再在画板上点击确定） |
| **hidden/show** | <input type="hidden">   | 定义表单隐藏/显示，与js定义hidden属性true/false对应          |

基础体验：

```html
<form action="">
	邮箱：<input type="email"><br><br>
	url： <input type="url"><br><br>
	数字：<input type="number" min="10"  max="100" step="5"><br><br>
	搜索：<input type="search"><br><br>
	滑块：<input type="range" ><br><br>
	时分：<input type="time"><br><br>
	年月日：<input type="date"><br><br>
    时间：<input type="datetime"><br><br>
	年月：<input type="month"><br><br>
	星期：<input type="week"><br><br>
	颜色：<input type="color"><br><br>
	<input type="submit">
</form>
```



#### 2.4.2、新增控件常用属性

autocomplete: input历史记录的功能,on是打开,off是关闭. 默认为on. 说白了就是是否让浏览器自动记录之前输入的值. 

http://www.w3school.com.cn/tiy/t.asp?f=html5_input_autocomplete

| 属性             | 用法                                            | 含义                                                         |
| ---------------- | ----------------------------------------------- | ------------------------------------------------------------ |
| **placeholder**  | <input type="text" placeholder="请输入用户名" > | 占位符 用于提示用户输入，当用户输入数据时，提示信息会自动消失 |
| **autofocus**    | <input type="text"  autofocus>                  | 规定当页面加载时input元素应该自动获得焦点，例：百度注册页面  |
| **multiple**     | <input type="file" multiple>                    | 多文件上传                                                   |
| **autocomplete** | <input type="text" autocomplete="off">          | 规定表单是否应该启用自动完成功能，有两个值分别是on和off，on表示记录已经输入的值，默认on值 。条件是：1.表单需要有提交按钮    2.autocomplete元素必须给name值 |
| **required**     | <input type="text" required>                    | 必填项，内容不能为空                                         |

### 2.5、多媒体标签

- audio：播放音频
- video：播放视频

#### 2.5.1、多媒体 video

HTML5通过<audio>标签来解决音频播放的问题。

同音频播放一样，<video>使用也相当简单，如下图

![1498468072194](assets/1552878622385.png) 

同样，通过附加属性可以更友好的控制视频的播放

autoplay 自动播放要结合[muted](https://www.w3school.com.cn/tags/att_video_muted.asp) （设置静音播放）使用才有效

controls 是否显示默认播放控件

loop 循环播放

width 设置播放窗口宽度

height 设置播放窗口的高度

由于版权等原因，不同的浏览器可支持播放的格式是不一样的，如下图供参考

![1498468086199](assets/1552878637922.png) 

**多浏览器支持的方案，如下图**![1498468097509](assets/1552878652774.png)

#### 2.5.2、多媒体 audio

HTML5通过<audio>标签来解决音频播放的问题。

使用相当简单，如下图所示

![1498468026526](assets/1552878544708.png) 

并且可以通过附加属性可以更友好控制音频的播放，如：

autoplay 自动播放

controls 是否显不默认播放控件

loop 循环播放    如果这个属性不写 默认播放一次        loop  或者  loop = “loop”    表示无限循环

由于版权等原因，不同的浏览器可支持播放的格式是不一样的，如下图供参考

![1498468041058](assets/1552878565461.png) 

多浏览器支持的方案，如下图

<source> 标签允许您规定可替换的视频/音频文件供浏览器根据它对媒体类型或者编解码器的支持进行选择

![1498468052965](assets/1552878602754.png) 



















