---
title: dom
---
# DOM
## 事件
 + js是以事件驱动为核心的一门语言。js是采用事件驱动(event-driven)响应用户操作的。比如通过鼠标或者按键在浏览器窗口或者网页元素(按钮，文本框...)上执行的操作，我们称之为事件(Event)。由鼠标或热键引发的一连串程序的动作，称之为事件驱动(Event-Driver)。对事件进行处理程序或函数，我们称之为事件处理程序(Event Handler)。
 + 事件的三要素。
    - 事件源：要触发的对象  （一般是名词，事件发起者，比如开关按钮）
    - 事件：怎么触发这个事情  （一般是动词，触发事件，比如点击开关）
    - 事件处理程序：事件处理程序:发生了什么事情 （处理结果，比如灯亮了）
 + js做什么：获取事件源，绑定事件，书写事件驱动程序。 
 + 事件有哪些
    - onabort	图像加载被中断
    - onblur	元素失去焦点
    - onchange 用户改变域的内容
    - onclick	鼠标点击某个对象
    - ondblclick	鼠标双击某个对象
    - onerror	当加载文档或图像时发生某个错误
    - onfocus	元素获得焦点
    - onkeydown	某个键盘的键被按下
    - onkeypress	某个键盘的键被按下或按住
    - onkeyup	某个键盘的键被松开
    - onload	某个页面或图像被完成加载
    - onmousedown	某个鼠标按键被按下
    - onmousemove	鼠标被移动
    - onmouseout	鼠标从某元素移开
    - onmouseover	鼠标被移到某元素之上
    - onmouseup	某个鼠标按键被松开
    - onreset	重置按钮被点击
    - onresize	窗口或框架被调整尺寸
    - onselect	文本被选定
    - onsubmit	提交按钮被点击
    - onunload	用户退出页面
## dom概述
 + HTML DOM是HTML Document Object Model(文档对象模型)的缩写，HTML DOM则是专门适用于HTML/XHTML的文档对象模型。熟悉软件开发的人员可以将HTML DOM理解为网页的API。它将网页中的各个元素都看作一个个对象，从而使网页中的元素也可以被计算机语言(js)获取或者编辑。 例如Javascript就可以利用HTML DOM动态地修改网页。 
 + dom的数据结构是树状的，一个元素只能有一个父节点。
 + dom元素
    - 页面中所有**标签**都是dom元素。
 + node节点
   - 页面中所有的标签都是node节点
	- 标签的文本内容也是node节点
	- 标签的换行 回车 也是节点
	- 标签的属性也是节点
	- 标签的注释 也是节点
 + 获取dom节点
    - `document.getElementById();` 根据id获取
    - `document.getElementsByClassName();`根据class名称获取
    - `document.getElementsByTagName(); ` 根据标签名获取
```
         //获取到di元素
		var d1El = document.getElementById('d1'); 
		//结果类型为 htmlcollection 集合,类似于数组但不是数组,我们称之"伪数组"
		// 可以通过数组下标获取内容,但是不具备数组的sort等基本api
		var d1El_2 = document.getElementsByClassName('d1'); 
		// 也就是说可以直接获取,但是这种方法在IE8
		var d1El_3 = document.getElementsByClassName('d1')[0];
		// 标签选择
		var d1El_4 = document.getElementsByTagName('div')[0];
 		console.log(d1El);
		console.log(d1El_2);
		console.log(d1El_2[0]);
		console.log(d1El_4);

```
### 通过关系获取节点
   **DOM的节点并不是孤立的，因此可以通过DOM节点之间的相对关系对它们进行访问。节点的访问关系，是以属性的方式存在的。**
 + 父节点
   - 一个节点只有一个父节点。调用方式就是`parentNode`
```
      var d1El = document.getElementsByClassName('d1')[0];
		// parentNode 属性
		var pNode = d1El.parentNode;
		console.log(pNode);
		
		//事件的3要素 给pnode绑定click事件
		pNode.onclick = function () {
			// 样式的操作
			//background-color在js中应该采用驼峰命名法
			pNode.style.backgroundColor = 'purple';
		}
```
+ 兄弟节点
   - nextSibling：调用者是节点。（存在浏览器兼容问题）
IE678中指下一个元素节点（标签、注释）。在火狐谷歌IE9+(标准)以后都指的是下一个节点（包括空文档和换行节点）。
   - nextElementSibling：在火狐谷歌IE9都指的是下一个元素节点。
   - 总结：在IE678中用nextSibling，在火狐谷歌IE9+  ie10以后用nextElementSibling
   - 兼容写法：`nextEle =节点.nextElementSibling || 节点.nextSibling`
   **兼容写法顺序不可调换**
   - previousSibling：调用者是节点。IE678中指前一个元素节点（标签）。在火狐谷歌IE9+以后都指的是前一个节点（包括空文档和换行节点）。
   - previousElementSibling：在火狐谷歌IE9都指的是前一个元素节点。
   - 总结：在IE678中用previousSibling，在火狐谷歌IE9+以后用previousElementSibling。
   - 兼容写法：`previousEle =节点.previousElementSibling || 节点.previousSibling;`
   ```
      var li4 = document.getElementById('li4');	
		//兼容写法 不能改变顺序
		var li5 = li4.nextElementSibling || li4.nextSibling;	
		li5.style.backgroundColor = 'red';
      var li3 = li4.previousElementSibling || li4.previousSibling;
      li3.style.backgroundColor ='red';
   ```
+ 孩子节点
   - firstChild：调用者是父节点。IE678中指第一个子元素节点（标签）。在火狐谷歌IE9+以后都指的是第一个节点（包括空文档和换行节点）。
   - firstElementChild:在火狐谷歌IE9都指的第一个元素节点。
   - lastChild:调用者是父节点。IE678中指最后一个子元素节点（标签）。在火狐谷歌IE9+以后都指的是最后一个节点（包括空文档和换行节点）。
   - lastElementChild：在火狐谷歌IE9都指的最后一个元素节点。
   - **兼容写法与上面的兄弟相同**
