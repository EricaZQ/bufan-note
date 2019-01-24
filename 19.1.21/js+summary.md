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
## switch循环
+ 字符串类型 从输入框获取的都是字符串类型。
+ 如何把字符串转换为number
	- 1. '3'-0 = 3;
	- 2. `parseInt('3') ==> 3`   int整数类型   `parseInt('3.333')==>3`
	- 3. `parseFloat('3.3') ==> 3.3` float 浮点类型(小数) 
```
		var fruitNum = prompt('请输入编号:');
		switch (parseInt(fruitNum)) {
			case 1:
				alert('苹果');
				break;
			case 2:
				alert('香蕉');
				break;
			case 3:
				alert('橘子');
				break;
			case 4:
				alert('梨');
				break;
			default:
				alert('没有这个编号!');
				break;
		}
```
## while循环
+ 需要有跳出条件
```
		var num = 1;
		while (num < 10) {
			console.log('num==>',num);
			num ++ ;
		}
```
## do...while循环
+ 先斩后奏，先运行后判断。
```
	do{
			console.log('num2==>',num);
		}while(num!=1)

```
## for循环
+ **很重要，会经常用到**
+ `i==0` 初始值 `i< 10`  执行条件 `i+=2` 步长
```
		for(var i = 0 ; i < 10 ; i+=2){
			console.log(i);
		}
		console.log('结束循环==>'+i);//可以打印，但是在java中这样写会报错。

		for(var j=10 ;j>0 ; j--){
			console.log('j==>',j);	
		}

```
+ break 一旦break 循环体被结束,当前循环体内部break后面的代码也不再执行。
```
		var num = 10;
		// 遍历0~99
		// 如果存在 i == num 结束循环
		for(var i = 0 ; i < 100 ; i ++){
			console.log('i==>',i);
			if(num == i){
				console.log('结束循环...');
				break;//直接跳出循环。
			}
			console.log('么么哒!');//一旦break这句将不会执行了。
		}
		console.log('end  for....');//但是并不会影响循环外的代码。
```
+ continue 结束本次循环,后面的代码不再执行。
```
		for(var i = 1; i <= 100 ;i++){
		 	if(i%7==0){
		 		console.log(i);
		 		continue;//这句结束下面的步骤不会进行了，但是并没有跳出循环，只是这一次循环结束。
		 	}
		 	if(i%17==0){
		 		console.log(i);
		 	}
		 }
```
+ 乘法表
```
		for(var i = 1 ; i <= 9 ; i++){
			var str = '';
			for(var j = 1 ; j <=9 ; j++){
				if(j>i){
					break; //只会停止内部循环体，跳出内部循环。
				}
				str = str + (i+'*'+j+'='+i*j+' ');  
			}
			//需要打印9行 所有在外层循环打印
			console.log(str);
		}
```
## 数组
+ 声明数组
	- 通过对象形式创建数组 `var arr = new Array();`
	```
		arr[0] = 30;
		arr[1] = 22;
		arr[2] = 33;
		// 数组的下标是从0开始的
	```
	- 直接创建空数组 `var arr2 = [25,33,44,70];`
	```
		console.log(arr);
		//可通过下标赋值 也可以通过下标取值
		console.log('arr[2]==>',arr[2]);
		console.log(arr2);
		console.log('arr2[2]==>',arr2[2]);
		// arr 是一个对象  xx.abc  abc是xx的属性;  xx.def() def是xx的方法
		console.log('数组的length==>',arr2.length);
	```
+ 数组的遍历
	- 利用数组的length属性遍历
	```
		for(var i = 0 ; i < arr.length ; i++){
			console.log('下标为'+i,arr[i]);
		}
	```
	- for in 遍历
	```
		for(var a in arr){
			console.log(arr[a])
		}

	```
+ 数组的方法
	- concat() 拼接 并不会影响原来的数组，需要一个新的变量去接收拼接后的结果。
	- join() 把数组转换为字符串,默认是用‘,’分开，想用什么符号可以在括号中写。
	- split() 把字符串打断为数组，字符串本来是用什么分割的，就在括号里写上这个符号。
	```
		var arr = [1,2,3];
		var arr2 = [4,5,6];
		// concat() 拼接 
		var arr3 = arr.concat(arr2);
		console.log(arr);
		console.log(arr3);
		// join() 把数组转换为字符串
		 var arr4 = ['a','b','c'];
		console.log(arr4.join(','));
		// split() 把字符串打断为数组
		var str = 'it is a fineday today';
		var arr5 = str.split(' ');
		console.log(arr5);
		//遍历所有的编号
		var code = '1101,1110,111,111,10101';
		var codeArr = code.split(',');
		for(var i = 0 ;i < codeArr.length ; i++){
			console.log(codeArr[i]);
		}

	```
	- push()   从后面推进去
	- unshift()  从数组的前面放入
	- pop()    删除最后一个元素
	- shift()   删除第一个元素
	```
		var arr = [1,2,3];
		arr.push(4);
		arr.push(5);
		arr.unshift(0);
		console.log(arr);
		arr.pop();
		console.log(arr);
	```
