---
typora-root-url: static
---

## 一、redux

1、redux是一个js容器，用于进行全局的状态管理

2、redux三大核心

1）单一数据源头

2）State是只读的

3）使用纯函数执行修改（保证复用性）

## 二、redux的组成

1 State-状态
就是我们传递的数据，那么我们在用React开发项目的时候，大致可以把State分为三类：

·DomainDate:可以理解成为服务器端的数据，比如:获取用户的信息，商品的列表等等。

·UI State:决定当前UI决定展示的状态，比如:弹框的显示隐藏，受控组件等等

·App State:App级别的状态，比如:当前是否请求loading，当前路由信息等可能被多个和组件去使用的到的状态

2 Action特点:
Action的本质就是一个javaScript的普通对象
Action对象内部必须要有一个type属性来表示要执行的动作·多数情况下，这个type会被定义成字符串常量
除了type字段之外，action的结构随意进行定义
而我们在项目中，更多的喜欢用action创建函数（就是创建action的地方)

只是描述了有事情要发生，并没有描述如何去更新state

3 Reducer
Reducer本质就是一个函数，它用来响应发送过来的 actions，然后经过处理，把state 发送给Store的注意:在Reducer函数中，需要return返回值，这样Store才能接收到数据
函数会接收两个参数，第一个参数是初始化 state，第二个参数是action

4 Store
Store就是把action 与 reducer联系到一起的对象主要职责:
维持应用的state
提供getState()方法获取state

提供dispatch()方法发送action

通过subscribe()来注册监听
通过subscribe()返回值来注销监听

![](/../redux.assets/redux1.png)









































