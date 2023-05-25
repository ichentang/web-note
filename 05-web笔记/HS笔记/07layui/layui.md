## layui简介

​	layui（谐音：类UI) 是一款采用自身模块规范编写的前端 UI 框架，遵循原生 HTML/CSS/JS 的书写与组织形式，门槛极低，拿来即用。其外在极简，却又不失饱满的内在，体积轻盈，组件丰盈，从核心代码到 API 的每一处细节都经过精心雕琢，非常适合界面的快速开发。

​	layui 首个版本发布于 2016 年金秋，她区别于那些基于 MVVM 底层的 UI 框架，却并非逆道而行，而是信奉返璞归真之道。准确地说，她更多是为后端程序员量身定做，你无需涉足各种前端工具的复杂配置，只需面对浏览器本身，让一切你所需要的元素与交互，从这里信手拈来。

## 快速上手

官网首页下载

https://www.layui.com/

快速上手

获得 layui 后，将其完整地部署到你的项目目录（或静态资源服务器），你只需要引入下述两个文件：

```html
./layui/css/layui.css
./layui/layui.js
```

基本的入门页面：

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
  <title>开始使用layui</title>
  <link rel="stylesheet" href="./layui/css/layui.css">
</head>
<body>
 
<!-- 你的HTML代码 -->
 
<script src="./layui/layui.js"></script>
<script>
//一般直接写在一个js文件中
layui.use(['layer', 'form'], function(){
  var layer = layui.layer
  ,form = layui.form;
  
  layer.msg('Hello World');
});
</script> 
</body>
</html>
```

## 栅格系统

栅格布局规则：

------

| 1.   | 采用 *layui-row* 来定义行，如：<div class="layui-row"></div> |
| ---- | ------------------------------------------------------------ |
| 2.   | 采用类似 *layui-col-md** 这样的预设类来定义一组列（column），且放在行（row）内。其中：变量*md* 代表的是不同屏幕下的标记（可选值见下文）变量*** 代表的是该列所占用的12等分数（如6/12），可选值为 1 - 12如果多个列的“等分数值”总和等于12，则刚好满行排列。如果大于12，多余的列将自动另起一行。 |
| 3.   | 列可以同时出现最多四种不同的组合，分别是：*xs*（超小屏幕，如手机）、*sm*（小屏幕，如平板）、*md*（桌面中等屏幕）、*lg*（桌面大型屏幕），以呈现更加动态灵活的布局。 |
| 4.   | 可对列追加类似 *layui-col-space5*、 *layui-col-md-offset3* 这样的预设类来定义列的间距和偏移。 |
| 5.   | 最后，在列（column）元素中放入你自己的任意元素填充内容，完成布局！ |

```html
<div class="layui-container">  
  常规布局（以中型屏幕桌面为例）：
  <div class="layui-row">
    <div class="layui-col-md9">
      你的内容 9/12
    </div>
    <div class="layui-col-md3">
      你的内容 3/12
    </div>
  </div>
   
  移动设备、平板、桌面端的不同表现：
  <div class="layui-row">
    <div class="layui-col-xs6 layui-col-sm6 layui-col-md4">
      移动：6/12 | 平板：6/12 | 桌面：4/12
    </div>
    <div class="layui-col-xs6 layui-col-sm6 layui-col-md4">
      移动：6/12 | 平板：6/12 | 桌面：4/12
    </div>
    <div class="layui-col-xs4 layui-col-sm12 layui-col-md4">
      移动：4/12 | 平板：12/12 | 桌面：4/12
    </div>
    <div class="layui-col-xs4 layui-col-sm7 layui-col-md8">
      移动：4/12 | 平板：7/12 | 桌面：8/12
    </div>
    <div class="layui-col-xs4 layui-col-sm5 layui-col-md4">
      移动：4/12 | 平板：5/12 | 桌面：4/12
    </div>
  </div>
