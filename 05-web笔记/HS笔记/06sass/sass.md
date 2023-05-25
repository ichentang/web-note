## Sass入门

### Sass简介

Sass (英文全称：Syntactically Awesome Stylesheets) 是一个最初由 Hampton Catlin 设计并由 Natalie Weizenbaum 开发的层叠样式表语言。

​     Sass 是一个 CSS 预处理器。  Less

​     Sass 是 CSS 扩展语言，可以帮助我们减少 CSS 重复的代码，节省开发时间。

​     Sass 完全兼容所有版本的 CSS。

​     Sass 是一款强化 CSS 的辅助工具，它在 CSS 语法的基础上增加了变量 (variables)、嵌套 (nested rules)、混合 (mixins)、导入 (inline imports) 等高级功能，这些拓展令 CSS 更加强大与优雅。

​     Sass 生成良好格式化的 CSS 代码，易于组织和维护。

​     Sass 文件后缀为 .scss或 .sass。

### 安装Sass和基本使用

浏览器并不支持 Sass 代码。因此，你需要使用一个 Sass 预处理器将 Sass 代码转换为 CSS 代码。

首先执行以下命令安装sass：

```
 npm install –g sass
```

把sass编译成css的命令：

 sass  sass文件目录:css文件目录。    例： 

```
sass sass/style.scss:css/style.css
```

自动编译sass（监视sass变化）的命令：

sass --watch sass文件目录:css文件保存目录   例：

```
sass --watch sass:css
```

你的目录里有很多 Sass 文件，你可以使用此Sass命令来监视整个目录

### 修改编译输出的css格式

编译排版格式：

  expanded   扩展

  compressed 压缩

指定排版格式编译命令：

```
sass --watch sass:css --style compressed   
```

### .sass和.scss的区别

Sass 有两种语法格式：

​    一种是 SCSS (Sassy CSS) ——这种格式仅在 CSS3 语法的基础上进行拓展，所有 CSS3 语法在 SCSS 中都是通用的，同时加入 Sass 的特色功能。此外，SCSS 也支持大多数 CSS hacks 写法以及浏览器前缀写法 (vendor-specific syntax)，以及早期的 IE 滤镜写法。这种格式以 .scss 作为拓展名。

​    另一种也是最早的 Sass 语法格式，被称为缩进格式 (Indented Sass) 通常简称 “Sass”，是一种简化格式。它使用 “缩进” 代替 “花括号” 表示属性属于某个选择器，用 “换行” 代替 “分号” 分隔属性，很多人认为这样做比 SCSS 更容易阅读，书写也更快速。缩进格式也可以使用 Sass 的全部功能，只是与 SCSS 相比个别地方采取了不同的表达方式，具体请查看：https://sass-lang.com/documentation/syntax。这种格式以 .sass 作为拓展名。

### 注释 /\* \*/  与  //

Sass 支持标准的 CSS 多行注释 /* */，以及单行注释 //，前者会 被完整输出到编译后的 CSS 文件中，而后者则不会

```scss
/* 多行注释
 * 会包含在没有压缩之后的css里面
 * 天王盖地虎
 * 宝塔镇河妖
*/
 body { color: black; }

 // 单行注释不会出现在css里面 // 你脸红啥？
 a { color: green; }

```

编译为:

```css
/* 多行注释
 * 会包含在没有压缩之后的css里面
 * 天王盖地虎
 * 宝塔镇河妖
*/
body {
  color: black;
}
a {
  color: green;
}

```

将 **!** 作为多行注释的第一个字符表示在压缩输出模式下保留这条注释并输出到 CSS 文件中，通常用于添加版权信息。

## CSS功能拓展

### 嵌套规则

Sass 嵌套 CSS 选择器类似于 HTML 的嵌套规则。

Sass 允许将一套 CSS 样式嵌套进另一套样式中，内层的样式将它外层的选择器作为父选择器，例如：

