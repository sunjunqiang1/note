1. 原型和原型链


2. 作用域相关， 

闭包

​	闭包让开发者在内部函数可以访问外部函数的作用域，闭包会随着函数创建被同时创建。

应用场景：自执行函数、函数柯里化、链式调用、$message、防抖、节流

3. 防抖和节流

4. 移动端适配方案
   1.  使用rem布局
   2. 使用vw 和 vh布局
   3. 响应式布局
   4. 百分比；
   5. vw 和 vh 结合 px 布局。
5. 移动端1px问题

​	移动端的1px问题是由于设备的devicePixelRatio的不同引起的， 在移动设备中由于设备DPR的不同， 1px在设备上显示的大小也不相同。具体1px在设备上表示多少物理像素可以使用window.devicePiexRatio查看。

​	为了让1px在移动端设备上表现相同， 需要设置viewport中的initial-scale 来进行控制

6. h5 与 jsBridge 通信的原理

​	jsBridge使用：

​		native -> web传值： 通过webVIew执行一个javascript定义好的全局函数， 并且将需要传的数据当作参数传递进去

​		web -> native传值：1. url-schema利用iframe的src属性， nav对请求进行拦截，调用原生的方法；2.向webview中注入js API， 在web端调用注入的方法

7. 事件循环

​	浏览器的事件循环：浏览器将异步任务分为宏任务和微任务，当宏任务具备执行条件的时候它会被放入宏任务队列当中， 微任务具备执行条件的时候被放入微任务队列当中。 当主线程空闲的时候，会先查看微任务队列是否有需要执行的任务， 如果有那么将其放到主线程执行，否则查看宏任务队列。

​	nodejs端的事件循环：nodejs分为六个阶段来处理异步任务， 执行中的nodejs进程在这六个阶段中循环。分别是：timers：执行定时器回调；IO/Callback:执行io的回调；Idel prepare阶段在这个阶段执行一些nodejs内部任务；poll阶段，获取异步IO；check阶段执行setImmediate回调；close执行关闭的回调比如socket.close导致的回调。

​	在nodejs当中promise 和 process.nextTick被视为微任务， 每当一个事件循环阶段完成之后， 他回去检查这个队列， 并执行队列中的任务。

8. commonjs 和 es module 的区别

   	1. 两者的导入导出方式不同，commonjs使用module.export 和 require导出和导入，而es module 使用 export 和 import 导出和导入
   	
   	1. commonjs 是动态引入的， 不必要在代码的顶部引入， 而 import是静态的， 必须在代码的顶部引入；
   	
   	1. commonjs 是在运行时加载模块，而esmodule是在编译时加载模块，commonjs 导入是对值的引用， 可以修改， 而 import 引入是只读的；
   	
   	1. commonjs 是单值导出，  es module 可以多值导出。

9. promise所有的方法
   1. then
   2. catch
   3. finally
   4. all：当所有promise成功，返回全部的值，有一个失败，执行reject
   5. race：返回promise第一个成功的值
   6. allSettled：返回所有的peomise结果，并带有成功和失败的状态
   7. any：返回第一个成功的promise的值
   8. resolve
   9. reject

10. async await和promise的关系

1. async 函数直接调用在没有await的时候， 返回一个promise

2. await 后面可以跟promise函数

3. async 和 await和promise一样都是非阻塞的；

4. async 和 await 可以说是一个改良版的promise

esnext新增了哪些特性

​	2016： includes , 幂运算符

​	2017：padStart, padEnd 前填充和后填充字符串， includes 

​	2018：对象的解构赋值，对象新增了获取其描述信息的方法，promise新增finally方法

​	2019：try/catch 允许增加参数，增加Symbol.description，object.fromEntries() 将键值对转为新的对象，字符串新增trimStart 和 trimEnd方法，字符串新增了matchAll方法

​	2020：新增BigInt数据类型，Promise.allSettled方法，增加globalThis全局变量，新增可选链，新增空值合并运算符

​	2021：数字可以增加下划线连接、增加了 &&=,||=,??=

​	2022:top level awalt、字符串新增.at方法返回给定下标的字符串

​	2023：数组新增findLast、at方法

问题

优点、缺点

浏览器缓存

强缓存

expires： http1.0 值为资源的过期时间， 如果服务器和客户端时间不一样则会有问题

cache-control：使用max-age来设置资源的过期时间， 单位为秒。资源缓存策略：

​	public：所有内容都将被缓存（客户端和服务器代理）

​	private：只有客户端缓存

​	no-cache：不使用强制缓存， 但使用协商缓存

​	no-store：不使用强制缓存也不使用协商缓存

协商缓存

​	Last-Modified：资源的最后修改时间

​	Etag：当前资源的唯一标识（由服务器生成）

​	If-Modified-Since：对应Last-Modified，服务器通过该时间判断资源是否有效

​	If-None-Match：资源唯一标识，判断该资源是否有效





















