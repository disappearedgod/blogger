---
Angular & React & Vue 对比
---
#相同点：
1. 单页应用程序
2. 组建管理 Component
3. 数据流动
4. 后段API如何进行 路径如何处理
5. css/js/
6. webpeck

#不同点:
1. React - 面向网页显示 
	jsx - 组建都涵盖在这一个文件中（html / css/ js）
	整体设计变化不大
	容易潜入网页
2. Angular - 面向整体应用开发（应用开发）
	* 精简架构设计 提供TS （AngularJs以后）
	* html/cs/js 分开
3. Vue 界面显示（类似React 但不用选择第三方插件 也没有太多选择）
	* 本身组建分开 简单
	* 一直在追赶Angular
	* 没有大公司的支持

##React & Vue：不断增加第三方插件

---
#Angular
1. 多Component 后可以lazy mounting 
2. 嵌入多个moudule
3. Single Page Component（React类似） App Component - index.html
	3.1 Rounting: (单页应用开发之前 rount 是在后端，计算出html数据推送到前端。 ) 
		* 单页应用，后段只管理数据
		* Angular framework 里面（多个lib，api请求的lib，rounting moudule） 所以称之为架构
		** Vue & React：lib 放在min-js 通过require加载
4. Angular的标准化 让代码可以90%重用
5. TypeScript 微软主推（编程效率）
6. 模版 代码 css可分
	* React：JSX 混合
	* 大型项目重要性
7. API访问
	* 直接集成HTML dispution
	* 开发环境需要share proxy，命令行配置
	* React 有一个proxy属性，设置自己API

