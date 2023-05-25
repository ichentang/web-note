# 一、Node.js在前端工程化和后端服务应用的区别

![image-20230514143623569](Node%E5%BA%94%E7%94%A8%E5%AE%9E%E8%B7%B5%E5%BC%80%E5%8F%91.assets/image-20230514143623569.png)

运行环境：

- 工程化的大部分情况都是基于当前开发环境，运行在本地开发机器上
- 后端服务应用一般运行在远程服务器上，需要利用一些工具分析判断或者监控运行情况
- 运行在本地的服务，可以快速地判断、定位、分析、解决问题

# 二、Node.js事件循环原理

![image-20230514150220948](Node%E5%BA%94%E7%94%A8%E5%AE%9E%E8%B7%B5%E5%BC%80%E5%8F%91.assets/image-20230514150220948.png)

（1）timers：本阶段执行已经被本阶段执行已经被 setTimeout() 和 setInterval() 调度的回调函数，简单理解就是由这两个函数启动的回调函数。

（2）pending callbacks：本阶段执行某些系统操作（如 TCP 错误类型）的回调函数。

（3）idle、prepare：仅系统内部使用，只需要知道有这 2 个阶段就可以。

（4）poll：检索新的 I/O 事件，执行与 I/O 相关的回调，其他情况 Node.js 将在适当的时候在此阻塞。这也是最复杂的一个阶段，所有的事件循环以及回调处理都在这个阶段执行，接下来会详细分析这个过程。

（5）check：setImmediate() 回调函数在这里执行，setImmediate 并不是立马执行，而是当事件循环 poll 中没有新的事件处理时就执行该部分，如下代码所示：

```js
const fs = require('fs');
setTimeout(()=>{ // 新的事件循环的起点
  console.log('1')
},0);

setImmediate( () => {
    console.log('setImmediate 1');
});

/// 将会在 poll 阶段执行
fs.readFile('./test.conf', {encoding: 'utf-8'}, (err, data) => {
    if (err) throw err;
    console.log('read file success');
});

/// 该部分将会在首次事件循环中执行
Promise.resolve().then(()=>{
    console.log('poll callback');
});

// 首次事件循环执行
console.log('2');

注意：
>setTimeout 如果不设置时间或者设置时间为 0，则会默认为 1ms；
>主流程执行完成后，超过 1ms 时，会将 setTimeout 回调函数逻辑插入到待执行回调函数poll 队列中；
>由于当前 poll 队列中存在可执行回调函数，因此需要先执行完，待完全执行完成后，才会执行check：setImmediate。
```

（6）close callbacks：执行一些关闭的回调函数，如 socket.on('close', ...)。

## 1、Node.js事件循环

![image-20230514151256126](Node%E5%BA%94%E7%94%A8%E5%AE%9E%E8%B7%B5%E5%BC%80%E5%8F%91.assets/image-20230514151256126.png)

​                                                    `图 2 事件循环过程`

**微任务：**在 Node.js 中微任务包含 2 种——process.nextTick 和 Promise。微任务在事件循环中优先级是最高的，因此在同一个事件循环中有其他任务存在时，优先执行微任务队列。并且process.nextTick 和 Promise 也存在优先级，process.nextTick 高于 Promise。

**宏任务：**在 Node.js 中宏任务包含 4 种——setTimeout、setInterval、setImmediate 和 I/O。宏任务在微任务执行之后执行，因此在同一个事件循环周期内，如果既存在微任务队列又存在宏任务队列，那么优先将微任务队列清空，再执行宏任务队列。事件循环中的事件类型是存在优先级。

在图 2 的左侧，我们可以看到有一个核心的主线程，它的执行阶段主要处理三个核心逻辑。

- 
  同步代码。

- 
  将异步任务插入到微任务队列或者宏任务队列中。

- 
  执行微任务或者宏任务的回调函数。在主线程处理回调函数的同时，也需要判断是否插入微任务和宏任务。根据优先级，先判断微任务队列是否存在任务，存在则先执行微任务，不存在则判断在宏任务队列是否有任务，有则执行。



































































































































































