</div>
```

响应式规则：

------

栅格的响应式能力，得益于CSS3媒体查询（Media Queries）的强力支持，从而针对四类不同尺寸的屏幕，进行相应的适配处理

|                             | 超小屏幕 (手机<768px)    | 小屏幕 (平板≥768px)                                    | 中等屏幕 (桌面≥992px) | 大型屏幕 (桌面≥1200px) |
| :-------------------------- | :----------------------- | :----------------------------------------------------- | :-------------------- | :--------------------- |
| *.layui-container*的值      | auto                     | 750px                                                  | 970px                 | 1170px                 |
| 标记                        | xs                       | sm                                                     | md                    | lg                     |
| 列对应类 * 为1-12的等分数值 | layui-col-xs*            | layui-col-sm*                                          | layui-col-md*         | layui-col-lg*          |
| 总列数                      | 12                       |                                                        |                       |                        |
| 响应行为                    | 始终按设定的比例水平排列 | 在当前屏幕下水平排列，如果屏幕大小低于临界值则堆叠排列 |                       |                        |

响应式公共类：

------

| 类名（class）             | 说明                                                        |
| :------------------------ | :---------------------------------------------------------- |
| layui-show-*-block        | 定义不同设备下的 display: block; * 可选值有：xs、sm、md、lg |
| layui-show-*-inline       | 定义不同设备下的 display: inline; * 可选值同上              |
| layui-show-*-inline-block | 定义不同设备下的 display: inline-block; * 可选值同上        |
| layui-hide-*              | 定义不同设备下的隐藏类，即： display: none; * 可选值同上    |

布局容器：

------

将栅格放入一个带有 *class="layui-container"* 的特定的容器中，以便在小屏幕以上的设备中固定宽度，让列可控。

```html
<div class="layui-container">
  <div class="layui-row">
    ……
  </div>
</div>            
```

当然，你还可以不固定容器宽度。将栅格或其它元素放入一个带有 *class="layui-fluid"* 的容器中，那么宽度将不会固定，而是 100% 适应

```html
<div class="layui-fluid">
  ……
</div>    
```

## 字体图标

layui 的所有图标全部采用字体形式，取材于阿里巴巴矢量图标库（iconfont）。因此你可以把一个 icon 看作是一个普通的文字，这意味着你直接用 css 控制文字属性，如 color、font-size，就可以改变图标的颜色和大小。你可以通过 *font-class* 或 *unicode* 来定义不同的图标。

```html
<i class="layui-icon layui-icon-face-smile" style="font-size: 30px; color: #1E9FFF;"></i>  
```



## 表格

表格的常规用法

```html
<table class="layui-table">
  <colgroup>
    <col width="150">
    <col width="200">
    <col>
  </colgroup>
  <thead>
    <tr>
      <th>昵称</th>
      <th>加入时间</th>
      <th>签名</th>
    </tr> 
  </thead>
  <tbody>
    <tr>
      <td>贤心</td>
      <td>2016-11-29</td>
      <td>人生就像是一场修行</td>
    </tr>
    <tr>
      <td>许闲心</td>
      <td>2016-11-28</td>
      <td>于千万人之中遇见你所遇见的人，于千万年之中，时间的无涯的荒野里…</td>
    </tr>
  </tbody>
</table>
```



## 按钮

向任意HTML元素设定*class="layui-btn"*，建立一个基础按钮。通过追加格式为*layui-btn-{type}*的class来定义其它按钮风格。内置的按钮class可以进行任意组合，从而形成更多种按钮风格。

```html
<button type="button" class="layui-btn">一个标准的按钮</button>
<a href="http://www.layui.com" class="layui-btn">一个可跳转的按钮</a>
```



## 表单

在一个容器中设定 *class="layui-form"* 来标识一个表单元素块，通过规范好的HTML结构及CSS类，来组装成各式各样的表单元素，并通过内置的 *form模块* 来完成各种交互。

```html
<form class="layui-form" action="">
  <div class="layui-form-item">
    <label class="layui-form-label">输入框</label>
    <div class="layui-input-block">
      <input type="text" name="title" required  lay-verify="required" placeholder="请输入标题" autocomplete="off" class="layui-input">
    </div>
  </div>
  <div class="layui-form-item">
    <label class="layui-form-label">密码框</label>
    <div class="layui-input-inline">
      <input type="password" name="password" required lay-verify="required" placeholder="请输入密码" autocomplete="off" class="layui-input">
    </div>
    <div class="layui-form-mid layui-word-aux">辅助文字</div>
  </div>
  <div class="layui-form-item">
    <label class="layui-form-label">选择框</label>
    <div class="layui-input-block">
      <select name="city" lay-verify="required">
        <option value=""></option>
        <option value="0">北京</option>
        <option value="1">上海</option>
        <option value="2">广州</option>
        <option value="3">深圳</option>
        <option value="4">杭州</option>
      </select>
    </div>
  </div>
  <div class="layui-form-item">
    <label class="layui-form-label">复选框</label>
    <div class="layui-input-block">
      <input type="checkbox" name="like[write]" title="写作">
      <input type="checkbox" name="like[read]" title="阅读" checked>
      <input type="checkbox" name="like[dai]" title="发呆">
    </div>
  </div>
  <div class="layui-form-item">
    <label class="layui-form-label">开关</label>
    <div class="layui-input-block">
      <input type="checkbox" name="switch" lay-skin="switch">
    </div>
  </div>
  <div class="layui-form-item">
    <label class="layui-form-label">单选框</label>
    <div class="layui-input-block">
      <input type="radio" name="sex" value="男" title="男">
      <input type="radio" name="sex" value="女" title="女" checked>
    </div>
  </div>
  <div class="layui-form-item layui-form-text">
    <label class="layui-form-label">文本域</label>
    <div class="layui-input-block">
      <textarea name="desc" placeholder="请输入内容" class="layui-textarea"></textarea>
    </div>
  </div>
  <div class="layui-form-item">
    <div class="layui-input-block">
      <button class="layui-btn" lay-submit lay-filter="formDemo">立即提交</button>
      <button type="reset" class="layui-btn layui-btn-primary">重置</button>
    </div>
  </div>
