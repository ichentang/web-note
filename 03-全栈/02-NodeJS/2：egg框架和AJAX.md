#### nodejs
##### 1、egg框架使用
1.1 创建项目
```js
mkdir 项目名称; 也可以手动创建
```
1.2 进入项目目录
```js
cd 项目名称
```
1.3 初始化项目
```js
npm init egg --type=simple
```
1.4 安装egg框架
```js
npm i egg
```
1.5 启动项目
```js
npm run dev
在 http://localhost:7001 打开项目
```
###### 2 egg的目录结构

```js
app 文件夹是主要的文件夹
config 为主要配置文件和插件配置的文件夹
logs 文件夹是日志文件夹，一般不用
node_modules 模块安装文件夹
package.json 当前项目的依赖，以及启动设置
```
###### 3 egg的约定规范

```js
E:\Web-1课程\Nodejs\Nodejs_2\day8\egg-example
├─package-lock.json
├─package.json
├─README.md
├─typings
|    
├─test
├─run
├─node_modules
├─logs
|   └test
| 
├─config
|   ├─config.default.js
|   └plugin.js
|
├─app
|  ├─router.js ---> 路由写在app下的router.js中
|  ├─view ---> 模版写在app文件下的view文件夹中
|  ├─service ---> 查询数据，获取数据写在app文件下的service中
|  ├─public ---> 静态文件放在public（css、image）
|  |   ├─images
|  |   ├─css
|  |
|  ├─middleware ---> 判断权限放在app文件下的middleware文件中
|  ├─extend ---> 拓展功能写在app文件下的extend文件夹中
|  ├─controller ---> 业务逻辑写在controller里
|       └home.js
```
#### AJAX
AJAX不是新的技术，是技术的组合；Async Javascript And Xml;
前后端在进行数据交互的时候，==一定（夸张==）用JSON格式；
###### AJAX的好处：
1. 实现页面局部刷新；
1. 减少HTTP请求，减轻服务器压力；
1. 提升用户体验；

AJAX的实现，不需要任何第三方插件，所有的浏览器默认支持-XMLHttpRequest；

###### XHR的状态值：


```js
<button>点击发送请求</button>
    <div id="result"></div>
    <script>
        //1
        const btn = document.getElementsByTagName('button')[0];
        const result = document.getElementById('result');
        //2
        btn.onclick = function () {
            //1 创建XMLHttpRequest对象
            const xhr = new XMLHttpRequest();
            //2 初始化
            xhr.open('GET', 'http://localhost:8000/server?a=100&b=200&c=300');
            //3 发送
            xhr.send();// send('method',url,async)
            method:请求方式
            url: 请求地址
            async: ture/false （默认）true:异步 false:同步
            //4 事件绑定
            //on when 当...时候
            //readystate 是xhr 对象中的属性：
            //0开头 表示未初始化 
            //1开头 表示open方法调用完毕
            //2开头 表示send方法调用完毕
            //3开头 表示服务端返回部分结果
            //4开头 表示服务端返回所有结果

            //5 处理服务端返回结果
            xhr.onreadystatechange = function () {
                //判断（服务端返回了所有结果）
                if (xhr.readyState === 4) {
                    //判断状态码200 404 403 401 500
                    //2xx 成功  2开头的都表示成功
                    if (xhr.status >= 200 && xhr.status < 300) {
                        //处理结果 行 头 空行 体
                        //响应行
                        console.log(xhr.status); //状态码
                        console.log(xhr.statusText); //状态字符串
                        console.log(xhr.getAllResponseHeaders()); //所有响应头
                        console.log(xhr.response); //响应体
                        //设置 result 文本
                        result.innerHTML = xhr.response;
                    } else { }
                }
            }
        }
    </script>
```
###### 常见的属性和方法:




