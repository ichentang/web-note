## BFC概念

BFC(Block Formatting Context)，**块级格式化上下文**，一个创建了新的BFC的盒子是独立布局的，盒子里面的子元素的样式不会影响到外面的元素。

通俗一点来讲，可以把BFC，理解为一个封闭的大箱子，箱子内部的元素无论如何翻江倒海，都不会影响到外部。

BFC是Web页面中**盒模型**布局的一种CSS渲染模式。它的定位体系属于 **常规文档流**。



W3C规范定义：

浮动元素和绝对定位元素，非块级盒子的块级容器（例如 inline-blocks, table-cells, 和 table-captions），以及overflow值不为“visiable”的块级盒子，都会为他们的内容创建新的BFC（块级格式上下文）。

在BFC中，盒子从顶端开始垂直地一个接一个地排列，两个盒子之间的垂直的间隙是由他们的margin 值所决定的。在一个BFC中，两个相邻的块级盒子的垂直外边距会产生折叠。

在BFC中，每一个盒子的左外边缘（margin-left）会触碰到容器的左边缘(border-left)（对于从右到左的格式来说，则触碰到右边缘）。

## 触发BFC

**W3C**中提到：

  一些元素，如 **float**，绝对定位元素，**inline-block**, **table-cell**, **table-caption**,和**overflow**的值不为visible的元素，（除了这个值已经被传到了视口的时候）将创建一个新的块级格式化上下文。



**归纳形成BFC**的几个要点：

- float的值不为none;

- position的值不为static或者relative;

- display的值为 table-cell, table-caption, inline-block, flex, 或者 inline-flex中的其中一个;

- overflow的值不为visible。

## BFC布局特点

- 内部的Box会在垂直方向，一个接一个地放置。

- Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生重叠

- 每个元素的margin box的左边， 与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此。

- BFC的区域不会与float box重叠。

- **BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之也如此。**

- 计算BFC的高度时，浮动元素也参与计算

## 创建一个BFC

创建一个新的BFC模式，只要满足 **触发BFC** 中的任何一个条件即可，即添加相关的CSS属性。



**实列：**

给容器**.container** 添加诸如：**overflow: scroll**, **overflow: hidden**, **display: flex**, **float: left**,或者 **display: table**等任何一个属性，就可以形成一个新的BFC。尽管这些条件都能形成一个BFC，但是它们各自却有着不一样的表现：

- display: table;  —— 在响应式布局中会有问题

- overflow: scroll; —— 可能会出现你不想要的滚动条

- float: left;   —— 使元素左浮动，并且其他元素对其环绕

- overflow: hidden; —— 隐藏溢出部分

总的来说，根据情况用不同的方式创建BFC。

## BFC特点及应用

#### 1、消除外边距

```html
	  <!-- html -->
	  <div class="wrap">
        <div class="item">华清远见</div>
        <div class="item">创客学院</div>
      </div>
```

```css
 	  /* css */
		.wrap {
          width:330px;
          background: #08c;
          overflow: hidden;
        }
        .item {
          width: 300px;
          height: 50px;
          margin: 15px;
          line-height: 50px;
          text-align: center;
          color: #fff;
          background: #6c0;
        }
```

效果图：![image-20200402170749727](images\image-20200402170749727.png)

item元素垂直方向之间的margin值合并了，原本应该是30px，目前只有15px。

解决方案：建立新的BFC元素包裹起来

```html
	  <!-- html -->
      <div class="wrap">
        <div class="item">华清远见</div>
        <div class="new-BFC">
            <div class="item">创客学院</div>
        </div>
      </div>
```

```css
	  /* 添加CSS属性： */
        .new-BFC {
            overflow: hidden;
        }
```

这样被新BFC元素隔离出来的item就不受外部影响了，离第一个盒子之间的垂直margin距离达到30px，如图：

![image-20200402171109733](images\image-20200402171109733.png)

#### 2、容纳内部浮动元素