```scss
#main p {				
    color: #00ff00;
    width: 97%;
  
    .redbox {
      background-color: #ff0000;
      color: #000000;
    }
}
```

编译为

```css
#main p {
  color: #00ff00;
  width: 97%; }
  #main p .redbox {
    background-color: #ff0000;
    color: #000000; }
```

嵌套功能避免了重复输入父选择器，而且令复杂的 CSS 结构更易于管理：

```scss
#main {
    width: 97%;
  
    p, div {
      font-size: 2em;
      a { font-weight: bold; }
    }
  
    pre { font-size: 3em; }
}
```

编译为

```css
#main {
  width: 97%;
}
#main p, #main div {
  font-size: 2em;
}
#main p a, #main div a {
  font-weight: bold;
}
#main pre {
  font-size: 3em;
}
```

### 父选择器 &

在嵌套 CSS 规则时，有时也需要直接使用嵌套外层的父选择器，例如，当给某个元素设定 hover 样式时，或者当 body 元素有某个 classname 时，可以用 **&** 代表嵌套规则外层的父选择器。

```scss
a {
    font-weight: bold;
    text-decoration: none;
    &:hover { 
		text-decoration: underline; 
    }
    body.firefox & { 
 	    font-weight: normal; 
	}
}
```

编译为

```css
a {
  font-weight: bold;
  text-decoration: none;
}
a:hover {
  text-decoration: underline;
}
body.firefox a {
  font-weight: normal;
}
```

编译后的 CSS 文件中 **&** 将被替换成嵌套外层的父选择器，如果含有多层嵌套，最外层的父选择器会一层一层向下传递：

```scss
#main {
    color: black;
    a {
      font-weight: bold;
      &:hover { color: red; }
    }
}
```

编译为

```css
#main {
  color: black;
}
#main a {
  font-weight: bold;
}
#main a:hover {
  color: red;
}
```

**&** 必须作为选择器的第一个字符，其后可以跟随后缀生成复合的选择器，例如：

```scss
#main {
    color: black;
    &-sidebar { 
		border: 1px solid; 
	}
}
```

编译为

```css
#main {
  color: black;
}
#main-sidebar {
  border: 1px solid;
}
```

### 属性嵌套

有些 CSS 属性遵循相同的**命名空间** (namespace)，比如 **font-family**, **font-size**, **font-weight** 都以 **font** 作为属性的命名空间。为了便于管理这样的属性，同时也为了避免了重复输入，Sass 允许将属性嵌套在命名空间中，例如：

```scss
.funky {
    font: {
      family: fantasy;
      size: 30em;
      weight: bold;
    }
}
```

编译为

```css
.funky {
  font-family: fantasy;
  font-size: 30em;
  font-weight: bold;
}
```

命名空间也可以包含自己的属性值，例如：

```scss
.funky {
    font: 20px/24px {
      family: fantasy;
      weight: bold;
    }
}
```

编译为

```css
.funky {
  font: 20px/24px;
  font-family: fantasy;
  font-weight: bold;
}
```

## SassScript

### 变量 $

变量用于存储一些信息，它可以重复使用。另外**变量可以存储字符串，数字，颜色值，布尔值，列表和null值**

SassScript 最普遍的用法就是变量，**变量以美元符号开头**，赋值方法与 CSS 属性的写法一样：**$width**: **5em**;直接使用即调用变量：

```scss
#main {
    width: $width;
}
```

**变量支持块级作用域**，嵌套规则内定义的变量只能在嵌套规则内使用（局部变量），不在嵌套规则内定义的变量则可在任何地方使用（全局变量）。将局部变量转换为全局变量可以添加 !global 声明：

```scss
#main {
    $width: 5em !global;
    width: $width;
}
#sidebar {
    width: $width;
}
```

编译为

```css
#main {
  width: 5em;
}
#sidebar {
  width: 5em;
}
```

