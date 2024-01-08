BFC

​	BFC是一个独立的布局环境， BFC内部的布局不会影响BFC外部的布局

触发BFC的条件：

	1. 根元素body
	1. float不为none的元素
	1. overflow 不为visible的元素
	1. 行内块级元素
	1. 绝对定位的元素position 为 absolute 和 fixed

BFC解决问题：

	1.  解决两个块级元素上下边界重叠的问题， 可以将其放在两个BFC容器当中；
	1.  float 元素脱离文档流元素导致父元素高度塌陷问题， 父元素也定义成为BFC；
	1.  float元素文字环绕问题

css3新增特性

	1.  盒子： border-radius、box-shadow、broder-image
	1.  文字：word-shadow、word-wrap
	1.  背景：线性和径向渐变， linear-gradient、radito-gradient
	1.  过度和动画：trasition、@keyword、animation
	1.  变形：transform
	1.  背景颜色和图片：bk-size、bk-clip、bk-origin
	1.  新增颜色表示：rgba、hsla
	1.  字体：@font-face





