根据BFC特点规则第六条：计算BFC的高度时，浮动元素也参与计算

由BFC的独立区域特性体现，BFC内部的元素不会影响到外部元素。

```html
	<!-- html -->
    <div class="content">
        <div class="child">child 01</div>
        <div class="child">child 02</div>
    </div>
```

```css
	    /* css */
        .content {
            width: 360px;
            padding: 10px;
            background: #08c;
        }
        .child {
            float: left;
            width: 150px;
            height: 50px;
            margin: 0 15px;
            line-height: 50px;
            text-align: center;
            color: #fff;
            background: #6c0;
        }
```

![image-20200402171556352](images\image-20200402171556352.png)

解决方案：这里我们可以根据W3C的规则触发父元素content形成BFC，让内部的浮动元素也参与计算，给父元素添加

```css
	    .content {
            overflow: hidden;
        }
```

如图，父级高度由子元素撑开了：

![image-20200402171826231](images\image-20200402171826231.png)

#### 3、自适应两栏布局

BFC布局规则第三条与第四条：

​       每个元素的margin box的左边， 与包含块border box的左边相接触(对于从左往右的格式化，否则相反)，即使存在浮动也是如此。

​      BFC的区域不会与float box重叠。

​     了解以上规则后，我们可以利用BFC来实现自适应两栏布局。

```html
	<!-- html -->
	<div class="wrap">
        <div class="side">side</div>
        <div class="main">main</div>
    </div>
```

```css
		/* css */
        .wrap {
            width: 300px;
            background: #08c;
        }
        .side {
            float: left;
            width: 120px;
            height: 200px;
            background: #6c0;
        }
        .main {
            height: 300px;
            background: #00f;
        }
```

根据BFC规则第三条体现为：蓝色的**main**元素以及绿色的 **浮动** 元素**side**都会紧贴 **wrap的左边** border（由于浮动元素脱离文档流会盖在蓝色盒子上面），如图：

![image-20200402172238924](images\image-20200402172238924.png)

根据BFC布局规则第四条，我们可以采用给main添加overflow: hidden;来触发新的BFC，这样新的BFC元素不会与浮动的side重叠。

```css
		.main {
            overflow: hidden;
        }
```

因此会根据父级元素的宽度以及side的宽度，自动变窄，形成侧栏固定，主体自适应宽度布局。如图所示：

![image-20200402172339937](images\image-20200402172339937.png)

#### 4、利用BFC阻止文本环绕

我们经常见到的“左图+右文本”的布局方式，根据以上原理我们也可以利用BFC来解决文字环绕的问题，让文字隔离图片并自适应排版。

```html
	<!-- html -->
	<div class="content">
        <div class="img"></div>
        <p class="info">华清远见官网,15年品牌IT培训机构。IT培训课程涵盖嵌入式、Android、Java、HTML5、大数据、VR、UI、物联网,python多个方向的编程培训。全国有12个IT就业培训直营校区,每年向社会输送软件开发培训人才上万名</p>
    </div>
```

```css
		/* css */
        .content {
            width: 300px;
            background: #08c;
        }
        .img {
            float: left;
            width: 100px;
            height: 80px;
            background: #fd0;
        }
        .info {
            background: #f66;
        }
```

如图所示：![image-20200402172527284](images\image-20200402172527284.png)

有时候我们不想要上面的展示，而是下面的效果：

![image-20200402172558769](images\image-20200402172558769.png)

那么根据上面所了解的知识，我们可以触发p元素的BFC来形成新的BFC独有区域，不与浮动的图片元素重叠，因此给.info添加能触发BFC模式的CSS属性属性即可，这里采用overflow:hidden;，你也可以试试别的能够触发BFC的属性：

```css
		.info {
            overflow: hidden;
        }
```

根据上面几个例子印证了BFC布局规则第五条：

   **BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之也如此。**

因此我们可以利用这些特性来优化我们的margin、float元素、自适应布局等布局。

