1. 原型和原型链

2. 作用域相关， 

闭包

​	闭包让开发者在内部函数可以访问外部函数的作用域，闭包会随着函数创建被同时创建。

应用场景：自执行函数、函数柯里化、链式调用、$message

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

​		web -> native传值：



















