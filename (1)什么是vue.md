# 什么是Vue？


    1、Vue是一个渐进式的Javescript框架

	渐进式：vue -->组件化-->vue-router(路由)--vuex(大型数据共享)--构建工具webpack--周边生态环境（element UI,nint ui,iviewe等）

    2、mvvm模式，mvc模式

	mvc:m:model(数据层)  v:view(视图层)  c:controller(控制器)

	mvvm:m:model(数据层)   v:view(视图层)   vm:viewmodel(数据模型)

     3、vue的核心特点：组件化，数据驱动，虚拟Dom

	React:this.setState()
  	Vue:自动更新
	虚拟Dom： 本质上就是一个Js对象,在内存中操作，提升性能
	
	 把Dom结构映射为一个Js对象


	<div id="app">
	  hello
	</div>


	映射成：

	{
		tagName:"div",
		attr:{id:"app",title:"hello"},
		children:{
		        "text":"hello"
		}
	}



#vue指令与修饰符

v-(指令)

	1、v-for(循环遍历)
	2、v-if(判断)
	3、v-show:
		注意：v-if和v-show区别？？看是否渲染dom结构
		v-show:切换频率高时用
		v-if:切换频率低时使用
	4、v-on：绑定事件  简写：@
	5、v-bind:绑定属性  简写： :
	6、v-model:双向绑定

	修饰符：.enter