注意：用中划线声明的变量可以使用下划线的方式引用

### 数据类型

SassScript 支持 6 种主要的数据类型：

- 数字，1, 2, 13, 10px
- 字符串，有引号字符串与无引号字符串，"foo", 'bar', baz
- 颜色，blue, #04a3f9, rgba(255,0,0,0.5)
- 布尔型，true, false
- 空值，null
- 数组 (list)，用空格或逗号作分隔符，1.5em 1em 0 2em, Helvetica, Arial, sans-serif
- maps, 相当于 JavaScript 的 object，(key1: value1, key2: value2)，Maps主要为sassscript函数服务

#### 字符串

SassScript 支持 CSS 的两种字符串类型：

​    有引号字符串 (quoted strings)，如 “Lucida Grande” ‘http://sass-lang.com’。

​    无引号字符串 (unquoted strings)，如 sans-serif bold。

​    在编译 CSS 文件时不会改变其类型。只有一种情况例外，使用 #{} (interpolation，插值运算符) 时，有引号字符串将被编译为无引号字符串，这样便于在混合指令 mixin 中引用选择器名，对于插值运算符#{}和混合指令mixin后面章节会讲到，先做了解。

```scss
@mixin firefox-message($selector) {
    body.firefox #{$selector}:before {
      content: "Hi, Firefox users!";
    }
}
@include firefox-message(".header");
```

编译为

```css
body.firefox .header:before {
  content: "Hi, Firefox users!";
}
```

#### 数组 (Lists)

数组 (lists) 指 Sass 如何处理 CSS 中 **margin: 10px 15px 0 0** 或者 **font-face: Helvetica, Arial, sans-serif** 这样通过空格或者逗号分隔的一系列的值。事实上，独立的值也被视为数组 —— 只包含一个值的数组。



数组中可以包含子数组，比如 **1px 2px, 5px 6px** 是包含 **1px 2px** 与 **5px 6px** 两个数组的数组。这个数组也可以使用括号分隔开，也可以写成 **(1px 2px) (5px 6px)**，在被编译成css时，sass会去掉这些括号。

#### 运算

所有数据类型均支持相等运算 **==** 或 **!=**，此外，每种数据类型也有其各自支持的运算方式。

- 数字运算

SassScript 支持数字的加减乘除、取整等运算 **(+, -, \*, /, %)**，如果必要会在不同单位间转换值。

```scss
$width:100px;
$height:40px;
p{
    width: $width;
    height: $height;
    line-height: $width - $height;
}
```

编译为

```css
p {
  width: 100px;
  height: 40px;
  line-height: 60px;
}
```

关系运算 <, >, <=, >= 也可用于数字运算，相等运算 ==, != 可用于所有数据类型。

- 除法运算 /

**/** 在 CSS 中通常起到分隔数字的用途，SassScript 作为 CSS 语言的拓展当然也支持这个功能，同时也赋予了 **/** 除法运算的功能。也就是说，如果 **/** 在 SassScript 中把两个数字分隔，编译后的 CSS 文件中也是同样的作用。

**以下三种情况** **/** **将被视为除法运算符号**：

1.如果值，或值的一部分，是变量或者函数的返回值

2.如果值被圆括号包裹

3.如果值是算数表达式的一部分

```scss
p {
    font: 10px/8px;             
    $width: 1000px;
    width: $width/2;            
    width: round(1.5)/2;        
    height: (500px/2);          
    margin-left: 5px + 8px/2px; 
}
```

编译为

```css
p {
  font: 10px/8px;
  width: 500px;
  width: 1;
  height: 250px;
  margin-left: 9px;
}
```

如果需要使用变量，同时又要确保 / 不做除法运算而是完整地编译到 CSS 文件中，只需要用 #{} 插值语句将变量包裹。

```scss
p {
    $font-size: 12px;
    $line-height: 30px;
    font: #{$font-size}/#{$line-height};
}
```

