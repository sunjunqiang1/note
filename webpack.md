webpack和vite的区别

	1. 概念不同：webpack是一个静态模块打包器， vite是一个基于es import 开发的服务器；
	1. 编译方式不同：webpack先将代码编译成为bundle， 而vite利用es module的特性，只有在真正需要的时候才编译文件。在生产模式下vite使用rollup对代码进行打包，提供更好的tree sharking
	1. 扩展性不同：webpack有成熟的插件生态， 几乎可以实现任何想要的功能， vite插件相比与webpack有一点差距
	1. 应用场景不同：webpack由于其丰富的功能和扩展性，更适合大型复杂的项目。vite凭借更轻量和速度更适合开发小型的项目；
	1. 开发效率不同：vite由于其更快的响应速度， 开发效率要优于webpack。