## 冒泡排序
+ 冒泡排序（Bubble Sort），是一种计算机科学领域的较简单的排序算法。它重复地走访过要排序的元素列，依次比较两个相邻的元素，如果他们的顺序（如从大到小、首字母从A到Z）错误就把他们交换过来。走访元素的工作是重复地进行直到没有相邻元素需要交换，也就是说该元素已经排序完成。
	```
		var arr = [8,5,4,3,2];
		//外层循环，控制轮数。
	    for(var j = 1 ; j < arr.length ; j ++){
	    //内层循环，控制每一个和旁边的数进行比较和换位。
	    	for(var i = 0 ; i < arr.length-j ; i++){
	    		if(arr[i]>arr[i+1]){
	    			//交换位置
	    			var temp = arr[i];
	    			arr[i] = arr[i+1];
	    			arr[i+1] = temp;
	    		}
	    	}
    		console.log('第'+j+'轮的结果',arr);
	    }
	    console.log('最终结果',arr);
	```

## 选择排序
+ 选择排序（Selection sort）是一种简单直观的排序算法。它的工作原理是每一次从待排序的数据元素中选出最小（或最大）的一个元素，存放在序列的起始位置，然后，再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。以此类推，直到全部待排序的数据元素排完。 选择排序是不稳定的排序方法。
```
		var arr = [1,8,5,7,4,3,2];
		//外层循环，控制循环的轮数。
		for(var j = 0 ; j < arr.length-1 ; j++){
			//声明变量minIndex，这是最小值的下标。默认最小值的下标为0 
			var minIndex = j;
			//遍历整个数组，拿第一个和后面的数作比较，如果后面的数比较小，就把这个小数的下标付给minIndex。
			for(var i = 1+j ; i < arr.length ; i ++){
				if(arr[minIndex]>arr[i]){
					//让贤
					minIndex = i;
				}
			}
			//如果最小下标依然是j 就没必要交换位置，只有j!=minIndex，才有交换的必要。
			if(j!=minIndex){
				//放到第一个位置
				var temp = arr[j];
				arr[j] = arr[minIndex];
				arr[minIndex] = temp;
			}
			
			console.log('获取了最小下标为'+minIndex);
			console.log(arr);
		}
		console.log('最终结果为:',arr);
```
## 求平均值
+ 先遍历数组把数组中的数字遍历出来。
```
		var arr = [33,21,1,40,12,5] 
		var sum = 0 ;
		for(var i = 0 ; i < arr.length ; i++){
			sum += arr[i];
		}
		console.log(sum/arr.length);
```
## 函数
+ 基本知识
	- js的复杂数据类型：对象类型   数组  函数类型
	- 函数如果不调用是不会执行的。
	- 为什么需要函数，函数可以封装一部分功能，解决重复问题。
	- 科学编程 面向对象的编程 继承 封装 多态，函数本身就是封装的体现。
+ 函数的声明方式
	- 自定义函数 可以先使用，后声明。
	- 匿名函数 必须先声明，后使用。
	- 一般多使用自定义函数，业务逻辑部分放在前面（就是是能实现什么功能），具体实现部分放在后面（函数）。
	```
		// a) 业务逻辑部分
		say();

		// b) 具体实现部分
		// 1. 自定义函数 
		function  say(){
			alert('hello,world!');
		}
		// 2. 匿名函数  
		var run = function(){
			alert('Hi  i  am  running...');
		}
		run();
	```
+ 函数的参数
	- 函数是可以接受参数的，参数是函数体与外部程序的桥梁。
	- js中没有方法重载，如果函数名重复的话，后面会覆盖前面的方法，但这个在java中是可以被当做两个方法正常使用的，称为方法的重载。
	- 实参比形参多，多余的实参会被忽略。
	- 形参比实参多，就会报错。
```
		// x,y 为函数的形参 占位符
		function add(x,y){
			alert(x+'+'+y+'='+(x+y));
		}
		//如果函数名重复的话,后面会覆盖前面的方法,但是这个在java中是可以被当做两个方法正常使用过的,那么称为方法的重载.
		function add(x,y,z){
			alert(x+'+'+y+z+'='+(x+y+z));
		}
		// 3, 5  函数的实参
		add(3,5);
		add(2,7);
		// 1. 如果实参比形参多,多余的实参会被忽略.
		add(1,3,5,6);
		// 2. 如果形参比实参多,错误!!!
		add(1);
		// 3. 使用呢? 一般实参跟形参是一样多的. 特殊情况,讲到再说
		// 4. 面试题: js中没有方法重载!

```
+ 函数的返回值
	- return返回函数的执行结果，这样的话函数外部也可以使用。return之后的代码不再执行。
```
		function add (x,y) {
			return x+y;
			console.log('么么哒!');
		}
		//弹出3,5的结果
		var sum = add(3,5);
		alert(sum);
		// 打印3,5的结果
		console.log(sum);

```
+ 变量的作用域
	- 在windows对象（script标签可以认为是js的window对象）里声明的变量，在函数里都可以使用。
	- 函数内部不能调用其他函数内部的变量。
	- 在window作用域不能调用函数内部的变量。







	
	
	

