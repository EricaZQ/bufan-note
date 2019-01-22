# 第三周总结
## js基础
+ 内嵌式
```
	<script>
		alert("今天天气不错!");
	</script>
```
+ 外链式
```
	<script type="text/javascript" src="main.js">
	</script>
```
+ alert
	- alert()这是一个方法 用于弹窗,输入弹窗的内容 是 "字符串"类型的,必须加引号,可以是'',也可是""。
```
	alert('今天天气不错!');
```
	
+ confirm
	- confirm 返回了两种状态 boolean 布尔类型 true/false。
```
	if(confirm('你确定要走?')){

			alert('你走吧,永远不要回来!');

		}else{

			alert('咱们结婚吧!');
		}
```
	
+ console.log
	- 调试代码用的,检查的时候在控制台可以看到。
```
	console.log('今天天气不错啊!!!');
```
+ prompt
```
	prompt('请输入您的身高,单位cm: ',0);
```
+ document.write 
```
	document.write('这是一段话...');
```
## 数据类型
+ String
	- 字符串类型，用''或""引起来。
+ Number
	- 数字类型
+ Boolean
	- 布尔类型，返回两个值，true/false。
+ underfind
	- 声明了变量 但是没有赋值。
+ null
	- null就是null。
+ 判断数据类型
	- typeof 可以判断 "基本数据类型"
```
	var name = '张三';
	var age = 20;
	console.log(typeof  name);  // string
	console.log(typeof  age);  // number
```
***
**js是弱类型语言 也就是说在声明的时候 没必要"显式"的声明数据类型,但是数据类型却是确实存在的,我们在编程的过程中应该时刻明确我们当前声明的数据类型。**
## 运算符
+ 比较运算符
	- `>  <   >=  <=  !=  ==  ===` 
	- 比较运算符的结果是  boolean。
	- num和字符串类型的nubmer比较，可以把字符串类型的number隐式转换为num进行比较，但是一般不要出现这种情况。
	- `===` 恒等于，首先判断数据类型,再判断值。
+ 算数运算符
	- `+  -  *   /   %(求余)`
	- 字符串+num ==> 拼接为字符串
	- 字符串+字符串 ==> 拼接为字符串 (在所有的编程语言中,拼接是用的最多的操作)
	- num-字符串类型的数字 ==> number
	- 字符串类型number - 字符串类型number ==> number
	- num-字符串(非number) ==> NaN(not  a  number);而且NaN!=NaN
	- 1/0 = Infinity 无限大
	- 优先级 和之前数学学的一样的。
## 内置对象
#### 在程序里,包含了一部分属性和功能的集合,我们称之为对象
+ Date  日期对象，用于获取年月日时分秒。
```
<script>
	var date = new Date();  //程序获取的是北京时间
	// js内置对象的API  applition  progrom  interface
	console.log(date);
	//根据date对象获取年份
	var year = date.getFullYear();
	var month = date.getMonth()+1; // 月份是从0开始算的范围是0~11，所以要在后面加1 
	var day = date.getDate();
	var hour = date.getHours();
	var min = date.getMinutes();
	var sec = date.getSeconds();
	document.write(year+'年'+month+'月'+day+'日 '+hour+':'+min+':'+sec);
</script>
```
+ Math对象，和Date对象不同的是 Math里的都是静态方法,不需要new。

```
<script>
		// 1.天花板函数 向上取整
		console.log(Math.ceil(2.1));  // 3
		console.log(Math.ceil(-2.1));  // -2
		//2.地板函数
		console.log(Math.floor(-2.1));  // -3
 		// 3. max 求最大值 
 		Math.max(3,7,2,8);
 		// 4. min 最小值
 		Math.min(3,7,2,8);
 		// 5. Math.random() 区间:[0,1)
 		console.log(Math.random());
 		// 6.求1-10 随机数  [1-11) 
 		console.log(Math.floor(Math.random()*10+1));
 		// 7. 任意区间 比如  15-31?     *个数+最小值
 		console.log('15-31之间随机值: ',Math.floor(Math.random()*17+15));
 		// 8. Math.pow(x,y)
 		// 9. Math.round(x) 四舍五入 但是不推荐使用  

</script>
```
## 逻辑运算符
+ &&  与/且  两个都为真==>真,有一个为假==>假
+ ||  或   两个有一个为真==>真,两个都为假==>假
+ !   非   取反
+ 连比是错误的，是不支持的 ~~console.log(3<2<5);~~，应该写成这样`console.log(3<2&&2<5);`
## 逻辑判断语句
+ 有具体作业在文件夹19.1.22
	






	
	
	

