#问题：
1. Keep-alive （场景 视频VLog） [  文章](https://juejin.im/post/5d92acae6fb9a04e143daa0c)
  1. 作用：缓存 - 降级荣塞
  2. How： 以队列方式缓存
  3. 缓存的是什么：VNode (虚拟DOM)
  4. 坑：内存泄漏   解决方法：缓存数量限制
    5. 使用了什么机制： LRU
	*  显示隐藏
	*  设置缓存大小 
	*   自己写
   			（Keep-alive 缓存的是结果，也就是vnode，如果太大就缓存数据）
   	* 有卡顿
   		* 	
   
   Vue 基于数据驱动  -> 缓存数据
 #第一 
   
   1.  Vue runtime + complier
	*     运行时生命周期 编译时
		*   template ->
			*   (上线前变异)ast->
				*   (本地Complier，将*.vue打包成js，上线的时候只是JS 上传到服务器)render ->*
					*  【运行时】**vnode （内存中存在的状态）在内存中diff**->
> 					  DOM PULL 在React，主动发出的动作（react setSate props）后数据发生改变
>  					  DOM PUSH 在Vue，通过响应数据生成DOM					
> ` <div>{{text}}</div>. {{text}}  一个组建-> 一个watcher[内存]-> DOM` 
> 组建内部用Diff修改
> 为什么有Vnode/虚拟DOM： （缓存：类似 寄存器/内存/硬盘） 虚拟DOM - 缓冲地带 - 不同端运行
					  
						在线编译：浏览器JS运行时候调用template，然后解析  
						RuntimeOnly：如果要在Template里面加入**Component后性能非常差，必须要加入Complier包**，优化成render函数然后删除这个包（资源优化）。				
						*    （通过patch（）{ doucument.getElementBy('').apendchild()}）**修改正式DOM的动作，通过虚拟DOM树递归【慢】， react中做了fiber，做时间分片** [React Fiber(时间分片)](https://juejin.im/post/5dadc6045188255a270a0f85)
							*    -> 转换成DOM
		*   script(浏览器从服务器拉下js开始运行) --> 
			*   new Vue()  -> (把数据处理成)响应data **（生成vnode）**
		*   style
   2. Vue 浏览器端一贞解析机制
   3. Vue 首屏优化
		* 优化
			*  如何优化加载速度，白屏如何引起的
				*  运行环境：
				*  浏览器如何渲染：js/css/html 
				*  来源 - [浏览器一帧渲染](https://aerotwist.com/blog/the-anatomy-of-a-frame/)：       