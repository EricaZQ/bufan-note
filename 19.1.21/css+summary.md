# 第一周总结

## 一、常见标签
+ `<h1>~<h6>` h1为当前页面的以及标题,一般只能写一个。h1到h6有不同的字号。
+ `<hr>`一条横线。
+ `<img src="" alt="">`img的src属性指向图片的资源地址。
+ `<p></p>`段落。
+ `<br>`br标签可以实现换行。
+ `<a href="" target="_blank"></a>`a标签用于实现跳转 target属性 _blank 新窗口打开。
+ `<div>和<span>`div 和span 只是单纯的标签没有任何样式和语义化.div一般用于布局,span一般用于特殊字段引用。
**标签一般成对存在。**
## 二、字体标签
+ `<em>` 斜体.少用。
+ `<strong>` 加粗,表示强调。
+ `<i> <b>` 单纯的表示斜体和加粗,没用语义化。
+ `<sup>` 下标 比如: 52。
+ `<sub>` 上标 比如: H2O 。
**一般不会在页面中出现一段裸露的话。**
## 三、列表
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
## 四、表格
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
## 五、css选择器 
#### 标签选择器
```
	h1{color:red;}
```
#### id选择器
```
	#p2{
				color: blue
			}
```
**唯一标识,整个页面不能重复。**
#### class选择器
```
	.detail{
				color:orange;
			}
```
*用于描述当前标签的作用,一般可以通过class给标签设置样式。*
#### 组合选择器
只让具有danger样式的p标签变红
使用交集选择器
```
	p.danger{
				color: red;
			}
```
#### 后代选择器
.box.success 同时具备.success和.box样式的标签
后代选择器不管孩子孙子都能选中
```
	.box .success{
				color: blue;
			}
```
#### 并集选择器
```
	.span1,.span2{
				color: yellow;
			}
```
## 六、css常见属性
+ `color: red;` 字体颜色
+ `width: 200px;`长
+ `height: 200px;`高
+ `background-color: green;`背景颜色
+ `text-align: center;`水平位置有三个属性 left|center|right
+ `text-indent: 32px;` 首行缩进
+ `text-indent: 2em;` em 基于当前字体的倍数
+ `font-family: 'Ping Fang','SimSun','微软雅黑';`字体
+ `font-weight: bolder;` 100~900 >700加粗预定义: lighter  normal  bolder;
+ `line-height: 10px;`行高，行高== 父类高度 可以实现单行文本的垂直居中
## 七、标签的表现形式
*我们根据标签的表现形式把标签分为3类*
+ 块状标签 (石头)
	- 会自动换行
	- 宽高有效
	- 比如: `div  p  h1~h6  ul>li ol>li  dl>dt~dd  tr  form` 
+ 行内块标签 (果冻)
	- 不会自动换行
	- 宽高有效
	- 比如: `img  td  input  select  button`
+ 行内标签 (水)
	- 不会自动换行
	- 宽高无效
	- 比如: `span  a`
## 八、css盒子模型
#### css盒子模型
+ 盒子边框属性  `border`
	- `border-width: 100px;`边框的宽
	- `border-style: solid;none (默认) / dashed(虚线) / dotted（点） / solid(实线) / double(双实线)`
	- `border-color: blue;`边框的颜色
+ 盒子边框和内容填充物   `padding`
	- `padding: 50px;`一个值 上下左右一样
	- `padding: 50px 100px 30px 100px;`上右下左
	- `padding: 50px 100px;`两个值  上下  左右
	- `padding: 30px 80px 100px;`分别指定上、左右、下四个方向的内边距
+ 盒子间距   `margin`
	- 和padding写法一模一样
#### margin问题
+ 垂直重叠
	- 当两个div垂直放置的时候,上面盒子的`margin-bottom`和下面盒子的`margin-top`会发生重叠,最终的结果 以大 的为准
+ 嵌套崩塌
	- 当两个盒子发生嵌套的时候,里面盒子的`margin-top`会直接作用到外层盒子
解决方法: 给父类盒子添加极小的`padding/border/overflow(推荐)
overflow: hidden;`
## 十、css特性
+ 一般在实现页面的时候,会去掉所有的默认样式,包括padding/margin/list-style/a下划线
+css初始化
```
		*{
			margin: 0;
			padding: 0;
		}
		body{
			font: 16px/1.2 '微软雅黑';
		}
		ul{
			list-style: none;
		}
		a{
			text-decoration: none;
		}
```
+ 字体所有的属性都能实现继承
+ 例外
	- 1. a标签的颜色不会继承
	- 2.h1~h6标签的大小不会实现继承
+ css权重
	- 行内样式(1000)>id选择器(100)> class选择器(10)> 标签选择器(1)> 通配符
	- 权重低的会被高的覆盖掉。有多个样式则相加看谁的大，权重相同则按照就近原则。
## 十一、浮动
+ `float: left;`
	- 浮动原则: 同一个父类盒子内部,要浮动都浮动!
	-右浮动很少用,而且会影响标签原来的顺序。需要右浮动的时候可以用定位。
+ 浮动问题
	- 当子类盒子浮动,而其高度大于父类盒子的时候,会产生浮动的影响
+ 清除浮动的影响
	- 父类 `overflow: hidden;` 
	- 在浮动元素最后面添加空标签,设置样式:`clear:both;`
+ 浮动的另一个作用: 文字环绕图片。
## 十二、定位
+ 元素的定位三种:
	- 固定定位: `fixed`相对浏览器定位。
+ 相对定位: `relative`相对自己原来的位置定位。不会脱标,而且会占据原来的位置。
+ 绝对定位: `absolute`  相对父类盒子定位。
	- 没有嵌套元素,相对body做定位
	- 如果有嵌套元素,而且父类有定位元素,则相对父类做定位。用`absolute ` 父类一般都是`relative` "子绝父相"。
+ z-index
	- 如果定位元素发生了重叠,那么可以通过`z-index`控制定位元素的层级。
	- 默认级别为`z-index:0`值越大,层级越靠上。