编译为

```css
p {
  font: 12px/30px;
}
```

#### 字符串运算

**+** 可用于连接字符串

```scss
p {
    cursor: e + -resize;
}
```

编译为

```css
p {
  cursor: e-resize;
}
```

注意，如果有引号字符串（位于 + 左侧）连接无引号字符串，运算结果是有引号的，相反，无引号字符串（位于 + 左侧）连接有引号字符串，运算结果则没有引号。

```scss
p:before {
    content: "Foo " + Bar;
    font-family: sans- + "serif";
}
```

编译为

```css
p:before {
  content: "Foo Bar";
  font-family: sans-serif;
}
```

运算表达式与其他值连用时，用空格做连接符：

```scss
p {
    margin: 3px + 4px auto;
}
```

编译为

```css
p {
  margin: 7px auto;
}
```

在有引号的文本字符串中使用 #{} 插值语句可以添加动态的值：

```scss
p:before {
    content: "I ate #{5 + 10} pies!";
}
```

编译为

```css
p:before {
  content: "I ate 15 pies!";
}
```

圆括号可以用来影响运算的顺序

#### 插值语句 #{}

通过 #{} 插值语句可以在选择器或属性名中使用变量：

```scss
$name: foo;
$attr: border;
p.#{$name} {
  #{$attr}-color: blue;
}
```

编译为

```css
p.foo {
  border-color: blue;
}
```

## @-Rules 与指令

### @import

Sass 拓展了 **@import** 的功能，允许其导入 SCSS 或 Sass 文件。被导入的文件将合并编译到同一个 CSS 文件中，另外，**被导入的文件中所包含的变量或者混合指令** **(mixin)** **都可以在导入的文件中使用**。

通常，@import 寻找 Sass 文件并将其导入，但在以下情况下，@import 仅作为普通的 CSS 语句，不会导入任何 Sass 文件。

1.文件名文件拓展名是 .css；

2.以 http:// 开头；

3.文件名是 url()；

4.@import 包含 media queries。

如果不在上述情况内，文件的拓展名是 .scss 或 .sass，则导入成功。没有指定拓展名，Sass 将会试着寻找文件名相同，拓展名为 .scss 或 .sass 的文件并将其导入。

```css
@import “foo.scss”; 或  @import "foo";
都会导入文件 foo.scss，但是
@import "foo.css";
@import "foo" screen;
@import "http://foo.com/bar";
@import url(foo);
编译为
@import "foo.css";
@import "foo" screen;
@import "http://foo.com/bar";
@import url(foo);
```

Sass **允许同时导入多个文件**，例如同时导入 rounded-corners 与 text-shadow 两个文件：

```scss
@import "rounded-corners", "text-shadow";
```



- 分音(Partials)

如果需要导入 SCSS 或者 Sass 文件，但又不希望将其编译为 CSS，只需要在文件名前添加下划线，这样会告诉 Sass 不要编译这些文件，但**导入语句中却不需要添加下划线**。

例如，将文件命名为 **_colors.scss**，便不会编译 **_colours.css** 文件。

```scss
@import "colors";
```

上面的例子，导入的其实是 **_colors.scss**文件

**注意：**不可以同时存在添加下划线与未添加下划线的同名文件，添加下划线的文件将会被忽略。比如，_colors.scss 和 colors.scss 不能同时存在于同一个目录下，否则带下划线的文件将会被忽略。

### @extend

在设计网页的时候常常遇到这种情况：一个元素使用的样式与另一个元素完全相同，但又添加了额外的样式。通常会在 HTML 中给元素定义两个 class，一个通用样式，一个特殊样式。假设现在要设计一个普通错误样式与一个严重错误样式，一般会这样写：

```html
<div class="error seriousError">
    Oh no! You've been hacked!
</div>
```

样式如下：

```css
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.seriousError {
  border-width: 3px;
}
```