#### 同源策略
同源策略是一种约定和规范好的客户端的安全策略，是浏览器最核心最基本的安全保障。同源政策的目的，是为了保证用户信息的安全，防止恶意的网站窃取数据。
**要求：**
1.	协议相同；
2.	域名相同：当做字符串来对比；
3.	端口相同；
只要其中任意一个没有满足，就是跨域了；
http://localhost:81
http://127.0.0.1:81
http://lulaoshi:81
http://192.168.2.64:81

其中任意2个都是非同源的；

**同源策略的限制范围**：服务器端的动态的数据：
1.	Cookie、localStorage、sessionStorage。
2.	AJAX

**不受同源策略限制的示例**：静态资源，你不让用，我就下载下来用，就没有意义了，所以不受同源限制

```js
1.	<script src=“...”></script>；
2.	<link rel=“stylesheet” href=“...”>；
3.	<img>、<video>、<audio>；
4.	@font-face 引入的字体；
```
##### 跨域处理
###### 1. JSONP：JSON with Padding
a)	**原理**：script标签不受同源的限制；
b)	**特征**：
i.	兼容性特别好，不需要任何配置；
ii.	非常的轻便高效；
iii.只能获取(GET)数据，不能提交(POST)数据，比如登录用不了；
c)**服务器端JSONP的实现：**
**egg**框架中提供了便捷的响应 JSONP 格式数据的方法，封装了 JSONP XSS 相关的安全防范，并支持进行 CSRF 校验和 referrer 校验。

(1)通过 app.jsonp() 提供的中间件来让一个 controller 支持响应 JSONP 格式的数据。在路由中，我们给需要支持 jsonp 的路由加上这个中间件：

```js
// app/router.js
module.exports = (app) => {
  const jsonp = app.jsonp();
  app.router.get('/api/posts/:id', jsonp, app.controller.posts.show);
  app.router.get('/api/posts', jsonp, app.controller.posts.list);
};
```
(2)在 Controller 中，只需要正常编写即可：

(3)用户请求对应的 URL 访问到这个 controller 的时候，如果 query 中有 _callback=fn 参数，将会返回 JSONP 格式的数据，否则返回 JSON 格式的数据。

egg官网JSONP：https://www.eggjs.org/zh-CN/basics/controller#jsonp
###### 2.	CORS：
跨域资源共享(CORS)是一种机制，是W3C标准。它允许浏览器向跨源服务器，发出XMLHttpRequest或Fetch请求。并且整个CORS通信过程都是浏览器自动完成的，不需要用户参与而使用这种跨域资源共享的前提是，浏览器必须支持这个功能，并且服务器端也必须同意这种"跨域"请求。因此实现CORS的关键是服务器。通常是有以下几个配置：


```
Access-Control-Allow-Origin
Access-Control-Allow-Methods
Access-Control-Allow-Headers
Access-Control-Allow-Credentials
Access-Control-Max-Age
```

**过程分析：**
浏览器先根据同源策略对前端页面和后台交互地址做匹配，若同源，则直接发送数据请求；若不同源，则发送跨域请求。
当我们发起跨域请求时，如果是非简单请求，浏览器会帮我们自动触发预检请求，也就是 OPTIONS 请求，用于确认目标资源是否支持跨域。如果是简单请求，则不会触发预检，直接发出正常请求。
服务器收到浏览器跨域请求后，根据自身配置返回对应文件头。若未配置过任何允许跨域，则文件头里不包含 Access-Control-Allow-origin 字段，若配置过域名，则返回 Access-Control-Allow-origin + 对应配置规则里的域名的方式。
https://blog.csdn.net/weixin_34414650/article/details/91468076?ops_request_misc=&request_id=&biz_id=102&utm_term=cors%E8%B7%A8%E5%9F%9F%E5%8E%9F%E7%90%86&utm_medium=distribute.pc_search_result.none-task-blog-2

3.	Proxy：
代理
无感
- 向自己的服务器发起请求--是同源的
- 自己的服务器把请求转发给目标服务器
- 目标服务器把处理结果返回给自己的服务器
- 自己的服务器再把接收到数据响应到前端





