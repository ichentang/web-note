# css 基础

## 1. 引入CSS样式表（书写位置）


### 1.1 行内式（内联样式）

```html
<标签名 style="属性1:属性值1; 属性2:属性值2; 属性3:属性值3;">内容</标签名>
```


实际上任何HTML标签都拥有style属性，用来设置行内式。

案例：

```css
<div style="color: red; font-size: 12px;">青春不常在，抓紧谈恋爱</div>
```



### 1.2 内部样式表（内嵌样式表）

概念：

> 称内嵌式，是将CSS代码集中写在HTML文档的head头部标签中，并且用style标签定义 

其基本语法格式如下： 

```html
<head>
<style type="text/CSS">
    选择器（选择的标签） { 
      属性1: 属性值1;
      属性2: 属性值2; 
      属性3: 属性值3;
    }
</style>
</head>
```


```css
<style>
	 div {
	 	color: red;
	 	font-size: 12px;
	 }
</style>
```


### 1.3 外部样式表（外链式）

概念：

> 称链入式：
> 是将所有的样式放在一个或多个以**.CSS**为扩展名的外部样式表文件中，
> 通过link标签将外部样式表文件链接到HTML文档中 

其基本语法格式如下： 

```html
<head>
  <link rel="stylesheet" type="text/css" href="css文件路径">
</head>
```

> rel：定义当前文档与被链接文档之间的关系，在这里需要指定为“stylesheet”，表示被链接的文档是一个样式表文件。
>
> type：定义所链接文档的类型，在这里需要指定为“text/CSS”，表示链接的外部文件为CSS样式表。我们都可以省略
>
> href：定义所链接外部样式表文件的URL，可以是相对路径，也可以是绝对路径。