麻烦的是，这样做必须时刻记住使用 **.seriousError** 时需要参考 **.error** 的样式，带来了很多不变：智能比如加重维护负担，导致 bug，或者给 HTML 添加无语意的样式。

使用 **@extend** 可以避免上述情况，告诉 Sass 将一个选择器下的所有样式继承给另一个选择器。

```scss
.error {
    border: 1px #f00;
    background-color: #fdd;
}
.seriousError {
    @extend .error;
    border-width: 3px;
}
```

编译为

```css
.error, .seriousError {
  border: 1px #f00;
  background-color: #fdd;
}
.seriousError {
  border-width: 3px;
}
```

上面代码的意思是将 **.error** 下的所有样式继承给 **.seriousError**，**border-width: 3px;** 是单独给 **.seriousError** 设定特殊样式，这样，使用 **.seriousError** 的地方可以不再使用 **.error**。

**@extend** 的作用是将重复使用的样式 (.error) 延伸 (extend) 给需要包含这个样式的特殊样式（.seriousError）

```scss
.error {
    border: 1px #f00;
    background-color: #fdd;
}
.error.intrusion {
    color: red;
}
.seriousError {
    @extend .error;
    border-width: 3px;
}
```

编译为

```css
.error, .seriousError {
  border: 1px #f00;
  background-color: #fdd;
}
.error.intrusion, .intrusion.seriousError {
  color: red;
}
.seriousError {
  border-width: 3px;
}
```

**@extend 很好的体现了代码的复用**。

## 控制指令

### @if

当 **@if** 的表达式返回值不是 false 或者 null 时，条件成立，输出 {} 内的代码：

```scss
p {
    @if 1 + 1 == 2 { border: 1px solid; }
    @if 5 < 3 { border: 2px dotted; }
    @if null  { border: 3px double; }
}
```

编译为

```css
p {
  border: 1px solid;
}
```

**@if** 声明后面可以跟多个 **@else if** 声明，或者一个 **@else** 声明。如果 **@if** 声明失败，Sass 将逐条执行 **@else if** 声明，如果全部失败，最后执行 **@else** 声明，例如：

```scss
$type: monster;
p {
  @if $type == ocean {color: blue;
  } @else if $type == matador {color: red;
  } @else if $type == monster {color: green;
  } @else {color: black;
  }
}
```

### @for

   **@for** 指令可以在限制的范围内重复输出格式，每次按要求（变量的值）对输出结果做出变动。

   这个指令包含两种格式：

```scss
@for $var from <start> through <end>，或者 @for $var from <start> to <end>
```

   两种格式的区别在于 **through** 与 **to** 的含义：当使用 **through** 时，条件范围**包含**  <start>与 <end> 的值，而使用 **to** 时条件范围**只包含**<start> 的值**不包含** <end> 的值。

-    **$var** 可以是任何变量，比如 **$i**；
-   <start>**和**  <end>**必须是整数值**。

**语法：**

```scss
@for  $var  from  <开始值(包含)>  through  <结束值(包含)> {
      …
}

或

@for  $var  from  <开始值(包含)>  to  <结束值(不包含)> {
      …
}
```

实列：

```scss
@for $i from 1 through 3 {
    .item-#{$i} { width: 2em * $i; }
}
```

编译为

```css
.item-1 {
  width: 2em;
}
.item-2 {
  width: 4em;
}
.item-3 {
  width: 6em;
}
```

### @each

**@each** 指令的格式是 **$var in <list> , $var** 可以是任何变量名，比如 **$length** 或者 **$name**，而 <list> 是一连串的值，也就是值列表。语法：

```
@each $var in $list {

}
```

**@each** 将变量 **$var** 作用于值列表中的每一个项目，然后输出结果，例如：

```scss
@each $s in sm, lg, xs, md{
    .#{$s}{
      width:100px;
    }
}
```

编译为

