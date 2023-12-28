1. $nextTick原理

   ​	nextTick即下一个滴答，也就是下一个周期，， 我们都知道浏览器的主线程是去异步队列中取异步任务放到主线程中执行的，从取任务到执行完成，我们称为浏览器的一个时钟周期或者说一个滴答。

   ​	vue为了优化性能，数据更新之后不会立刻的表现在页面当中， 我们都知道，当改变数据的时候， vue会通知watch的更新， 他是这么实现的， 他会将本次的更新任务加到一个队列当中， 直到下一个时钟周期才去渲染页面，其中就是使用的$nextTick实现的， $nextTick 是通过异步的任务， 在下一个时钟周期执行异步队列中的全部任务。源码中异步使用的是promise/setTimeout/mutationOb实现的异步。

​		一个常用到的场景就是， 我们更新完数据之后想要获取到	更新后的dom的情况下， 我们会用到this.$nextTick

2. vue 中 template -> render 的过程

   ​	我们常见的语言从写入的源代码到执行的过程都会经过以下这几步， 1. 经过词法分析，将源代码变成token；2. 讲过语法分析过程将token生成ast语法树；3.语言之间有些略微的差别，我们常见的前端编译器和jbk都是将ast语法树编译成为字节码；4. 将字节码直接执行通过即时编译器直接执行或者转为二进制的机器码指令执行。

   ​	vue的过程也不例外， 首先vue调用compileToFunction方法，其中使用parse，经过词法分析和语法分析将源码转为ast语法树，其中词法分析是通过正则匹配实现的， 他将匹配到的token压入一个栈中， 当匹配到闭合标签的时候出栈并组合ast语法树。遍历ast，生成一个由with包含的字符串，其中with作用是将其中的this指向vue实例对象。_c 表示 createElement函数。使用new Function 将这个字符串转为一个函数， 然后render就是这个函数。

3. vue3中常用hooks

   ref、reactive、computed、watch、watchEffect、props、setup、onBeforeMount、onMounted、onBeforeUpdate、onUpdated、onErrorCapture、

4. 说一下vuex当中的actions和mutations特性

   vuex中重要特性有data、getter、mutations、actios、modules，其中actions、mutation是vuex中重要的特性。

   更改vuex中state唯一的途径是提交mutation，mutations接收的是一个state， state相当于vue中的data。

   actions接收一个store， 通过这个store可以调用commit方法去修改state

5. 说一下vuex的原理

​	vuex是vue的一个全局状态管理的一个库。 在vuex的state中定义的变量，可以在vue的任何组件中修改。

​	那么就有两个重要的问题， 我们在每个组件中都能够修改vuex和修改vuex会触发视图的 更新他是如何做到的呢

​	为什么每个组件中都能够操作vuex， 在vue组件当中beforeCreate生命周期中， 调用this.$store = this.$parent.$store.

​	为什么vuex是响应式的，根据vuex的源码我们不难看出， vuex中的state是挂到vue组件的data中的， vuex中的getter是挂到vue组件的computed当中的。 

6. 说一个vue-router都有哪些钩子和他们的触发时机

   beforeRouteLeave(上一个组件) -> beforeEach -> beforeEnter（路由独享守卫）-> beforeRouteEnter（组件进入守卫）-> beforeResolve（路由确认守卫）-> afterEach

7. 路由的模式以及他们的区别

   1. hash模式：hash模式通过监听浏览器的onHashChange事件

   2. history模式

      hash模式通过hash的方式来管理路由， hash的方式通过onhashChange来管理路由的跳转操作。

      history模式，h5提供了

   7.1 hostory模式下， nginx服务器应该如何配置

   ```
   location / {
       try_files $uri $uri/ /index.html;
   }
   # nginx 发现并没有请求的文件， 那么就会查看是否有请求的目录， 如果请求的目录也没有， 那么就会返回index.html文件
   ```

   

8. vue2 和 vue3 的区别
   1. 数据双向绑定的原理不同：vue2使用的是Object.defineProperty api 而 vue3采用的是proxy api
   2. 是否支持碎片：vue2不支持碎片而vue3支持碎片Fragment， 也就是说可以有多个根节点
   3. api方式不同： vue2 采用options api 而 vue3 采用的是composition api， 这就导致vue3能够更容易的分离视图与业务， 而不需要使用vue2中的mixin
   4. 定义数据的方法不同：vue2中的数据放到data中去， 而vue3使用ref 和 reactive定义响应式数据；
   5. 生命周期的钩子不同：

​		vue2：beforeCreate，createed、beforeMount、mounted、beforeUpdate、updated、beforeDestory、destoried

​		vue3：setup（代替beforeCreate、crated）、onBeforeMount、onMounted、onBeforeUpdate、onUpdated、onBeforeUnMount、onUnMounted

  6. ​	vue2当中v-if和v-for会有冲突， 因为v-if的优先级要先于v-for、而vue3中没有这个问题。

9. vue-router的原理
   1. hash 模式通过监听hashChange事件， 切换在route中注册组件， vuerouter 根据hash值的不同切换相应的组件
   2. history模式， 通过pushState 和 replaceState不会跳转的特性， 根据路径切换不同的组件

10. 自定义指令

​	自动获取焦点

​	点击复制信息

11. 说一下vue的单向数据流

    vue的单向数据流是：在父组件中定义的数据可以通过props传递给子组件， 在子组件当中props是不允许被修改的，否则会在控制台报一个警告， 如果想要在子组件中修改props只能通过$emit进行触发父组件中传递的事件进行修改。 

    父组件修改了数据， 通过props传递给子组件 也会同时响应。

12. vue父子组件生命周期的执行顺序

    初始化：父beforeCreate->父created->父beforeMount->子beforeCreate->子created->子beforeMount->子mounted->父mounted

​	更新：父beforeUpdate->子beforeUpdate->子updated->父updated

​	销毁：父beforeDestory->子beforeDestory->子destoryed->父destoryed