![](https://img-blog.csdnimg.cn/0848d764c7aa49ecad6d9c9e17ca8b2e.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#id=nW8YX&originHeight=357&originWidth=810&originalType=binary&ratio=1&status=done&style=none)


## 2.CSS选择器


### 2.1 标签选择器

概念：

> 标签选择器（元素选择器）是指用**HTML标签名**称作为选择器，按标签名称分类，为页面中某一类标签指定统一的CSS样式。 

```css
<style>
    div {
    	color: red;
    }
    span {
    	color: green;
    }
</style>
```


### 2.2 类选择器


类选择器使用“.”（英文点号）进行标识，后面紧跟类名.

```css
<style>
	.red {
		color: red;
	}
</style>
<body>
	<div class="red">嘿嘿，工作类最多。</div>
</body>
```


### 2.3 类选择器特殊用法- 多类名


我们可以给标签指定多个类名，从而达到更多的选择目的。

```html
<div class="pink fontWeight font20">亚瑟</div>
<div class="font20">刘备</div>
<div class="font14 pink">安其拉</div>
<div class="font14">貂蝉</div>
```


### 2.4 id选择器


id选择器使用`#`进行标识，后面紧跟id名

```html
<style>
	#pink {
		color: pink;
	}
</style>
<body>
	<p id="pink">依旧笑魇如花。</p>
</body>
```

W3C标准规定，在同一个页面内，不允许有相同名字的id对象出现，但是允许相同名字的class。

**_id选择器和类选择器最大的不同在于 使用次数上。_**

> 类选择器我们在修改样式中，用的最多。
>
> id选择器一般用于页面唯一性的元素身上，经常和我们后面学习的javascript 搭配使用。

### 2.6 通配符选择器

概念

> 通配符选择器用`*`号表示，  *   就是 选择所有的标签      他是所有选择器中作用范围最广的，能匹配页面中所有的元素。 


例如下面的代码，使用通配符选择器定义CSS样式，清除所有HTML标记的默认边距。


```css
* {
    /* 定义外边距*/  
    margin: 0;                   
    /* 定义内边距*/
    padding: 0;
}
```


## 3. CSS字体样式属性


### 3.1 font-size:大小

```css
p {  
    font-size:20px; 
}
```

单位： 

> 可以使用相对长度单位，也可以使用绝对长度单位。
>
> 相对长度单位比较常用，推荐使用像素单位px，绝对长度单位使用较少。



![](https://img-blog.csdnimg.cn/6fa59b829f2f47758c22175f410472e2.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#id=SeuGj&originHeight=313&originWidth=638&originalType=binary&ratio=1&status=done&style=none)​


**注意：**


- 我们文字大小以后，基本就用px了，其他单位很少使用
- 谷歌浏览器默认的文字大小为16px
- 但是不同浏览器可能默认显示的字号大小不一致，我们尽量给一个明确值大小，不要默认大小。一般给body指定整个页面文字的大小

### 3.2 font-family:字体

作用：

> font-family属性用于设置哪一种字体。 

```css
p { 
	font-family:"微软雅黑";
}
```

> 网页中常用的字体有宋体、微软雅黑、黑体等，例如将网页中所有段落文本的字体设置为微软雅黑
>
> 可以同时指定多个字体，中间以逗号隔开，表示如果浏览器不支持第一个字体，则会尝试下一个，直到找到合适的字体， 如果都没有，则以我们电脑默认的字体为准。



```
p { 
	font-family: Arial,
	"Microsoft Yahei", 
	"微软雅黑";
}
```

常用技巧：

1. 各种字体之间必须使用英文状态下的逗号隔开。
2. 中文字体需要加英文状态下的引号，英文字体一般不需要加引号。当需要设置英文字体时，英文字体名必须位于中文字体名之前。
3. 如果字体名中包含空格、#、$等符号，则该字体必须加英文状态下的单引号或双引号，例如font-family: "Times New Roman";。
4. 尽量使用系统默认字体，保证在任何用户的浏览器中都能正确显示。

**CSS Unicode字体**


![](https://img-blog.csdnimg.cn/9ac108c510fa4c118039aad44b515d5d.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_19,color_FFFFFF,t_70,g_se,x_16#id=sqv1i&originHeight=360&originWidth=613&originalType=binary&ratio=1&status=done&style=none)​

为什么使用 Unicode字体 

> 在 CSS 中设置字体名称，直接写中文是可以的。但是在文件编码（GB2312、UTF-8 等）不匹配时会产生乱码的错误。
>
> xp 系统不支持 类似微软雅黑的中文。

解决： 

方案一： 你可以使用英文来替代。 比如`font-family:"Microsoft Yahei"`。 

方案二： 在 CSS 直接使用 Unicode 编码来写字体名称可以避免这些错误。使用 Unicode 写中文字体名称，浏览器是可以正确的解析的。  

```css
font-family: "\5FAE\8F6F\96C5\9ED1";   表示设置字体为“微软雅黑”。
```

宋体  SimSun  \5B8B\4F53

新宋体  NSimSun  \65B0\5B8B\4F53

黑体  SimHei  \9ED1\4F53

微软雅黑  Microsoft YaHei  \5FAE\8F6F\96C5\9ED1

楷体_GB2312  KaiTi_GB2312  \6977\4F53_GB2312

隶书  LiSu  \96B6\4E66

幼园  YouYuan  \5E7C\5706

华文细黑  STXihei  \534E\6587\7EC6\9ED1

为了照顾不同电脑的字体安装问题，我们尽量只使用宋体和微软雅黑中文字体


### 3.3 font-weight:字体粗细

> normal  默认值（不加粗的）
>
> bold  定义粗体（加粗的）
>
> 100~900  400 等同于 normal，而 700 等同于 bold  我们重点记住这句话

提倡：我们平时更喜欢用数字来表示加粗和不加粗。


### 3.4 font-style:字体风格

font-style属性用于定义字体风格，如设置斜体、倾斜或正常字体，其可用属性值如下：

> normal  默认值，浏览器会显示标准的字体样式  font-style: normal;
>
> italic  浏览器会显示斜体的字体样式。


### 3.5 font:综合设置字体样式 

基本语法格式如下：

```css
选择器 { font: font-style  font-weight  font-size/line-height  font-family;}
```

注意： 

> 使用font属性时，必须按上面语法格式中的顺序书写，不能更换顺序，各个属性以**空格**隔开。
>
> 其中不需要设置的属性可以省略（取默认值），但必须保留font-size和font-family属性，否则font属性将不起作用。

## 4. CSS外观属性


### 4.1 color:文本颜色

作用：

> color属性用于定义文本的颜色， 

其取值方式有如下3种： 

> 预定义的颜色值  red，green，blue，还有我们的御用色 pink
>
> 十六进制  #FF0000，#FF6600，#29D794
>
> RGB代码          rgb(255,0,0)或rgb(100%,0%,0%)

### 4.2 text-align:文本水平对齐方式

作用：

> text-align属性用于设置文本内容的水平对齐，相当于html中的align对齐属性 

其可用属性值如下： 

> left  左对齐（默认值）
>
> right  右对齐
>
> center  居中对齐

### 4.3 line-height:行间距

作用：

> line-height属性用于设置行间距，就是行与行之间的距离，即字符的垂直间距，一般称为行高。 

单位： 

> line-height常用的属性值单位有三种，分别为像素px，相对值em和百分比%，实际工作中使用最多的是像素px


### 4.4 text-indent:首行缩进

作用：

> text-indent属性用于设置首行文本的缩进， 

属性值 

> 其属性值可为不同单位的数值、em字符宽度的倍数、或相对于浏览器窗口宽度的百分比%，允许使用负值,建议使用em作为设置单位。

**1em 就是一个字的宽度   如果是汉字的段落， 1em 就是一个汉字的宽度**


```css
p {      
    /*行间距*/      
    line-height: 25px;      
    /*首行缩进2个字  em  1个em 就是1个字的大小*/      
    text-indent: 2em;   
}
```


### 4.5 text-decoration 文本的装饰

text-decoration   通常我们用于给链接修改装饰效果

> none  默认。定义标准的文本。 取消下划线（最常用）
>
> underline  定义文本下的一条线。下划线 也是我们链接自带的（常用）
>
> overline  定义文本上的一条线。（不用）
>
> line-through  定义穿过文本下的一条线。（不常用）

## 5. CSS复合选择器

### 5.1 后代选择器（重点）

概念：

> 后代选择器又称为包含选择器 

作用：

> 用来选择元素或元素组的**子孙后代** 
>
> 其写法就是把外层标签写在前面，内层标签写在后面，中间用**空格**分隔，先写父亲爷爷，在写儿子孙子。 

```
父级 子级 {
	属性:属性值;
	属性:属性值;
}
```

案例：

```css
.class h3{
	color:red;
	font-size:16px;
}
```

### 5.2 子元素选择器

作用：

> 子元素选择器只能选择作为某元素**子元素(亲儿子)**的元素。 
>
> 其写法就是把父级标签写在前面，子级标签写在后面，中间跟一个 `>` 进行连接 

语法： 

```css
.class>h3 {
	color:red;
	font-size:14px;
}
```


> 这里的子 指的是 亲儿子  不包含孙子 重孙子之类。

白话：


```css
比如：.demo > h3 {
    color: red;
}   说明  h3 一定是demo 亲儿子。demo 元素包含着h3。
```


### 5.3 交集选择器

条件:

> 交集选择器由两个选择器构成，找到的标签必须满足：既有标签一的特点，也有标签二的特点。 



![](https://img-blog.csdnimg.cn/64484c1a7fe14d679178317038d99efc.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#id=q5wbL&originHeight=346&originWidth=780&originalType=binary&ratio=1&status=done&style=none)​

其中第一个为标签选择器，第二个为class选择器，两个选择器之间**不能有空格**，如h3.special。

**记忆技巧：**


交集选择器 是 并且的意思。  即...又...的意思

> 比如：p.one   选择的是： 类名为 .one  的 段落标签。


### 5.4 并集选择器（重点）

任何形式的选择器（包括标签选择器、class类选择器id选择器等），都可以作为并集选择器的一部分。 

记忆技巧：
并集选择器通常用于集体声明  ，逗号隔开的，所有选择器都会执行后面样式，逗号可以理解为 和的意思。 



```css
比如  
.one, p , #test {
    color: #F00;
}  
表示   .one 和 p  和 #test 这三个选择器都会执行颜色为红色。 
通常用于集体声明。
```


### 5.5  链接伪类选择器


作用：

> 用于向某些选择器添加特殊的效果。比如给链接添加特殊效果， 比如可以选择 第1个，第n个元素。
>
> 因为伪类选择器很多，比如链接伪类，结构伪类等等。我们这里先给大家讲解链接伪类选择器。

```css
a:link      /_ 未访问的链接 _/ 
a:visited   /_ 已访问的链接 _/ 
a:hover     /_ 鼠标移动到链接上 _/ 
a:active    /_ 选定的链接 _/
```

**注意** 

因为叫链接伪类，所以都是 利用交集选择器  a:link    a:hover

因为a链接浏览器具有默认样式，所以我们实际工作中都需要给链接单独指定样式。

实际工作开发中，我们很少写全四个状态，一般我们写法如下：

```css
a {   
    /* a是标签选择器  所有的链接 */
	font-weight: 700;
	font-size: 16px;
	color: gray;
}
a:hover {   
    /* :hover 是链接伪类选择器 鼠标经过 */
	color: red; 
    /*  鼠标经过的时候，由原来的 灰色 变成了红色 */
}
```

## 6. 标签显示模式（display）

### 6.1 块级元素(block-level)

例：

```html
常见的块元素有
<h1>~<h6>、<p>、<div>、<ul>、<ol>、<li>等，
其中<div>标签是最典型的块元素。
```

块级元素的特点

（1）自己独占一行

（2）高度，宽度、外边距以及内边距都可以控制。

（3）宽度默认是容器（父级宽度）的100%

（4）是一个容器及盒子，里面可以放行内或者块级元素。

注意： 

> 只有 文字才 能组成段落  因此 p  里面不能放块级元素，特别是 p 不能放div
>
> 同理还有这些标签h1,h2,h3,h4,h5,h6,dt，他们都是文字类块级标签，里面不能放其他块级元素。



### 6.2 行内元素(inline-level)

例：

```html
常见的行内元素有
<a>、<strong>、<b>、<em>、<i>、<s>、<ins>、<u>、<span>等，
其中<span>标签最典型的行内元素。有的地方也成内联元素
```

行内元素的特点：

（1）相邻行内元素在一行上，一行可以显示多个。

（2）高、宽直接设置是无效的。

（3）默认宽度就是它本身内容的宽度。

（4）**行内元素只能容纳文本或则其他行内元素。**


注意：

> 链接里面不能再放链接。
>
> 特殊情况a里面可以放块级元素，但是给a转换一下块级模式最安全。

### 6.3 行内块元素（inline-block）

例：

```css
在行内元素中有几个特殊的标签
<img />、<input />、<td>，
可以对它们设置宽高和对齐属性，有些资料可能会称它们为行内块元素。
```

行内块元素的特点：

（1）和相邻行内元素（行内块）在一行上,但是之间会有空白缝隙。一行可以显示多个

（2）默认宽度就是它本身内容的宽度。

（3）高度，行高、外边距以及内边距都可以控制。 

### 6.4 标签显示模式转换 display

块转行内：display:inline;

行内转块：display:block;

块、行内元素转换为行内块： display: inline-block;

此阶段，我们只需关心这三个，其他的是我们后面的工作。


## 7. CSS 背景(background)

### 7.1 背景颜色(color)

语法：  

```css
background-color: 颜色值;   
默认的值是 transparent  透明的
```


### 7.2 背景图片(image)

语法：

```css
background-image : none | url (url)
```

> none  无背景图（默认的）
>
> url  使用绝对或相对地址指定背景图像

```css
background-image : url(images/demo.png);
```

小技巧：  我们提倡 背景图片后面的地址，url不要加引号。

### 7.3 背景平铺（repeat）

语法：

```css
background-repeat : repeat | no-repeat | repeat-x | repeat-y
```

repeat        背景图像在纵向和横向上平铺（默认的）

no-repeat  背景图像不平铺

repeat-x     背景图像在横向上平铺

repeat-y     背景图像在纵向平铺

### 7.4 背景位置(position) 重点

语法：

```css
background-position : length || length

background-position : position || position
```

length  百分数

position  top

注意： 

> 必须先指定background-image属性
>
> position 后面是x坐标和y坐标。 可以使用方位名词或者 精确单位。
>
> 如果指定两个值，两个值都是方位名字，则两个值前后顺序无关，比如left  top和top  left效果一致
>
> 如果只指定了一个方位名词，另一个值默认居中对齐。
>
> 如果position 后面是精确坐标， 那么第一个，肯定是 x  第二的一定是y
>
> 如果只指定一个数值,那该数值一定是x坐标，另一个默认垂直居中
>
> 如果指定的两个值是 精确单位和方位名字混合使用，则第一个值是x坐标，第二个值是y坐标

**实际工作用的最多的，就是背景图片居中对齐了。**


### 7.5 背景附着

背景附着就是解释背景是滚动的还是固定的 

语法：  

```css
background-attachment : scroll | fixed
```

> scroll  背景图像是随对象内容滚动
>
> fixed  背景图像固定

### 7.6 背景简写

> background：属性的值的书写顺序官方并没有强制标准的。为了可读性，建议大家如下写：
>
> background: 背景颜色 背景图片地址 背景平铺 背景滚动 背景位置;

语法：

```css
background: transparent url(image.jpg) repeat-y  scroll center top ;
```


### 7.7 背景透明(CSS3)

语法：

```css
background: rgba(0, 0, 0, 0.3);
```

> 最后一个参数是alpha 透明度  取值范围 0~1之间
>
> 我们习惯把0.3 的 0 省略掉  这样写  background: rgba(0, 0, 0, .3);
>
> 注意：  背景半透明是指盒子背景半透明， 盒子里面的内容不受影响
>
> 因为是CSS3 ，所以 低于 ie9 的版本是不支持的。

## 8. CSS 三大特性

### 8.1 CSS层叠性


![](https://img-blog.csdnimg.cn/99936f49eff748938dffcaa47f407995.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#id=BqkjX&originHeight=401&originWidth=1010&originalType=binary&ratio=1&status=done&style=none)​

概念：

> 所谓层叠性是指多种CSS样式的叠加。
> 是浏览器处理冲突的一个能力,如果一个属性通过两个相同选择器设置到同一个元素上，那么这个时候一个属性就会将另一个属性层叠掉 

原则： 

> 样式冲突，遵循的原则是**就近原则。** 那个样式离着结构近，就执行那个样式。
>
> 样式不冲突，不会层叠

### 8.2 CSS继承性


![](https://img-blog.csdnimg.cn/df610f1bd50047689d2cf9a001a7c5e9.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#id=L4iTP&originHeight=404&originWidth=995&originalType=binary&ratio=1&status=done&style=none)​

概念：

> 子标签会继承父标签的某些样式，如文本颜色和字号。
> 想要设置一个可继承的属性，只需将它应用于父元素即可。 

**注意**： 

> 恰当地使用继承可以简化代码，降低CSS样式的复杂性。比如有很多子级孩子都需要某个样式，可以给父级指定一个，这些孩子继承过来就好了。
>
> 子元素可以继承父元素的样式（**text-，font-，line-这些元素开头的可以继承，以及color属性**）


### 8.3 CSS优先级（重点）


![](https://img-blog.csdnimg.cn/2a122334e6f34a7683fac6b3e87b1c24.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#id=G2aAf&originHeight=373&originWidth=994&originalType=binary&ratio=1&status=done&style=none)​

概念：

定义CSS样式时，经常出现两个或更多规则应用在同一元素上，此时， 选择器相同，则执行层叠性。选择器不同，就会出现优先级的问题。

#### 1). 权重计算公式

关于CSS权重，我们需要一套计算公式来去计算

> 标签选择器                                                                           计算权重公式
>
> 继承或者 * ，后代选择器                                                           0,0,0,0
>
> 标签选择器，伪元素选择器(li::after)                                         0,0,0,1
>
> 每个类，伪类，属性选择器(a[ref="eee"])                                0,0,1,0
>
> 每个ID                                                                                          0,1,0,0
>
> 每个行内样式style=""                                                                 1,0,0,0
>
> 每个!important  重要的                                                            ∞ 无穷大

#### 2). 权重叠加


我们经常用交集选择器，后代选择器等，是有多个基础选择器组合而成，那么此时，就会出现权重叠加。


就是一个简单的加法计算

> div ul  li   ------>      0,0,0,3
>
> .nav ul li   ------>      0,0,1,2
>
> a:hover      -----—>   0,0,1,1
>
> .nav a       ------>      0,0,1,1

注意：

数位之间没有进制 比如说： 0,0,0,5 + 0,0,0,5 =0,0,0,10 而不是 0,0, 1, 0， 所以不会存在10个div能赶上一个类选择器的情况。


## 9. 盒子模型

CSS3 中的盒模型有以下两种：标准盒子模型、IE 盒子模型


![在这里插入图片描述](https://img-blog.csdnimg.cn/4c4e27efb3664191806e84c142625655.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5qC86Zu354uQ5oCd,size_20,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/6e1d8162ecee48f4830e8b40ce867eb9.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5qC86Zu354uQ5oCd,size_20,color_FFFFFF,t_70,g_se,x_16)


盒模型都是由四个部分组成的，分别是 margin、border、padding 和 content。

标准盒模型和 IE 盒模型的区别在于设置 width 和 height 时，所对应的范围不同：

- 标准盒模型的 width 和 height 属性的范围只包含了 content，
- IE 盒模型的 width 和 height 属性的范围包含了 border、padding 和 content。

可以通过修改元素的 box-sizing 属性来改变元素的盒模型：

- `box-sizing: content-box`表示标准盒模型（默认值）
- `box-sizing: border-box`表示 IE 盒模型（怪异盒模型）


## 10. 内边距（padding）

padding属性用于设置内边距。**是指 边框与内容之间的距离。**


### 10.1 设置

| 属性           | 作用     |
| -------------- | -------- |
| padding-left   | 左内边距 |
| padding-right  | 右内边距 |
| padding-top    | 上内边距 |
| padding-bottom | 下内边距 |

当我们给盒子指定padding值之后， 发生了2件事情：

> 内容和边框 有了距离，添加了内边距。

> 盒子会变大了。

**注意：  后面跟几个数值表示的意思是不一样的。**

我们分开写有点麻烦，我们可以不可以简写呢？

> 值的个数                                    表达意思
>
> 1个值                           padding：上下左右内边距;
>
> 2个值                           padding: 上下内边距    左右内边距 ；
>
> 3个值                           padding：上内边距   左右内边距   下内边距；
>
> 4个值                           padding: 上内边距 右内边距 下内边距 左内边距 ；

### 10.2 内盒尺寸计算（元素实际大小）


![](https://img-blog.csdnimg.cn/d7388300952c48d780d8dc3aab559f81.png#id=srWcq&originHeight=251&originWidth=296&originalType=binary&ratio=1&status=done&style=none)

宽度

> Element Height = content height + padding + border （Height为内容高度） 

高度

> Element Width = content width + padding + border （Width为内容宽度） 

> 盒子的实际的大小 =   内容的宽度和高度 +  内边距   +  边框 

## 11. 外边距（margin）

margin属性用于设置外边距。  margin就是控制**盒子和盒子之间的距离**


### 11.2 设置：

| 属性          | 作用     |
| ------------- | -------- |
| margin-left   | 左外边距 |
| margin-right  | 右外边距 |
| margin-top    | 上外边距 |
| margin-bottom | 下外边距 |

margin值的简写 （复合写法）代表意思  跟 padding 完全相同。


### 11.3 块级盒子水平居中

可以让一个块级盒子实现水平居中必须： 

> 盒子必须指定了宽度（width）

> 然后就给**左右的外边距都设置为auto**，

实际工作中常用这种方式进行网页布局，示例代码如下：


```css
.header{ 
  width:960px;
  
  //表示的意思是上下边距为0，左右为水平对齐
  margin:0 auto;
}
```


常见的写法，以下下三种都可以。

> margin-left: auto;   margin-right: auto;

> margin: auto;

> margin: 0 auto;

### 11.4 文字居中和盒子居中区别

盒子内的文字水平居中是  text-align: center,  而且还可以让 行内元素和行内块居中对齐

块级盒子水平居中  左右margin 改为 auto

```css
text-align: center; /*  文字 行内元素 行内块元素水平居中 */
margin: 10px auto;  /* 块级盒子水平居中  左右margin 改为 auto 就阔以了 上下margin都可以 */
```


### 11.5 插入图片和背景图片区别

插入图片 我们用的最多 比如产品展示类  移动位置只能靠盒模型 padding margin

背景图片我们一般用于小图标背景 或者 超大背景图片  背景图片 只能通过  background-position

```css
 img {  
		width: 200px;/* 插入图片更改大小 width 和 height */
		height: 210px;
		margin-top: 30px;  /* 插入图片更改位置 可以用margin 或padding  盒模型 */
		margin-left: 50px; /* 插入当图片也是一个盒子 */
	}

 div {
		width: 400px;
		height: 400px;
		border: 1px solid purple;
		background: #fff url(images/sun.jpg) no-repeat;
		background-position: 30px 50px; /* 背景图片更改位置 我用 background-position */
	}
```


### 11.6 清除元素的默认内外边距(重要)


为了更灵活方便地控制网页中的元素，制作网页时，我们需要将元素的默认内外边距清除


代码：


```css
* {
   padding:0;         /* 清除内边距 */
   margin:0;          /* 清除外边距 */
}
```


注意：

> 行内元素为了照顾兼容性， 尽量只设置左右内外边距， 不要设置上下内外边距。

### 11.7 外边距合并


使用margin定义块元素的**垂直外边距**时，可能会出现外边距的合并。


#### (1). 相邻块元素垂直外边距的合并

> 当上下相邻的两个块元素相遇时，如果上面的元素有下外边距margin-bottom

> 下面的元素有上外边距margin-top，则他们之间的垂直间距不是margin-bottom与margin-top之和

> **取两个值中的较大者**这种现象被称为相邻块元素垂直外边距的合并（也称外边距塌陷）。

**解决方案：尽量给只给一个盒子添加margin值**。

> 具体案例：

```html
<style>
    .first {
        width: 100px;
        height: 100px;
        background-color: aquamarine;
        margin-bottom: 50px;
    }
    .second {
        width: 100px;
        height: 100px;
        background-color: #333;
        margin-top: 50px;
    }
</style>
<body>
    <div class="first"></div>
    <div class="second"></div>
</body>
```




#### (2). 嵌套块元素垂直外边距的合并（塌陷）

```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        hr {
            border-top: 1px solid red;
        }
        .father {
            width: 300px;
            height: 300px;
            background-color: aquamarine;
        }
        .child {
            width: 100px;
            height: 100px;
            background-color: plum;
            /* 这时候加margin-top 子元素并没有下来,父元素下来了 */
            margin-top: 100px;
        }
    </style>
</head>
<body>
    <hr>
    <div class="father">
        <div class="child"></div>
    </div>
</body>
</html>
```



**解决方案：**


1. 可以为父元素定义上边框。
2. 可以为父元素定义上内边距
3. 可以为父元素添加overflow:hidden（让父元素内形成一个BFC）。



还有其他方法，比如浮动、固定、绝对定位的盒子不会有问题，后面咱们再总结。。。

**盒子模型布局稳定性**

学习完盒子模型，内边距和外边距，什么情况下用内边距，什么情况下用外边距？ 

我们根据稳定性来分，建议如下：


按照 优先使用  宽度 （width）  其次 使用内边距（padding）    再次  外边距（margin）。


```css
width >  padding  >   margin
```

原因： 

> margin 会有外边距合并 还有 ie6下面margin 加倍的bug（讨厌）所以最后使用。

> padding  会影响盒子大小， 需要进行加减计算（麻烦） 其次使用。

> width   没有问题，我们经常使用宽度剩余法 高度剩余法来做。

## 12. 浮动(float)


### 12.1 CSS 布局的三种机制

网页布局的核心——就是**用 CSS 来摆放盒子**。

CSS 提供了 **3 种机制**来设置盒子的摆放位置，分别是**普通流**（标准流）、**浮动**和**定位**，其中：

**普通流**（标准流） 

> **块级元素**会独占一行，**从上向下**顺序排列； 

```css
div,p
```

> **行内元素**会按照顺序，**从左到右**顺序排列，碰到父元素边缘则自动换行； 

```css
常用元素：span、a、i、em等
```

**浮动** 

> 让盒子从普通流中**浮**起来,主要作用让多个块级盒子一行显示。

**定位** 

> 将盒子**定**在浏览器的某一个**位**置——CSS 离不开定位，特别是后面的 js 特效。

### 12.2 为什么需要浮动？


思考题：


我们首先要思考以下2个布局中最常见的问题？


1.  如何让多个盒子(div)水平排列成一行？
    ![](https://img-blog.csdnimg.cn/c1ce4a466b8643959c1874e168ee9eb8.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#id=Pa2fW&originHeight=220&originWidth=1174&originalType=binary&ratio=1&status=done&style=none)​
2.  如何实现盒子的左右对齐？ 



![](https://img-blog.csdnimg.cn/caa6d5a04e6f4ce9a019eb94034deb15.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#id=zzb6O&originHeight=575&originWidth=1133&originalType=binary&ratio=1&status=done&style=none)​


虽然我们前面学过行内块（inline-block） 但是他却有自己的缺陷：


1. 它可以实现多个元素一行显示，但是中间会有空白缝隙，不能满足以上第一个问题。
2. 它不能实现以上第二个问题，盒子左右对齐



**总结**


> 因为一些网页布局要求，标准流不能满足我们的需要了，因此我们需要浮动来完成网页布局。



### 12.3  什么是浮动(float)


**概念**：元素的浮动是指**设置了浮动属性的元素**会


1. 脱离标准普通流的控制
2. 移动到指定位置。

#### 作用


1. **让多个盒子(div)水平排列成一行**，使得浮动成为布局的重要手段。
2. 可以实现盒子的左右对齐等等..
3. 浮动最早是用来**控制图片**，实现**文字环绕图片的效果**。


#### 语法


```css
选择器 { 
    float: 属性值; 
}
```

| 属性值    | 描述                     |
| --------- | ------------------------ |
| **none**  | 元素不浮动（**默认值**） |
| **left**  | 元素向**左**浮动         |
| **right** | 元素向**右**浮动         |


![](https://img-blog.csdnimg.cn/c48f7943034e46ffaa7a6d612282f518.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_15,color_FFFFFF,t_70,g_se,x_16#id=cZWir&originHeight=237&originWidth=478&originalType=binary&ratio=1&status=done&style=none)


```css
.box1 {
    width: 200px;
    height: 200px;
    background-color: rgba(255, 0, 0, 0.5);
    float: left;
}
.box2 {
    width: 150px;
    height: 300px;
    background-color: skyblue;
}
```


**小结**：

> `float` 属性会让盒子漂浮在标准流的上面，所以第二个标准流的盒子跑到浮动盒子的底下了。





![](https://img-blog.csdnimg.cn/55703f6280634b00b3e754e044976fd6.png#id=qZp00&originHeight=175&originWidth=489&originalType=binary&ratio=1&status=done&style=none)

**注意： 浮动的元素互相贴靠一起的，但是如果父级宽度装不下这些浮动的盒子， 多出的盒子会另起一行对齐**

### 12.4 浮动(float)的应用（重要）


#### 浮动和标准流的父盒子搭配


我们知道，浮动是脱标的，会影响下面的标准流元素，此时，我们需要给浮动的元素添加一个标准流的父亲，这样，最大化的减小了对其他标准流的影响。

#### 浮动应用案例


![](https://img-blog.csdnimg.cn/b89e4b15c6804a01aca536404f4bda9a.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#id=g8Zzw&originHeight=597&originWidth=1209&originalType=binary&ratio=1&status=done&style=none)​

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>小米案例练习</title>
	<style>
		/*清除元素默认内外边距样式*/
		* {
			margin: 0;
			padding: 0;
		}
		/*清除列表样式 前面的小点点*/
		li {
			list-style: none;
		}
		.box {
			width: 1226px;
			height: 615px;
			background-color: pink;
			margin: auto;
		}
		.left {
			float: left;
			width: 234px;
			height: 615px;
			background-color: purple;
		}
		.left img {
			/*width: 234px;*/
			width: 100%;
		}
		.right {
			float: right;
			width: 992px;
			height: 615px;
			background-color: skyblue;
		}
		.right li {
			float: left;
			width: 234px;
			height: 300px;
			background-color: pink;
			margin-left: 14px;
			margin-bottom: 14px;
		}
	</style>
</head>
<body>
	<div class="box">
		<div class="left">
			<img src="images/mi.jpg" alt="">
		</div>
		<ul class="right">
			<li>1</li>
			<li>2</li>
			<li>3</li>
			<li>4</li>
			<li>5</li>
			<li>6</li>
			<li>7</li>
			<li>8</li>
		</ul>
	</div>
</body>
</html>
```

### 12.5  浮动(float)的扩展


#### 1). 浮动元素与父盒子的关系

> 子盒子的浮动参照父盒子对齐

> 不会与父盒子的边框重叠，也不会超过父盒子的内边距



![](https://img-blog.csdnimg.cn/c22dbf74cb0a4414b0b8d9869509c9d6.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#id=E4gLe&originHeight=668&originWidth=1189&originalType=binary&ratio=1&status=done&style=none)​



#### 2). 浮动元素与兄弟盒子的关系


在一个父级盒子中，如果**前一个兄弟盒子**是：

> **浮动**的，那么**当前盒子**会与前一个盒子的顶部对齐；

> **普通流**的，那么**当前盒子**会显示在前一个兄弟盒子的下方。



**记住：**


> 浮动只会影响当前的或者是后面的标准流盒子，不会影响前面的标准流。



![](https://img-blog.csdnimg.cn/3da1521cd90d465ab6bee1760271ec48.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_17,color_FFFFFF,t_70,g_se,x_16#id=lnolf&originHeight=696&originWidth=533&originalType=binary&ratio=1&status=done&style=none)

**建议**

> **如果一个盒子里面有多个子盒子，如果其中一个盒子浮动了，其他兄弟也应该浮动。防止引起问题**


## 13. 清除浮动


### 13.1 为什么要清除浮动


因为父级盒子很多情况下，不方便给高度，但是子盒子浮动就不占有位置，最后父级盒子高度为0，就影响了下面的标准流盒子。


![](https://img-blog.csdnimg.cn/c9af2e7adfea47019d0d2f15282f05cf.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#id=K4ou1&originHeight=457&originWidth=803&originalType=binary&ratio=1&status=done&style=none)​


![](https://img-blog.csdnimg.cn/2af829eb70384474b7b3ffe66047c4b0.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#id=TVJ1t&originHeight=288&originWidth=805&originalType=binary&ratio=1&status=done&style=none)​

总结： 

> 由于浮动元素不再占用原文档流的位置，所以它会对后面的元素排版产生影响

> 准确地说，并不是清除浮动，而是**清除浮动后造成的影响**



### 13.2 清除浮动本质

**清除浮动本质：**

> 清除浮动主要为了解决父级元素因为子级浮动引起内部高度为0 的问题。清除浮动之后， 父级就会根据浮动的子盒子自动检测高度。父级有了高度，就不会影响下面的标准流了


### 13.3 清除浮动的方法

语法：

```css
选择器 {
    clear:属性值;
}   
clear 清除
```

| 属性值 | 描述                                       |
| ------ | ------------------------------------------ |
| left   | 不允许左侧有浮动元素（清除左侧浮动的影响） |
| right  | 不允许右侧有浮动元素（清除右侧浮动的影响） |
| both   | 同时清除左右两侧浮动的影响                 |

但是我们实际工作中， 几乎只用 clear: both;


#### 1).额外标签法(隔墙法)


```html
是W3C推荐的做法是通过在浮动元素末尾添加一个空的标签例如 
<div style=”clear:both”></div>，或则其他标签br等亦可。
```

优点：

> 通俗易懂，书写方便

缺点： 

> 添加许多无意义的标签，结构化较差。



#### 2).父级添加overflow属性方法


```css
可以给父级添加： 
overflow为 hidden| auto| scroll  都可以实现。
```

优点：  

> 代码简洁

缺点：  

> 内容增多时候容易造成不会自动换行导致内容被隐藏掉，无法显示需要溢出的元素。


#### 3).使用after伪元素清除浮动


**:after 方式为空元素额外标签法的升级版，好处是不用单独加标签了**


使用方法：


```css
 .clearfix:after {  
     content: ""; 
     display: block; 
     height: 0; 
     clear: both; 
     visibility: hidden;  
}   
.clearfix {*zoom: 1;}   /* IE6、7 专有 */
```

优点： 

> 符合闭合浮动思想  结构语义化正确

缺点： 

> 由于IE6-7不支持:after，使用 zoom:1触发 hasLayout。

代表网站：

> 百度、淘宝网、网易等



#### 4).使用双伪元素清除浮动


使用方法：


```css
.clearfix:before,.clearfix:after { 
  content:"";
  display:table; 
}
.clearfix:after {
 clear:both;
}
.clearfix {
  *zoom:1;
}
```

优点：  

> 代码更简洁 

缺点：  

> 由于IE6-7不支持:after，使用 zoom:1触发 hasLayout。 

代表网站： 

> 小米、腾讯等 



**清除浮动案例**

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		/*声明清除浮动的样式*/
		.clearfix:after {
			content: "";
			display: block;
			height: 0;
			visibility: hidden;
			clear: both;
		}
		.clearfix {
			*zoom: 1;  /*ie6,7 专门清除浮动的样式*/
		}
		/*很多情况下，我们的父盒子，不方便给高度  根据内容撑开，有多少内容，我的父盒子就有多高*/
		.one {
			width: 500px;
			/*background-color: pink;*/
			border: 1px  solid red;
			
		}
		/*因为damao 二毛 浮动了，不占有位置， 而父级又没有高度， 所以two 就到底下去了*/
		.damao {
			float: left;
			width: 200px;
			height: 200px;
			background-color: purple;
		}
		.ermao {
			float: left;
			width: 250px;
			height: 250px;
			background-color: skyblue;
		}
		.two {
			width: 700px;
			height: 150px;
			background-color: #000;
		}

	</style>
</head>
<body>
	<div class="one clearfix">
		<div class="damao"></div>
		<div class="ermao"></div>
	</div>
	<div class="two"></div>
</body>
</html>
```

# 定位(position)

## 1. CSS 布局的三种机制


> 网页布局的核心 —— 就是**用 CSS 来摆放盒子位置**。

CSS 提供了 **3 种机制**来设置盒子的摆放位置，分别是**普通流**、**浮动**和**定位**，其中：


1. **普通流**（**标准流**） 

2. **浮动** 

   > 让盒子从普通流中**浮**起来 —— **让多个盒子(div)水平排列成一行**。

3. **定位** 

   > 将盒子**定**在某一个**位**置  自由的漂浮在其他盒子的上面  —— CSS 离不开定位，特别是后面的 js 特效。


## 3. 定位详解


定位也是用来布局的，它有两部分组成：


> `定位 = 定位模式 + 边偏移`

### 3.1 边偏移


简单说， 我们定位的盒子，是通过边偏移来移动位置的。

在 CSS 中，通过 `top`、`bottom`、`left` 和 `right` 属性定义元素的**边偏移**：（方位名词）

定位的盒子有了边偏移才有价值。 一般情况下，凡是有定位地方必定有边偏移。


### 3.2  定位模式 (position)


在 CSS 中，通过 `position` 属性定义元素的**定位模式**，语法如下：


```css
选择器 { 
    position: 属性值; 
}
```

定位模式是有不同分类的，在不同情况下，我们用到不同的定位模式。

值                                                   语义

`static`                                     **静态**定位

`relative`                                 **相对**定位

`absolute`                                 **绝对**定位

`fixed`                                        **固定**定位



![](https://img-blog.csdnimg.cn/f85a9387b536436fbe3d901be5e3b65a.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_17,color_FFFFFF,t_70,g_se,x_16#id=rnCrK&originHeight=310&originWidth=535&originalType=binary&ratio=1&status=done&style=none)



#### 3.2.1 相对定位(relative) - 重要

**相对定位**是元素**相对**于它  原来在标准流中的位置 来说的。（自恋型）

相对定位的特点：（务必记住）

> 相对于 自己原来在标准流中位置来移动的

> 原来**在标准流的区域继续占有**，后面的盒子仍然以标准流的方式对待它。



#### 3.2.3 绝对定位(absolute) - 重要

**绝对定位**是元素以带有定位的父级元素来移动位置 


1.  **完全脱标** —— 完全不占位置； 
2.  **父元素没有定位**，则以**浏览器**为准定位（Document 文档）。
    ![](https://img-blog.csdnimg.cn/ff9117de7b974063977b1941bfce9476.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#height=443&id=yVVce&originHeight=613&originWidth=969&originalType=binary&ratio=1&status=done&style=none&width=700)
3.  **父元素要有定位**
    将元素依据最近的已经定位（绝对、固定或相对定位）的父元素（祖先）进行定位。 



![](https://img-blog.csdnimg.cn/7c0f8985e4974ee48b6f53d92663504f.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#id=VEd1t&originHeight=574&originWidth=912&originalType=binary&ratio=1&status=done&style=none)


#### 3.2.4 固定定位(fixed) - 重要

**固定定位**是**绝对定位**的一种特殊形式：


1. **完全脱标** —— 完全不占位置；

2. 只认**浏览器的可视窗口** —— `浏览器可视窗口 + 边偏移属性` 来设置元素的位置； 

   > 跟父元素没有任何关系；单独使用的

   > 不随滚动条滚动。




## 4. 定位(position)的案例


### 4.1 哈根达斯

**案例截图**：


![](https://img-blog.csdnimg.cn/3c4cd45894404c9d89bd75cfe80927c5.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#height=272&id=y4PvI&originHeight=349&originWidth=641&originalType=binary&ratio=1&status=done&style=none&width=500)


#### 哈根达斯分析


1. 一个大的 `div` 中包含 `3` 张图片；
2. 大的 `div` 水平居中；
3. `2` 张小图片**重叠**在**广告**图片上方 —— 脱标，不占位置，需要使用**绝对定位**；
4. `2` 张小图片分别显示在**左上角**和**右下角** —— 需要**使用边偏移确定准确位置**。

代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>哈根达斯</title>
	<style>
		.box {
			position: relative;
			width: 310px;
			height: 190px;
			border: 1px solid #ccc;
			margin: 100px auto;
			padding: 10px;
		}
		.top {
			/*float: left;*/
			position: absolute;
			top: 0;
			left: 0;
		}
		.bottom {
			position: absolute;
			bottom: 0;
			right: 0;
		}
	</style>
</head>
<body>
	<div class="box">
		<img src="images/top_tu.gif" alt="" class="top">
		<img src="images/adv.jpg" alt="">
		<img src="images/br.gif" alt="" class="bottom">	
	</div>
</body>
</html>
```

**案例小结**：


1. **子绝父相** —— **子元素**使用**绝对定位**，**父元素**使用**相对定位**；

2. **与浮动的对比**： 

   > **绝对定位**：脱标，**利用边偏移指定准确位置**；

   > **浮动**：脱标，不能指定准确位置，**让多个块级元素在一行显示**。

## 5. 定位(position)的扩展


### 5.1 绝对定位的盒子居中


> **注意**：**绝对定位/固定定位的盒子**不能通过设置 `margin: auto` 设置**水平居中**。



在使用**绝对定位**时要想实现水平居中，可以按照下图的方法：


![](https://img-blog.csdnimg.cn/99b91d8f1a5c4e08b6d045cb64ec5499.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#id=QY06e&originHeight=260&originWidth=732&originalType=binary&ratio=1&status=done&style=none)


1. `left: 50%;`：让**盒子的左侧**移动到**父级元素的水平中心位置**；
2. `margin-left: -100px;`：让盒子**向左**移动**自身宽度的一半**。



> 案例演示：相对定位案例。



#### 盒子居中定位示意图


![](https://img-blog.csdnimg.cn/6d68230d19c042c2ad957d73020bc5bf.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#id=I62J2&originHeight=370&originWidth=731&originalType=binary&ratio=1&status=done&style=none)



```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>绝对定位的盒子水平居中对齐</title>
	<style>
		div {
			/*绝对定位 margin 左右auto 不能让盒子水平居中*/
			position: absolute;
			/*1.left 50% 走父亲宽度的一半*/	
			left: 50%;
			/*2.margin-left 左走自己宽度的一半  一定注意是 负值*/
			margin-left: -100px;
			width: 200px;
			height: 200px;
			background-color: pink;
			/*标准流 margin 左右auto 就可以让盒子水平居中*/
			/*margin: auto;*/
		}
	</style>
</head>
<body>
	<div></div>
</body>
</html>
```



### 5.2 堆叠顺序（z-index）


在使用**定位**布局时，可能会**出现盒子重叠的情况**。


加了定位的盒子，默认**后来者居上**， 后面的盒子会压住前面的盒子。


应用 `z-index` 层叠等级属性可以**调整盒子的堆叠顺序**。如下图所示：


![](https://img-blog.csdnimg.cn/56d39c54d9a742c4986d15787deb13b8.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#id=zdmH4&originHeight=226&originWidth=735&originalType=binary&ratio=1&status=done&style=none)

`z-index` 的特性如下：


1. **属性值**：**正整数**、**负整数**或 **0**，默认值是 0，数值越大，盒子越靠上；
2. 如果**属性值相同**，则按照书写顺序，**后来居上**；
3. **数字后面不能加单位**。



**注意**：`z-index` 只能应用于**相对定位**、**绝对定位**和**固定定位**的元素，其他**标准流**、**浮动**和**静态定位**无效。

### 5.3 定位改变display属性


前面我们讲过， display 是 显示模式， 可以改变显示模式有以下方式:

> 可以用inline-block  转换为行内块

> 可以用浮动 float 默认转换为行内块（类似，并不完全一样，因为浮动是脱标的）

> 绝对定位和固定定位也和浮动类似， 默认转换的特性 转换为行内块。



所以说， 一个行内的盒子，如果加了**浮动**、**固定定位**和**绝对定位**，不用转换，就可以给这个盒子直接设置宽度和高度等。

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		div {
			/*块级元素 不给width 默认通栏显示*/
			/*1. 利用 display inline-block*/
			/*display: inline-block;*/
			/*行内块不给width 默认的宽度就是内容的宽度*/
			/*2. 浮动 也能转换*/
			/*float: left;*/
			/*3. 绝对定位（固定定位） 也能转换*/
			position: absolute;
			height: 100px;
			background-color: pink;
		}
		span {
			position: absolute;
			top: 200px;
			left: 200px;
			width: 300px;
			height: 300px;
			background-color: purple;
		}
	</style>
</head>
<body>
	<div>天王盖地虎， 导师一米五</div>
	<span></span>
</body>
</html>
```



**同时注意：**


浮动元素、绝对定位(固定定位）元素的都不会触发外边距合并的问题。 （我们以前是用padding border overflow解决的）


也就是说，我们给盒子改为了浮动或者定位，就不会有垂直外边距合并的问题了。

## 6. 定位小结

| 定位模式         | 是否脱标占有位置     | 移动位置基准           | 模式转换（行内块） | 使用情况                 |
| ---------------- | -------------------- | ---------------------- | ------------------ | ------------------------ |
| 静态static       | 不脱标，正常模式     | 正常模式               | 不能               | 几乎不用                 |
| 相对定位relative | 不脱标，占有位置     | 相对自身位置移动       | 不能               | 基本单独使用             |
| 绝对定位absolute | 完全脱标，不占有位置 | 相对于定位父级移动位置 | 能                 | 要和定位父级元素搭配使用 |
| 固定定位fixed    | 完全脱标，不占有位置 | 相对于浏览器移动位置   | 能                 | 单独使用，不需要父级     |



**注意**：


1. **边偏移**需要和**定位模式**联合使用，**单独使用无效**；
2. `top` 和 `bottom` 不要同时使用；
3. `left` 和 `right` 不要同时使用。



## 案例

### 仿京东三角效果

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		div {
			position: relative;
			width: 200px;
			height: 100px;
			background-color: pink;
			margin: 100px auto;
		}
		p {
			position: absolute;
			top: -40px;
			left: 50%;
			margin-left: -20px;
			width: 0;
			height: 0;
			border-style: solid;
			border-width: 20px;
			border-color: transparent transparent pink transparent;
			font-size: 0;
			line-height: 0;
		}
	</style>
</head>
<body>
	<div>
		<p></p>
	</div>
</body>
</html>
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/f30368a2e6b04094a14da0a1464b3cc2.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5qC86Zu354uQ5oCd,size_20,color_FFFFFF,t_70,g_se,x_16)


# 常用技巧

## 1. 元素的显示与隐藏

目的

> 让一个元素在页面中消失或者显示出来

场景

> 类似网站广告，当我们点击关闭就不见了，但是我们重新刷新页面，会重新出现！


### 1.1 display 显示（重点）

display 设置或检索对象是否及如何显示。

```css
display: none 隐藏对象

display：block 除了转换为块级元素之外，同时还有显示元素的意思。
```

特点： 隐藏之后，不再保留位置。


![](https://img-blog.csdnimg.cn/3fe65f2d45a84583b905fe1ab62007ae.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

实际开发场景：

> 配合后面js做特效，比如下拉菜单，原先没有，鼠标经过，显示下拉菜单， 应用极为广泛


### 1.2 visibility 可见性 (了解)

设置或检索是否显示对象。

```css
visibility：visible ; 　对象可视

visibility：hidden; 　  对象隐藏
```

特点： 隐藏之后，继续保留原有位置。


![](https://img-blog.csdnimg.cn/0edc3126cffd41de9681e91692f38ddf.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

### 1.3 overflow 溢出(重点)

检索或设置当对象的内容超过其指定高度及宽度时如何管理内容。

> 属性值                                                                               描述
>
> **visible**                                                            不剪切内容也不添加滚动条
>
> **hidden**                                            不显示超过对象尺寸的内容，超出的部分隐藏掉
>
> **scroll**                                                         不管超出内容否，总是显示滚动条
>
> **auto**                                                       超出自动显示滚动条，不超出不显示滚动条


![](https://img-blog.csdnimg.cn/9bafc3aa184e4ed5873cc075fb3d4822.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

实际开发场景：

1. 清除浮动
2. 隐藏超出内容，隐藏掉,  不允许内容超过父盒子。


## 2. CSS用户界面样式

所谓的界面样式， 就是更改一些用户操作样式，以便提高更好的用户体验

### 2.1 鼠标样式cursor

设置或检索在对象上移动的鼠标指针采用何种系统预定义的光标形状。

| 属性值          | 描述       |
| --------------- | ---------- |
| **default**     | 小白  默认 |
| **pointer**     | 小手       |
| **move**        | 移动       |
| **text**        | 文本       |
| **not-allowed** | 禁止       |


鼠标放我身上查看效果哦：

```html
<ul>
  <li style="cursor:default">我是小白</li>
  <li style="cursor:pointer">我是小手</li>
  <li style="cursor:move">我是移动</li>
  <li style="cursor:text">我是文本</li>
  <li style="cursor:not-allowed">我是文本</li>
</ul>
```

### 2.2 轮廓线 outline

![](https://img-blog.csdnimg.cn/8fbcefd5b7dc4d75ba87e3d98bfd7be4.png#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

是绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用。

```css
outline : outline-color ||outline-style || outline-width
```

但是我们都不关心可以设置多少，我们平时都是去掉的。 

最直接的写法是 ：  outline: 0;   或者  outline: none;

```html
<input  type="text"  style="outline: 0;"/>
```

### 2.3 防止拖拽文本域resize

![](https://img-blog.csdnimg.cn/6fe85cd8fedc47aa86c03925b4aef613.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_14,color_FFFFFF,t_70,g_se,x_16#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

实际开发中，我们文本域右下角是不可以拖拽：

```html
<textarea  style="resize: none;"></textarea>
```


## 3. vertical-align 垂直对齐

有宽度的块级元素居中对齐，是margin: 0 auto;

让文字居中对齐，是 text-align: center;

vertical-align 垂直对齐，它只针对于**行内元素**或者**行内块元素**，

![](https://img-blog.csdnimg.cn/4303197ae5f14d868b6da755fbc14a16.png#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

```css
vertical-align : baseline |top |middle |bottom
```

设置或检索对象内容的垂直对其方式。

注意：

> vertical-align 不影响块级元素中的内容对齐，它只针对于**行内元素**或者**行内块元素**，
>
> 特别是行内块元素， **通常用来控制图片/表单与文字的对齐**。


### 3.1 图片、表单和文字对齐

所以我们知道，我们可以通过vertical-align 控制图片和文字的垂直关系了。 默认的图片会和文字基线对齐。

![](https://img-blog.csdnimg.cn/d92fcabe111943f5ac290ba3add4455a.png#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

### 3.2 去除图片底侧空白缝隙

![](https://img-blog.csdnimg.cn/c05be423b1eb4fe9b5665716618d09c4.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_11,color_FFFFFF,t_70,g_se,x_16#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

原因：

> 图片或者表单等行内块元素，他的底线会和父级盒子的基线对齐。
>
> 就是图片底侧会有一个空白缝隙。

解决的方法就是：

> 给img vertical-align:middle | top| bottom等等。  让图片不要和基线对齐。

![](https://img-blog.csdnimg.cn/0cb634975eec41db86160d80ebc4634a.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_16,color_FFFFFF,t_70,g_se,x_16#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

> 给img 添加 display：block; 转换为块级元素就不会存在问题了。

![](https://img-blog.csdnimg.cn/603bc643058d4eaea2039b66bd44b6fa.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_16,color_FFFFFF,t_70,g_se,x_16#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)


## 4. 溢出的文字省略号显示

### 4.1 white-space

white-space设置或检索对象内文本显示方式。通常我们使用于强制一行显示内容

```css
white-space:normal;默认处理方式

white-space:nowrap;强制在同一行内显示所有文本，直到文本结束或者遭遇br标签对象才换行。
```

### 4.2 text-overflow 文字溢出

设置或检索是否使用一个省略标记（...）标示对象内文本的溢出

```css
text-overflow : clip;不显示省略标记（...），而是简单的裁切 
text-overflow：ellipsis;当对象内文本溢出时显示省略标记（...）
```

**注意**：

一定要首先强制一行内显示，再次和overflow属性  搭配使用

![](https://img-blog.csdnimg.cn/b05b935b438447139b886a96941ee662.png#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

### 4.3 总结三步曲

```css
/*1. 先强制一行内显示文本*/
white-space: nowrap;
/*2. 超出的部分隐藏*/
overflow: hidden;
/*3. 文字用省略号替代超出的部分*/
text-overflow: ellipsis;
```

### 溢出案例

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>溢出的文字省略号显示</title>
	<style>
		div {
			width: 150px;
			height: 25px;
			border: 1px solid pink;
			/*当文字显示不开的时候，自动换行*/
			/*white-space: normal;*/
			/*1. 要文字强制一行内显示 除非 遇到 br   */
			white-space: nowrap;
			/*2. 溢出隐藏*/
			overflow: hidden;
			/*3. 文字溢出 用省略号替代  ellipsis 省略号*/
			text-overflow: ellipsis;

		}
	</style>
</head>
<body>
	<div>hi~ aaaaaaaaaaaaaaaaaaaaaaa-欢迎你</div>
</body>
</html>
```



## 5. CSS精灵技术（sprite) 重点

### 5.1 为什么需要精灵技术

![](https://img-blog.csdnimg.cn/9fec2470b5354184a36a14b4acd4b007.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

图所示为网页的请求原理图，当用户访问一个网站时，需要向服务器发送请求，网页上的每张图像都要经过一次请求才能展现给用户。

然而，一个网页中往往会应用很多小的背景图像作为修饰，当网页中的图像过多时，服务器就会频繁地接受和发送请求，这将大大降低页面的加载速度。

> **为了有效地减少服务器接受和发送请求的次数，提高页面的加载速度。**


出现了CSS精灵技术（也称CSS Sprites、CSS雪碧）。

### 5.2 精灵技术讲解

CSS 精灵其实是将网页中的一些背景图像整合到一张大图中（精灵图），然而，各个网页元素通常只需要精灵图中不同位置的某个小图，要想精确定位到精灵图中的某个小图。

![](https://img-blog.csdnimg.cn/0916c453b945411fb75141299f254839.png#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

这样，当用户访问该页面时，只需向服务发送一次请求，网页中的背景图像即可全部展示出来。

我们需要使用CSS的

> background-image

> background-repeat

> background-position属性进行背景定位，

> 其中最关键的是使用background-position 属性精确地定位。

### 5.3 精灵技术使用的核心总结

首先我们知道，css精灵技术主要针对于背景图片，插入的图片img 是不需要这个技术的。

1. 精确测量，每个小背景图片的大小和 位置。
2. 给盒子指定小背景图片时， 背景定位基本都是 负值。

### 精灵图案例

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>体会css精灵技术</title>
	<style>
		.icon1 {
			width: 23px;
			height: 23px;
			background: url(images/index.png) no-repeat  0 -107px;
			/*background-position: 0 -107px;*/
		}
		.icon2 {
			width: 23px;
			height: 23px;
			background: url(images/index.png) no-repeat -157px -107px;
			margin: 100px;
		}
	</style>
</head>
<body>
	<div class="icon1"></div>
	<div class="icon2"></div>
</body>
</html>
```

## 7. 拓展@

### 7.1 margin负值之美

#### 1). 负边距+定位：水平垂直居中

咱们前面讲过， 一个绝对定位的盒子， 利用  父级盒子的 50%，  然后 往左(上) 走 自己宽度的一半 ，可以实现盒子水平垂直居中。

#### 2). 压住盒子相邻边框

![](https://img-blog.csdnimg.cn/40f01ce01fe947edbfe637664d463c2e.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaGFuZ2FvMjMz,size_20,color_FFFFFF,t_70,g_se,x_16#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		div {
			/*浮动的盒子是紧贴在一起的*/
			float: left;
			width: 200px;
			height: 300px;
			border: 1px solid #ccc;
			margin-left: -1px;
			margin-top: -1px;
		}
	</style>
</head>
<body>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>margin负值之美-突出显示某个盒子</title>
	<style>
		div {
			position: relative;
			/*浮动的盒子是紧贴在一起的*/
			float: left;
			width: 200px;
			height: 300px;
			border: 1px solid #ccc;
			margin-left: -1px;
			margin-top: -1px;
		}
		/*鼠标经过div 的意思  p:hover */
		div:hover {
			/*我要让当前鼠标经过的这个div 升到最高处来就好了*/
			/*定位的盒子是最高层的  */
			border: 1px solid #f40;
			/*都是定位的盒子，我们通过z-index 来实现层级关系*/
			z-index: 1; 

		}
	</style>
</head>
<body>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
</body>
</html>
```



### 7.2 CSS三角形之美

![在这里插入图片描述](https://img-blog.csdnimg.cn/be8116e9d8cf41ec9892225278d064bd.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5qC86Zu354uQ5oCd,size_20,color_FFFFFF,t_70,g_se,x_16)


```css
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		div {
			/*我们用css 边框可以模拟三角效果*/
			width: 0;
			height: 0;
			border-top: 50px solid red;
			border-right: 50px solid green;
			border-bottom: 50px solid blue;
			border-left: 50px solid pink;
		}
		p {
			width: 0;
			height: 0;
			border-style: solid;
			border-width: 50px;
			border-color:  transparent transparent transparent red;
			font-size: 0;
			line-height: 0;
		}
	</style>
</head>
<body>
	<div></div>
	<p></p>
</body>
</html>
```

一张图， 你就知道 css 三角是怎么来的了, 做法如下：

![](https://img-blog.csdnimg.cn/1aeff939bd6c4cb78a52aa44365a98c0.png#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

1. 我们用css 边框可以模拟三角效果
2. 宽度高度为0
3. 我们4个边框都要写， 只保留需要的边框颜色，其余的不能省略，都改为 transparent 透明就好了
4. 为了照顾兼容性 低版本的浏览器，加上 font-size: 0;  line-height: 0;



# BFC

在理解BFC之前，我们需要先回顾标准流布局的概念

## **标准流**

* 标准流块元素独占一行
* 标准流块元素在垂直方向依次摆放
* 标准流块元素父子会产生外边距塌陷
* ....

## **BFC的概念**

理解完标准流后，我们介绍下BFC，什么是BFC？BFC全称为：Block **Formatting Context——块级格式化布局，简称BFC**，**它是一块独立的渲染区域，这个区域决定了标准流块元素的布局。** 也就是说，BFC是一块区域，作用是决定标准流块盒的布局。

通俗来讲：BFC 是一个独立的布局环境，可以理解为一个容器，在这个容器中按照一定规则进行物品摆放，并且不会影响其它环境中的物品。如果一个元素符合触发 BFC 的条件，则 BFC 中的元素布局不受外部影响。

BFC目的是形成一个相对于外界完全独立的空间，让内部的子元素不会影响到外部的元素

## **BFC的创建**

BFC由某个HTML元素创建，下列元素会在其内部创建BFC区域。

- 根元素：body；
- 元素设置浮动：float 除 none 以外的值；
- 元素设置绝对定位：position (absolute、fixed)；
- display 值为：inline-block、table-cell、table-caption、flex 等；
- overflow 值为：hidden、auto、scroll；

**BFC 的特点：**

- 垂直方向上，自上而下排列，和文档流的排列方式一致。
- 在 BFC 中上下相邻的两个容器的 margin 会重叠
- 计算 BFC 的高度时，需要计算浮动元素的高度
- BFC 区域不会与浮动的容器发生重叠
- BFC 是独立的容器，容器内部元素不会影响外部元素
- 每个元素的左 margin 值和容器的左 border 相接触

**BFC 的作用：**

- **解决 margin 的重叠问题**：由于 BFC 是一个独立的区域，内部的元素和外部的元素互不影响，将两个元素变为两个 BFC，就解决了 margin 重叠的问题。
- **解决高度塌陷的问题**：在对子元素设置浮动后，父元素会发生高度塌陷，也就是父元素的高度变为 0。解决这个问题，只需要把父元素变成一个 BFC。常用的办法是给父元素设置`overflow:hidden`。
- **创建自适应两栏布局**：可以用来创建自适应两栏布局：左边的宽度固定，右边的宽度自适应。


图示：

![在这里插入图片描述](https://img-blog.csdnimg.cn/ca82d90739834b3a912900d9e2e0d4ad.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5qC86Zu354uQ5oCd,size_20,color_FFFFFF,t_70,g_se,x_16)


注意到没有，每个元素创建的BFC都是互相独立的，元素A、B、C的BFC跟其他元素创建的BFC或者根元素创建的BFC都是相互独立。

## **BFC的特性**

1. 不同的BFC在进行渲染时互不干扰
2. 创建BFC的元素隔绝了它内部BFC与外部BFC的联系，内部的渲染不会影响到外部

## **BFC的应用**

### 解决高度坍塌的问题

![在这里插入图片描述](https://img-blog.csdnimg.cn/cd453885b10d4170ae40ebe0d5804654.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5qC86Zu354uQ5oCd,size_20,color_FFFFFF,t_70,g_se,x_16)


```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .father {
            width: 500px;
            border: 1px solid red;
            margin: 100px auto;
        }
        .son {
            width: 100px;
            height: 100px;
            background-color: aquamarine;
        }
    </style>
</head>

<body>
    <div class="father">
        <div class="son"></div>
    </div>
</body>

</html>
```

在父类元素的样式中添加下列三种属性之一使其生成BFC

- 浮动元素
- 绝对定位
- overflow（最常用，可不改变父类元素的布局方式）

```css
.father {
    width: 500px;
    border: 1px solid red;
    margin: 100px auto;
    overflow: hidden;
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/b6c2b041ed3b4401b4da1cb96eff31b8.png)


这里就是因为BFC的特性，互相独立的BFC互不干扰。当子类元素超出父类元素时会造成对其他BFC的干扰，所以需要将子类元素包含在自己的BFC中，所以自动扩展了高度。

### 相邻父子元素外边距合并问题

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .father {
            width: 300px;
            height: 300px;
            background-color: antiquewhite;
            margin: 100px auto;
            /* overflow: hidden; */
        }
        .son {
            width: 100px;
            height: 100px;
            background-color: aquamarine;
            margin: 40px;
        }
    </style>
</head>

<body>
    <div class="father">
        <div class="son"></div>
    </div>
</body>

</html>
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/348ae03c1f74404890eb9bc06b908a61.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5qC86Zu354uQ5oCd,size_16,color_FFFFFF,t_70,g_se,x_16)


可以看到，子元素的左右下外边距都能显示出效果，但是子类元素不显示上外边距效果，这是因为子类的上外边距跟父类元素的上外边距合并了，这里用BFC处理，在父类中创建BFC。

```css
.father {
    width: 300px;
    height: 300px;
    background-color: antiquewhite;
    margin: 100px auto;
    overflow: hidden;
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/8bbf2b99135540b6b0526ca2a7249850.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5qC86Zu354uQ5oCd,size_17,color_FFFFFF,t_70,g_se,x_16)


BFC就可以理解为把标准流中块元素强制执行（有的情况在标准流中块的特性会失效，比如外边距塌陷...）

# 面试题

## css基础

### 1. 伪元素和伪类的区别和作用

- 伪元素：在内容元素的前后插入额外的元素或样式，但是这些元素实际上不在文档树中。它们只在外部显示可见，因此，称为“伪”元素。例如：

```css
p::before {content:"第一章：";}
p::after {content:"Hot!";}
p::first-line {background:red;}
p::first-letter {font-size:30px;}
```

> 伪元素可以创建一些文档语言无法创建的虚拟元素。比如：文档语言没有一种机制可以描述元素内容的第一个字母或第一行，但伪元素可以做到(::first-letter、::first-line)。同时，伪元素还可以创建源文档不存在的内容，比如使用::before 或 ::after。

- 伪类：将特殊的效果添加到特定选择器上。它是已有元素上添加类别的，不会产生新的元素。例如：

```css
a:hover {color: #FF00FF}
p:first-child {color: red}
```

**总结：**伪类是通过在元素选择器上加⼊伪类改变元素状态，⽽伪元素通过对元素的操作进行对元素的改变。伪元素和伪类都**不会出现在源文档或者文档树中**。



### 2.  CSS 优化和提高性能的方法有哪些

**加载性能：**

（1）css 压缩：将写好的 css 进行打包压缩，可以减小文件体积。

（2）css 单一样式：当需要下边距和左边距的时候，很多时候会选择使用 margin:top 0 bottom 0；但 margin-bottom:bottom;margin-left:left;执行效率会更高。

（3）减少使用@import，建议使用 link，因为后者在页面加载时一起加载，前者是等待页面加载完成之后再进行加载。

**选择器性能：**

（1）关键选择器（key selector）。选择器的最后面的部分为关键选择器（即用来匹配目标元素的部分）。CSS 选择符是从右到左进行匹配的。当使用后代选择器的时候，浏览器会遍历所有子元素来确定是否是指定的元素等等；

（2）如果规则拥有 ID 选择器作为其关键选择器，则不要为规则增加标签。过滤掉无关的规则（这样样式系统就不会浪费时间去匹配它们了）。

（3）避免使用通配规则，如\*{}计算次数惊人，只对需要用到的元素进行选择。

（4）尽量少的去对标签进行选择，而是用 class。

（5）尽量少的去使用后代选择器，降低选择器的权重值。后代选择器的开销是最高的，尽量将选择器的深度降到最低，最高不要超过三层，更多的使用类来关联每一个标签元素。

（6）了解哪些属性是可以通过继承而来的，然后避免对这些属性重复指定规则。

**渲染性能：**

（1）慎重使用高性能属性：浮动、定位。

（2）尽量减少页面重排、重绘。

（3）去除空规则：｛｝。空规则的产生原因一般来说是为了预留样式。去除这些空规则无疑能减少 css 文档体积。

（4）属性值为 0 时，不加单位。

（5）属性值为浮动小数 0.\*\*，可以省略小数点之前的 0。

（6）标准化各种浏览器前缀：带浏览器前缀的在前。标准属性在后。

（7）不使用@import 前缀，它会影响 css 的加载速度。

（8）选择器优化嵌套，尽量避免层级过深。

（9）css 雪碧图，同一页面相近部分的小图标，方便使用，减少页面的请求次数，但是同时图片本身会变大，使用时，优劣考虑清楚，再使用。

（10）正确使用 display 的属性，由于 display 的作用，某些样式组合会无效，徒增样式体积的同时也影响解析性能。

（11）不滥用 web 字体。对于中文网站来说 WebFonts 可能很陌生，国外却很流行。web fonts 通常体积庞大，而且一些浏览器在下载 web fonts 时会阻塞页面渲染损伤性能。

**可维护性、健壮性：**

（1）将具有相同属性的样式抽离出来，整合并通过 class 在页面中进行使用，提高 css 的可维护性。

（2）样式与内容分离：将 css 代码定义到外部 css 中。





### 3. CSS 预处理器/后处理器是什么？为什么要使用它们？

**预处理器，**如：`less`，`sass`，`stylus`，用来预编译`sass`或者`less`，增加了`css`代码的复用性。层级，`mixin`， 变量，循环， 函数等对编写以及开发 UI 组件都极为方便。

**后处理器，** 如： `postCss`，通常是在完成的样式表中根据`css`规范处理`css`，让其更加有效。目前最常做的是给`css`属性添加浏览器私有前缀，实现跨浏览器兼容性的问题。

`css`预处理器为`css`增加一些编程特性，无需考虑浏览器的兼容问题，可以在`CSS`中使用变量，简单的逻辑程序，函数等在编程语言中的一些基本的性能，可以让`css`更加的简洁，增加适应性以及可读性，可维护性等。

其它`css`预处理器语言：`Sass（Scss）`, `Less`, `Stylus`, `Turbine`, `Swithch css`, `CSS Cacheer`, `DT Css`。

使用原因：

- 结构清晰， 便于扩展
- 可以很方便的屏蔽浏览器私有语法的差异
- 可以轻松实现多重继承
- 完美的兼容了`CSS`代码，可以应用到老项目中



### 4. ::before 和 :after 的双冒号和单冒号有什么区别？

（1）冒号(`:`)用于`CSS3`伪类，双冒号(`::`)用于`CSS3`伪元素。

（2）`::before`就是以一个子元素的存在，定义在元素主体内容之前的一个伪元素。并不存在于`dom`之中，只存在在页面之中。

**注意：** `:before `和 `:after` 这两个伪元素，是在`CSS2.1`里新出现的。起初，伪元素的前缀使用的是单冒号语法，但随着`Web`的进化，在`CSS3`的规范里，伪元素的语法被修改成使用双冒号，成为`::before`、`::after`。





### 5. 单行、多行文本溢出隐藏

- 单行文本溢出

```css
overflow: hidden;            // 溢出隐藏
text-overflow: ellipsis;      // 溢出用省略号显示
white-space: nowrap;         // 规定段落中的文本不进行换行
```

- 多行文本溢出

```css
overflow: hidden;            // 溢出隐藏
text-overflow: ellipsis;     // 溢出用省略号显示
display:-webkit-box;         // 作为弹性伸缩盒子模型显示。
-webkit-box-orient:vertical; // 设置伸缩盒子的子元素排列方式：从上到下垂直排列
-webkit-line-clamp:3;        // 显示的行数
```

注意：由于上面的三个属性都是 CSS3 的属性，不是所有浏览器都可以兼容，所以要在前面加一个`-webkit-` 来兼容一部分浏览器。



### 6. 对 CSS 工程化的理解

CSS 工程化是为了解决以下问题：

1. **宏观设计**：CSS 代码如何组织、如何拆分、模块结构怎样设计？
2. **编码优化**：怎样写出更好的 CSS？
3. **构建**：如何处理我的 CSS，才能让它的打包结果最优？
4. **可维护性**：代码写完了，如何最小化它后续的变更成本？如何确保任何一个同事都能轻松接手？

以下三个方向都是时下比较流行的、普适性非常好的 CSS 工程化实践：

- 预处理器：Less、 Sass 等；
- 重要的工程化插件： PostCss；
- Webpack loader 等 。

基于这三个方向，可以衍生出一些具有典型意义的子问题，这里我们逐个来看：

**（1）预处理器：为什么要用预处理器？它的出现是为了解决什么问题？**

预处理器，其实就是 CSS 世界的“轮子”。预处理器支持我们写一种类似 CSS、但实际并不是 CSS 的语言，然后把它编译成 CSS 代码：

![image](https://img-blog.csdnimg.cn/img_convert/bbbedbb1d63a927a0d782dc9b7979c70.png)

那为什么写 CSS 代码写得好好的，偏偏要转去写“类 CSS”呢？这就和本来用 JS 也可以实现所有功能，但最后却写 React 的 jsx 或者 Vue 的模板语法一样——为了爽！要想知道有了预处理器有多爽，首先要知道的是传统 CSS 有多不爽。随着前端业务复杂度的提高，前端工程中对 CSS 提出了以下的诉求：

1. 宏观设计上：我们希望能优化 CSS 文件的目录结构，对现有的 CSS 文件实现复用；
2. 编码优化上：我们希望能写出结构清晰、简明易懂的 CSS，需要它具有一目了然的嵌套层级关系，而不是无差别的一铺到底写法；我们希望它具有变量特征、计算能力、循环能力等等更强的可编程性，这样我们可以少写一些无用的代码；
3. 可维护性上：更强的可编程性意味着更优质的代码结构，实现复用意味着更简单的目录结构和更强的拓展能力，这两点如果能做到，自然会带来更强的可维护性。

这三点是传统 CSS 所做不到的，也正是预处理器所解决掉的问题。预处理器普遍会具备这样的特性：

- 嵌套代码的能力，通过嵌套来反映不同 css 属性之间的层级关系 ；
- 支持定义 css 变量；
- 提供计算函数；
- 允许对代码片段进行 extend 和 mixin；
- 支持循环语句的使用；
- 支持将 CSS 文件模块化，实现复用。

**（2）PostCss：PostCss 是如何工作的？我们在什么场景下会使用 PostCss？**

PostCss 仍然是一个对 CSS 进行解析和处理的工具，它会对 CSS 做这样的事情：

![img](https://img-blog.csdnimg.cn/img_convert/8235c8821d64907d9a7867b28a8bbdf6.png)

它和预处理器的不同就在于，预处理器处理的是 类 CSS，而 PostCss 处理的就是 CSS 本身。Babel 可以将高版本的 JS 代码转换为低版本的 JS 代码。PostCss 做的是类似的事情：它可以编译尚未被浏览器广泛支持的先进的 CSS 语法，还可以自动为一些需要额外兼容的语法增加前缀。更强的是，由于 PostCss 有着强大的插件机制，支持各种各样的扩展，极大地强化了 CSS 的能力。

PostCss 在业务中的使用场景非常多：

- 提高 CSS 代码的可读性：PostCss 其实可以做类似预处理器能做的工作；
- 当我们的 CSS 代码需要适配低版本浏览器时，PostCss 的 [Autoprefixer](https://github.com/postcss/autoprefixer) 插件可以帮助我们自动增加浏览器前缀；
- 允许我们编写面向未来的 CSS：PostCss 能够帮助我们编译 CSS next 代码；

**（3）Webpack 能处理 CSS 吗？如何实现？**

Webpack 能处理 CSS 吗：

- **Webpack 在裸奔的状态下，是不能处理 CSS 的**，Webpack 本身是一个面向 JavaScript 且只能处理 JavaScript 代码的模块化打包工具；
- Webpack 在 loader 的辅助下，是可以处理 CSS 的。

如何用 Webpack 实现对 CSS 的处理：

- Webpack 中操作 CSS 需要使用的两个关键的 loader：css-loader 和 style-loader

- 注意，答出“用什么”有时候可能还不够，面试官会怀疑你是不是在背答案，所以你还需要了解每个 loader 都做了什么事情：

  * css-loader：导入 CSS 模块，对 CSS 代码进行编译处理；

  - style-loader：创建 style 标签，把 CSS 内容写入标签。

在实际使用中，**css-loader 的执行顺序一定要安排在 style-loader 的前面**。因为只有完成了编译过程，才可以对 css 代码进行插入；若提前插入了未编译的代码，那么 webpack 是无法理解这坨东西的，它会无情报错。

### 7. **display、float、position 的关系**

（1）首先判断 display 属性是否为 none，如果为 none，则 position 和 float 属性的值不影响元素最后的表现。

（2）然后判断 position 的值是否为 absolute 或者 fixed，如果是，则 float 属性失效，并且 display 的值应该被设置为 table 或者 block，具体转换需要看初始转换值。

（3）如果 position 的值不为 absolute 或者 fixed，则判断 float 属性的值是否为 none，如果不是，则 display 的值则按上面的规则转换。注意，如果 position 的值为 relative 并且 float 属性的值存在，则 relative 相对于浮动后的最终位置定位。

（4）如果 float 的值为 none，则判断元素是否为根元素，如果是根元素则 display 属性按照上面的规则转换，如果不是，则保持指定的 display 属性值不变。

总的来说，可以把它看作是一个类似优先级的机制，"position:absolute"和"position:fixed"优先级最高，有它存在的时候，浮动不起作用，'display'的值也需要调整；其次，元素的'float'特性的值不是"none"的时候或者它是根元素的时候，调整'display'的值；最后，非根元素，并且非浮动元素，并且非绝对定位的元素，'display'特性值同设置值。

## 页面布局

### 1. 常见的 CSS 布局单位

常用的布局单位包括像素（`px`），百分比（`%`），`em`，`rem`，`vw/vh`。

**（1）像素**（`px`）是页面布局的基础，一个像素表示终端（电脑、手机、平板等）屏幕所能显示的最小的区域，像素分为两种类型：CSS 像素和物理像素：

- **CSS 像素**：为 web 开发者提供，在 CSS 中使用的一个抽象单位；
- **物理像素**：只与设备的硬件密度有关，任何设备的物理像素都是固定的。

**（2）百分比**（`%`），当浏览器的宽度或者高度发生变化时，通过百分比单位可以使得浏览器中的组件的宽和高随着浏览器的变化而变化，从而实现响应式的效果。一般认为子元素的百分比相对于直接父元素。

**（3）em 和 rem**相对于 px 更具灵活性，它们都是相对长度单位，它们之间的区别：**em 相对于父元素，rem 相对于根元素。**

- **em：** 文本相对长度单位。相对于当前对象内文本的字体尺寸。如果当前行内文本的字体尺寸未被人为设置，则相对于浏览器的默认字体尺寸(默认 16px)。(相对父元素的字体大小倍数)。
- **rem：** rem 是 CSS3 新增的一个相对单位，相对于根元素（html 元素）的 font-size 的倍数。**作用**：利用 rem 可以实现简单的响应式布局，可以利用 html 元素中字体的大小与屏幕间的比值来设置 font-size 的值，以此实现当屏幕分辨率变化时让元素也随之变化。

**（4）vw/vh**是与视图窗口有关的单位，vw 表示相对于视图窗口的宽度，vh 表示相对于视图窗口高度，除了 vw 和 vh 外，还有 vmin 和 vmax 两个相关的单位。

- vw：相对于视窗的宽度，视窗宽度是 100vw；
- vh：相对于视窗的高度，视窗高度是 100vh；
- vmin：vw 和 vh 中的较小值；
- vmax：vw 和 vh 中的较大值；

**vw/vh** 和百分比很类似，两者的区别：

- 百分比（`%`）：大部分相对于祖先元素，也有相对于自身的情况比如（border-radius、translate 等)
- vw/vm：相对于视窗的尺寸

### 2. px、em、rem 的区别及使用场景

**三者的区别：**

- px 是固定的像素，一旦设置了就无法因为适应页面大小而改变。
- em 和 rem 相对于 px 更具有灵活性，他们是相对长度单位，其长度不是固定的，更适用于响应式布局。
- em 是相对于其父元素来设置字体大小，这样就会存在一个问题，进行任何元素设置，都有可能需要知道他父元素的大小。而 rem 是相对于根元素，这样就意味着，只需要在根元素确定一个参考值。

**使用场景：**

- 对于只需要适配少部分移动设备，且分辨率对页面影响不大的，使用 px 即可 。
- 对于需要适配各种移动设备，使用 rem，例如需要适配 iPhone 和 iPad 等分辨率差别比较挺大的设备。



### 3. 两栏布局的实现

一般两栏布局指的是**左边一栏宽度固定，右边一栏宽度自适应**，两栏布局的具体实现：

- 利用浮动，左侧元素设置固定大小，并左浮动，右侧元素设置 overflow: hidden; 这样右边就触发了 BFC，BFC 的区域不会与浮动元素发生重叠，所以两侧就不会发生重叠。

```css
.left{
     width: 100px;
     height: 200px;
     background: red;
     float: left;
 }
 .right{
     height: 300px;
     background: blue;
     overflow: hidden;
 }
```

- 利用 flex 布局，将左边元素设置为固定宽度 200px，将右边的元素设置为 flex:1。

```css
.outer {
  display: flex;
  height: 100px;
}
.left {
  width: 200px;
  background: tomato;
}
.right {
  flex: 1;
  background: gold;
}
```

- 利用绝对定位，将父级元素设置为相对定位。左边元素设置为 absolute 定位，并且宽度设置为 200px。将右边元素的 margin-left 的值设置为 200px。

```css
.outer {
  position: relative;
  height: 100px;
}
.left {
  position: absolute;
  width: 200px;
  height: 100px;
  background: tomato;
}
.right {
  margin-left: 200px;
  background: gold;
}
```

- flex布局，主轴排列设置为 justify-content: flex-start; 左边宽度给 200px，右边设置 width 100%

```css
.outer {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  height: 100px;
}
.left {
  width: 200px;
  background: tomato;
}
.right {
  width: 100%;
  background: gold;
}
```



### 4. 三栏布局的实现

三栏布局一般指的是页面中一共有三栏，**左右两栏宽度固定，中间自适应的布局**，三栏布局的具体实现：

* 利用**绝对定位**，左右两栏设置为绝对定位，中间设置对应方向大小的 margin 的值。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>
    <style>
      .outer {
        position: relative;
        height: 100px;
      }

      .left {
        position: absolute;
        width: 100px;
        height: 100px;
        background: tomato;
      }

      .right {
        position: absolute;
        top: 0;
        right: 0;
        width: 200px;
        height: 100px;
        background: gold;
      }

      .center {
        margin-left: 100px;
        margin-right: 200px;
        height: 100px;
        background: lightgreen;
      }
    </style>
  </head>

  <body>
    <div class="outer">
      <div class="left"></div>
      <div class="center"></div>
      <div class="right"></div>
    </div>
  </body>
</html>

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/7628ebc6781945cd9ee08f340fe1068c.png)
* 利用 flex 布局，左右两栏设置固定大小，中间一栏设置为 flex:1。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>
    <style>
      .outer {
        display: flex;
        height: 100px;
      }

      .left {
        width: 100px;
        background: tomato;
      }

      .right {
        width: 100px;
        background: gold;
      }

      .center {
        flex: 1;
        background: lightgreen;
      }
    </style>
  </head>

  <body>
    <div class="outer">
      <div class="left"></div>
      <div class="center"></div>
      <div class="right"></div>
    </div>
  </body>
</html>

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/6f9ff787028143faae0846dfa333b6f0.png)

* 利用浮动，左右两栏设置固定大小，并设置对应方向的浮动。中间一栏设置左右两个方向的 margin 值，注意这种方式，**中间一栏必须放到最后：**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>
    <style>
	.outer {
	 	height: 100px;
	}
	
	.left {
		 float: left;
		 width: 100px;
		 height: 100px;
		 background: tomato;
	}
	
	.right {
		 float: right;
		 width: 200px;
		 height: 100px;
		 background: gold;
	}
	
	.center {
		 height: 100px;
		 margin-left: 100px;
		 margin-right: 200px;
		 background: lightgreen;
	}
    </style>
  </head>

  <body>
    <div class="outer">
      <div class="left"></div>
      <div class="right"></div>
      <div class="center"></div>
    </div>
  </body>
</html>

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/64a508c550024d3aab5fa15201f6883b.png)

### 5.水平垂直居中的实现
* 利用绝对定位，先将元素的左上角通过 top:50%和 left:50%定位到页面的中心，然后再通过 translate 来调整元素的中心点到页面的中心。该方法需要**考虑浏览器兼容问题。**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>
    <style>
      .parent {
        position: relative;
        height: 500px;
      }

      .child {
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        width: 50px;
        height: 50px;
        background-color: aquamarine;
      }
    </style>
  </head>

  <body>
    <div class="parent">
      <div class="child"></div>
    </div>
  </body>
</html>

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/c4af5a8b63cc49f1a21d7171f6f5e1d4.png)

* 使用 flex 布局，通过 align-items:center 和 justify-content:center 设置容器的垂直和水平方向上为居中对齐，然后它的子元素也可以实现垂直和水平的居中。该方法要**考虑兼容的问题**，该方法在移动端用的较多：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>
    <style>
      .parent {
        display: flex;
        justify-content: center;
        align-items: center;
      }

      .child {
        width: 50px;
        height: 50px;
        margin: auto;
        background-color: aquamarine;
      }
    </style>
  </head>

  <body>
    <div class="parent">
      <div class="child"></div>
    </div>
  </body>
</html>

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/aef21e4027bb4f5388e0be899fa955f2.png)

## 场景应用
### 1. 实现一个三角形

CSS 绘制三角形主要用到的是 border 属性，也就是边框。

平时在给盒子设置边框时，往往都设置很窄，就可能误以为边框是由矩形组成的。实际上，border 属性是由三角形组成的，下面看一个例子：

```css
div {
    width: 0;
    height: 0;
    border: 100px solid;
    border-color: orange blue red green;
}
```

将元素的长宽都设置为 0，显示出来的效果是这样的：
![在这里插入图片描述](https://img-blog.csdnimg.cn/4257561c948c4f30b721a0e2cca50390.png)
所以可以根据 border 这个特性来绘制三角形：
**（1）三角 1**

```css
div {
    width: 0;
    height: 0;
    border-top: 50px solid red;
    border-right: 50px solid transparent;
    border-left: 50px solid transparent;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/ecf105b4026e401897c16050e3bb9990.png)
**（2）三角 2**

```css
div {
    width: 0;
    height: 0;
    border-bottom: 50px solid red;
    border-right: 50px solid transparent;
    border-left: 50px solid transparent;
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/093fcabdd0df4237a93577ca9e280f6b.png)


**（3）三角 3**

```css
div {
    width: 0;
    height: 0;
    border-left: 50px solid red;
    border-top: 50px solid transparent;
    border-bottom: 50px solid transparent;
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/042fe245346e4eb4880f316fe353dbad.png)


**（4）三角 4**

```css
div {
    width: 0;
    height: 0;
    border-right: 50px solid red;
    border-top: 50px solid transparent;
    border-bottom: 50px solid transparent;
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/461d49ebf42b40bb96927e59f27d980e.png)


**（5）三角 5**

```css
div {
    width: 0;
    height: 0;
    border-top: 100px solid red;
    border-right: 100px solid transparent;
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/74242a3c2f7b46888b949291f73ba68f.png)


还有很多，就不一一实现了，总体的原则就是通过上下左右边框来控制三角形的方向，用边框的宽度比来控制三角形的角度。


### 2. 实现一个扇形

用 CSS 实现扇形的思路和三角形基本一致，就是多了一个圆角的样式，实现一个 90° 的扇形：

```css
div{
    border: 100px solid transparent;
    width: 0;
    height: 0;
    border-radius: 100px;
    border-top-color: red;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/6ee7ed0164fd4022b5973a1e1a0fcd6a.png)


参考文献：
1. 博学谷
2. https://blog.csdn.net/JustinST/article/details/120555377
3. https://github.com/supersea/front-end-interview