```css
.sm {
  width: 100px;
}
  .lg {
  width: 100px;
}
  .xs {
  width: 100px;
}
.md {
  width: 100px;
}
```

Layui的栅格系统 只定义宽度 .col-sm-

```scss
@each $w in xs, sm, md, lg{
    @for $i from 1 through 12{
      .col-#{$w}-#{$i}{
        width: percentage($i/12);
      }
    }
}
```

**@each**指令还可以使用多个变量，例如**@each**中的**$ var1，$ var2，...**中。 如果是列表，则子列表的每个元素都分配给相应的变量。 例如：

```scss
@each $s, $color, $cursor in      (item1, black, default),
                                  (item2, blue, pointer),
                                  (item3, white, move) {
  .#{$s}-icon {
    border: 2px solid $color;
    cursor: $cursor;
  }
}
```

编译为

```css
.item1-icon {
  border: 2px solid black;
  cursor: default;
}
.item2-icon {
  border: 2px solid blue;
  cursor: pointer;
}
.item3-icon {
  border: 2px solid white;
  cursor: move;
}
```

### @while

**@while** 指令重复输出格式直到表达式返回结果为 false。这样可以实现比 @for 更复杂的循环，只是很少会用到。例如：

```scss
$i: 6;
@while $i > 0 {
  .item-#{$i} { width: 2em * $i; }
  $i: $i - 2;
}
```

编译为

```css
.item-6 {
  width: 12em;
}
.item-4 {
  width: 8em;
}
.item-2 {
  width: 4em;
}
```

## 混合指令

### 定义混合指令 @mixin

混合指令的用法是在 **@mixin** 后添加名称与样式，比如名为 **large-text** 的混合通过下面的代码定义：

```scss
@mixin large-text {
    font: {
      family: Arial;
      size: 20px;
      weight: bold;
    }
    color: #ff0000;
}
```

混合也需要包含选择器和属性，甚至可以用 & 引用父选择器：

```scss
@mixin clearfix {
    display: inline-block;
    &:after {
      content: ".";
      display: block;
      height: 0;
      clear: both;
      visibility: hidden;
    }
    * html & { height: 1px }
}
```

### 引用混合样式 @include

使用 **@include** 指令引用混合样式，格式是在其后添加混合名称，以及需要的参数（可选）：

```scss
.page-title {
    @include large-text;
    padding: 4px;
    margin-top: 10px;
}
```

编译为

```css
.page-title {
  font-family: Arial;
  font-size: 20px;
  font-weight: bold;
  color: #ff0000;
  padding: 4px;
  margin-top: 10px;
}
```

也可以在最外层引用混合样式，不会直接定义属性，也不可以使用父选择器。

```scss
@mixin silly-links {
    a {
      color: blue;
      background-color: red;
    }
  }
@include silly-links;
```

编译为

```css
a {
  color: blue;
  background-color: red;
}
```

### @mixin里面的参数

参数用于给混合指令中的样式设定变量，并且赋值使用。在定义混合指令的时候，按照变量的格式，通过逗号分隔，将参数写进圆括号里。引用指令时，按照参数的顺序，再将所赋的值对应写进括号：

```scss
@mixin sexy-border($color, $width) {
    border: {
      color: $color;
      width: $width;
      style: dashed;
    }
}
p { 
	@include sexy-border(blue, 10px); 
}
```

- **关键词参数**

混合指令也可以使用关键词参数，之前的例子也可以写成：

```scss
@mixin sexy-border($color, $width) {
    border: {
      color: $color;
      width: $width;
      style: dashed;
    }
}
p { 
@include sexy-border($width:10px,$color: blue); 
}
h1 { 
@include sexy-border($color: blue, $width: 5px); 
}
```

编译为

```css
p {
  border-color: blue;
  border-width: 10px;
  border-style: dashed;
}
h1 {
  border-color: blue;
  border-width: 5px;
  border-style: dashed;
}
```