+ 所有孩子节点
   - childNodes：它是标准属性，嫡出，它返回指定元素的子元素集合，包括HTML节点，所有属性，文本节点。火狐 谷歌等高本版会把换行也看做是子节点。
      + nodeType  ==  1  时才是元素节点(标签)
      + nodeType  ==  1  表示的是元素节点   记住   元素就是标签
      + nodeType  ==  2  表示是属性节点   了解
      + nodeType  ==  3  是文本节点   了解
	   + nodeType  ==  8  注释  了解
   - children：非标准属性，庶出，它返回指定元素的子元素集合。但它只返回HTML节点，甚至不返回文本节点，虽然不是标准的DOM属性，但它和innerHTML方法一样，得到了几乎所有浏览器的支持。children在IE6/7/8中包含注释节点。
   ```
   var ulEl = document.getElementById('ul1');
		var lis = ulEl.childNodes;
      //遍历出来所有li的nodeType
		for(var i = 0 ; i < lis.length ; i ++){
			console.log(lis[i].nodeType);
		}
		var lis2 = ulEl.children;
		lis2[2].style.color = 'red';
		console.log(lis2);
      //可以通过数组下标改变样式
      var liEl1 = ulEl.children;
        liEl1[2].style.color = 'red';
        console.log(liEl1);


   ```
   - 所有孩子节点的问题
      + 在ie6,7,8中 children是包含注释节点的,所以需要把注释节点过滤掉，需要封装一个函数。
      ```
      var lis = myChildren(document.getElementById('ul1'));
		alert(lis.length);
		function myChildren (pNode) {
			var children = pNode.children;
			var rs = [];
			for(var i = 0 ; i < children.length ; i++){
				//过滤元素节点
				if(children[i].nodeType == 1){
					rs.push(children[i]);
				}
			}
			return rs;
		}
      ```
+ 创建节点
  - 使用方法是这样的document.createElement();
```
         d1El.onclick = function(){
			if(myChildren(this).length>0) return;
			//通过api创建一个元素
			//注意:元素创建之后必须插入才能显示
			// 插入a)  父节点.appendChild();
			var d2El = document.createElement('div');
			d2El.style.width = '200px';
			d2El.style.height = '200px';
			d2El.style.backgroundColor = 'red';
			//把创建的d2El插入的父节点
			d1El.appendChild(d2El);
		}
```
      
+ 插入节点
  - 使用方法： 父节点.appendChild();
  - 使用方法：父节点.insertBefore(要插入的节点，参考节点)；
  - 如果参考节点为null，那么他将在节点最后插入一个节点。
   ```
         btn1.onclick = function(){
         var img = document.createElement('img');
			//设置属性 记得? 对象动态添加属性
			img.src = 'wx.jpg';
			img.style.width = '100px';
			img.style.height = '100px';
			// 插入b)  父节点.insertBefore(要插入的节点，参考节点)；
			d1El.insertBefore(img, d1El.firstElementChild || d1El.firstChild);
		}

   ```
+ 删除节点
  - 用法：父节点.removeChild（子节点）。
  - 节点自己删除自己：
  - 不知道父级的情况下，可以这么写：node.parentNode.removeChild(node)
   ```
         btn2.onclick = function(){
			var img = d1El.firstElementChild || d1El.firstChild;
			// 父节点.removeChild（子节点）。
			// 删除操作 必须通过父节点执行
			d1El.removeChild(img);
		}

   ```
+ 复制节点
  - 用法：oldNode.cloneNode（true）
  - 想要复制的节点调用这个函数cloneNode()，得到一个新节点。
  - 方法内部可以传参，入股是true，深层复制，如果是false，只复制节点本身。
   ```
         btn3.onclick = function(){
         // 用法：oldNode.cloneNode（true）
         // 默认浅clone ,深clone需要增加额外的参数,如果是true，深层复制，节点里的别的节点也会复制，如果是false，只复制节点本身。
         var newDiv = d1El.cloneNode(true);
         document.body.appendChild(newDiv);
        }
   ```
+ 属性设置
   - 获取：getAttribute(名称)
   - 设置：setAttribute(名称, 值)
   ```
   btn1.onclick = function(){
			//添加属性 class
			// setAttribute是用于添加"属性"的,不是用于操作class内容的
			d1El.setAttribute('class', 'd1');
			d1El.setAttribute('title', '我是一个div1');
			var s1 = document.getElementById('script1');
			document.body.insertBefore(d1El,s1);
			//获取属性
			console.log(d1El.getAttribute('class'));
		}
   ```
   - 删除：removeAttribute(名称)
   ```
   btn2.onclick = function(){
			d1El.removeAttribute('title');
		}
   ```
+ 内容处理
   ```
      var p1EL = document.getElementsByClassName('p1')[0];
		var usernameInput = document.getElementsByClassName('username')[0];
		var ulEl = document.getElementsByClassName('ul')[0];

   ```
   - 如何给p标签插入(替换)内容 innerText/textContent
   ```
      p1EL.innerText = '不凡学院!'; // 常用
		p1EL.textContent = '你好!'; // 不常用
   ```
   - 如何给input设置value
   ```
   sernameInput.value = '张胜男';
   ```
   - 如何给ul动态添加li
   ```
         var liStr = '';
			for(var i = 0 ;i < 5;  i ++){
				liStr += '<li>li_'+(i+1)+'</li>';
			}
			//只能显示文本内容 不能解析html
			ulEl.innerHTML = liStr;
   ```


     
   