</form>
 
<script>
//Demo
layui.use('form', function(){
  var form = layui.form;
  
  //监听提交
  form.on('submit(formDemo)', function(data){
    layer.msg(JSON.stringify(data.field));
    return false;
  });
});
</script>
```



## 后台布局

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
  <title>layout 后台大布局 - Layui</title>
  <link rel="stylesheet" href="../src/css/layui.css">
</head>
<body class="layui-layout-body">
<div class="layui-layout layui-layout-admin">
  <div class="layui-header">
    <div class="layui-logo">layui 后台布局</div>
    <!-- 头部区域（可配合layui已有的水平导航） -->
    <ul class="layui-nav layui-layout-left">
      <li class="layui-nav-item"><a href="">控制台</a></li>
      <li class="layui-nav-item"><a href="">商品管理</a></li>
      <li class="layui-nav-item"><a href="">用户</a></li>
      <li class="layui-nav-item">
        <a href="javascript:;">其它系统</a>
        <dl class="layui-nav-child">
          <dd><a href="">邮件管理</a></dd>
          <dd><a href="">消息管理</a></dd>
          <dd><a href="">授权管理</a></dd>
        </dl>
      </li>
    </ul>
    <ul class="layui-nav layui-layout-right">
      <li class="layui-nav-item">
        <a href="javascript:;">
          <img src="http://t.cn/RCzsdCq" class="layui-nav-img">
          贤心
        </a>
        <dl class="layui-nav-child">
          <dd><a href="">基本资料</a></dd>
          <dd><a href="">安全设置</a></dd>
        </dl>
      </li>
      <li class="layui-nav-item"><a href="">退了</a></li>
    </ul>
  </div>
  
  <div class="layui-side layui-bg-black">
    <div class="layui-side-scroll">
      <!-- 左侧导航区域（可配合layui已有的垂直导航） -->
      <ul class="layui-nav layui-nav-tree"  lay-filter="test">
        <li class="layui-nav-item layui-nav-itemed">
          <a class="" href="javascript:;">所有商品</a>
          <dl class="layui-nav-child">
            <dd><a href="javascript:;">列表一</a></dd>
            <dd><a href="javascript:;">列表二</a></dd>
            <dd><a href="javascript:;">列表三</a></dd>
            <dd><a href="">超链接</a></dd>
          </dl>
        </li>
        <li class="layui-nav-item">
          <a href="javascript:;">解决方案</a>
          <dl class="layui-nav-child">
            <dd><a href="javascript:;">列表一</a></dd>
            <dd><a href="javascript:;">列表二</a></dd>
            <dd><a href="">超链接</a></dd>
          </dl>
        </li>
        <li class="layui-nav-item"><a href="">云市场</a></li>
        <li class="layui-nav-item"><a href="">发布商品</a></li>
      </ul>
    </div>
  </div>
  
  <div class="layui-body">
    <!-- 内容主体区域 -->
    <div style="padding: 15px;">内容主体区域</div>
  </div>
  
  <div class="layui-footer">
    <!-- 底部固定区域 -->
    © layui.com - 底部固定区域
  </div>
</div>
<script src="../src/layui.js"></script>
<script>
//JavaScript代码区域
layui.use('element', function(){
  var element = layui.element;
  
});
</script>
</body>
</html>
```









