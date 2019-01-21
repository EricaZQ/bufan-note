# 第一周总结

## 一、常见标签
`<h1>`~`<h6>` 
h1为当前页面的以及标题,一般只能写一个。
h1到h6有不同的字号。
`<hr>`
一条横线。
`<img src="" alt="">`
img的src属性指向图片的资源地址。
`<p></p>`
段落
`<br>`
br标签可以实现换行。
`<a href="" target="_blank"></a>`
a标签用于实现跳转 target属性 _blank 新窗口打开。
`<div>和<span>`
div 和span 只是单纯的标签没有任何样式和语义化.div 一般用于布局,span一般用于特殊字段引用。
**标签一般成对存在。**
***
##二、字体标签
`<em>` 斜体.少用。
`<strong>` 加粗,表示强调。
`<i> <b>` 单纯的表示斜体和加粗,没用语义化。
`<sup>` 下标 比如: 52。
`<sub>` 上标 比如: H2O 。
**一般不会在页面中出现一段裸露的话。**
***
##三、列表
`<ul><li><li></u>`可以实现列表
***注意: ul里只能嵌套li,但li可以嵌套任意元素***
**无序列表**
```
	<ul >
		<li>电脑/手机</li>
		<li>美食/箱包</li>
		<li>旅游/驴友</li>
	</ul>
```
*有序和无序对开发没有任何意义,因为在开发中都会去掉ul的默认样式。*
**有序列表**
```
	<ol>
		<li>起床</li>
		<li>洗脸</li>
		<li>刷牙</li>
	</ol>
```
**自定义列表**
```
	<dl>
		<dt>第一章</dt>
			<dd>html基础</dd>
			<dd>css基础</dd>
		<dt>第二章</dt>
			<dd>js</dd>
			<dd>动画</dd>
	</dl>
```
##四、表格
+ table  表格   
    - tr   table - row  
	- th   table-header  
	- td   table-data
+ 属性: border 边框
	- cellpadding 表格填充物 
	- cellspacing 表格间隙
	- align   left|center|right 
	- table:bgcolor  
	- tr:bgcolor






