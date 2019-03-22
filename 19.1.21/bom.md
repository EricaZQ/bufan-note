---
title: bom
---
# BOM
## js组成
+ javascript
    - ECMAScript 基础语法,包括变量声明,数组,对象,函数,循环等.
+ dom
    -  document object model , 文档对象模型. 包括了操作文档对象(html对象)的所有标签的增删改查的api.
+ bom
    - browser object  model ,浏览器对象模型. 包括定时器,浏览器滚动监听,浏览器宽高,元素边框等.
## bom
+ 三大家族和一个事件对象
    - 三大家族（offset/scroll/client）
    - 事件对象event   （事件被触动时，鼠标和键盘的状态）（通过属性控制）
## offset家族
+ offset这个单词本身是偏移，位移的意思。
+ 在js中是为了方便获取元素尺寸。
+ `offsetWidth和ffsetHeight`
    - 检测盒子自身宽高，包括边框和padding
    - 得到的结果是number类型，可以直接参与运算
```
var d1 = document.getElementsByClassName('d1')[0];
console.log('d1.offsetWidth===>',d1.offsetWidth);
console.log('d1.offsetHeight===>',d1.offsetHeight);

```
+ `offsetLeft和offsetTop`
    - 检测距离父盒子有定位的左/上的距离。
    - 如果父类没有定位，就一直往上找，找到有定位的父类元素为止。如果所有的父类都没有定位。那么指的是距离body边框的距离
    - 如果父类有定位元素，则找的是到定位元素的距离。
```
var d1 = document.getElementsByClassName('d1')[0];
console.log(d1.offsetLeft);
console.log(d1.offsetTop);
```
+ `offsetParent`
    - 检测父系盒子中带有定位的父盒子节点
    - 如果父类没有定位，就一直往上找，找到有定位的父类元素为止。如果所有的父类都没有定位。那么offsetParent为body。
    - 如果父类有定位元素，则offsetParent取最近的那个带定位的父级元素。
+ 任意元素到body的距离
```
var d1 = document.getElementsByClassName('d1')[0];
var d1Left = bodyDistance(d1);
console.log('d1Left',d1Left);
// 距离body边框的距离
function  bodyDistance(el){
    // 1.停止条件 有没有父类的定位元素了
    // offsetParent返回定位的父类元素对象
    var pNode = el.offsetParent;
    if(pNode.tagName == 'BODY'){
        return el.offsetLeft;
    }

    return el.offsetLeft + bodyDistance(pNode);
}
```
+ offset和style的区别
    - style只能获取行内样式的值
    - style获取的结果是css样式,单位带px,而offsetwidth获取的是number类型
    - offsetWidth 只能获取整数值
    - 通过对象修改属性`this.style.width = '400px';`这是给这个节点加上行内样式，将他的css覆盖掉了。
```
var d1 = document.getElementsByClassName('d1')[0];
console.log(d1.style.width);
console.log(d1.offsetWidth);
d1.onclick = function(){
    //通过对象修改属性
    this.style.width = '400px';
    // offsetWidth 是只读属性 只能获取不能设值
    this.offsetWidth  = 400;
}


```

## scroll家族
+ `scrollWidth`和`scroHeight`
    - 检测盒子的宽高。（调用者：节点元素。属性。）
    - 盒子内容的宽高。（如果有内容超出了，显示内容的高度）
    - 和offset不同，scroll不包含border，但是包含padding。
+ `scrollTop`和`scrollLeft`
    - 网页，被浏览器遮挡的头部和左边部分。
    - 被卷去的头部和左边部分。
    
+ 页面被卷进去的高度
    - `document.documentElement.scrollTop`已经声明DTD（IE678只认识他）
        - `Element.scrollTop` 属性可以获取或设置一个元素的内容垂直滚动的像素数
        ```
        document.documentElement.scrollTop =intvalue
        window.scrollTo(x,y);
        ```
    - `window.pageYOffset`火狐/谷歌/ie9+以上支持的
+ 监听浏览器的滚动事件，实时监听页面滚进去的高度,只要页面滚动无论向左向右，向上向下，哪怕只有1px，都会触动这个事件
```
        window.onscroll = function(){
			console.log(document.documentElement.scrollTop);
		}
```
+ 骨架标签
    - document.title --- 文档标题；
	- document.head --- 文档的头标签
	- document.body --- 文档的body标签；
	- document.documentElement --- html
## event事件
+ 事件对象（event）
    - 在触发DOM上的某个事件时，会产生一个事件对象event，这个对象中包含着所有与事件有关的信息。所有浏览器都支持event对象，但支持的方式不同。比如鼠标操作时候，会添加鼠标位置的相关信息到事件对象中。
    - 普通浏览器支持 event（带参，任意参数）
    - ie 678 支持 window.event（无参，内置）
    -  总结：他是一个事件中的内置对象。内部装了很多关于鼠标和事件本身的信息。

+ 事件对象的获取（event的获取）
    - IE678中，window.event 
    - 在火狐谷歌中，event或者，在事件绑定的函数中，加参，这个参数就是event.
    - 兼容方式  `var event = event||window.event;`
    ```
    //ie8
    d1.onclick = function(){
        var event = window.event;
        alert(document.documentElement.scrollTop+event.clientY);
    }
    //高级浏览器
    //e就是event对象
		d1.onclick = function(e){
			console.log(e);
			console.log('clientY',e.clientY);
		}
    ```
+ event属性
    - screenX/Y:鼠标位于屏幕的上方和左侧的距离。（屏幕）
    - pageX/Y:鼠标位于整个网页页面的顶部和左侧部分的距离。（页面）
    - clientX/Y:鼠标位于浏览器的左侧和顶部的距离。（浏览器大小和位置）
    ```
    var d1 = document.getElementsByClassName('d1')[0];
		//e就是event对象
		d1.onclick = function(e){
			console.log(e);
			// page指的是页面本身
			// client指的是浏览器客户端(不包含top的工具栏)
			// screen指的是显示器
			console.log('pageX',e.pageX);
			console.log('pageY',e.pageY);
			console.log('screenX',e.screenX);
			console.log('screenY',e.screenY);
			console.log('clientX',e.clientX);
			console.log('clientY',e.clientY);
		}
    ```
    - onmousemove 只要鼠标在绑定该事件的事件源上移动，哪怕1像素，也会触动这个事件。（这个事件可以直接或者间接的替代定时器）

## client 家族
+ 属性
    - `clientWidth`获取网页可视区域宽度
    - `clientHeight`获取网页可视区域高度
    - 盒子调用：指盒子本身。
    - `body/html`调用：可视区域大小(如果存在调试窗口，则显示能看到的版面的宽高)。	
    - `clientX`鼠标距离可视区域左侧距离（event调用）
    - `clientY`鼠标距离可视区域上侧距离（event调用）
    - `clientTop/clientLeft`盒子的border宽高
+ 检测浏览器宽和高度，可视区域
    - `document.body.clientHeight` (`document.documentElement.clientHeight` )  (ie和firfox都能用)
	- `window.innerHeight`  (firefox能用)
	- 推荐用innerHeight  (忽略滚动条的宽度)
    - 兼容写法：`var cWidth = window.innerWidth||this.clientWidth;`
+ onresize 事件；沉浸式体验
    - 有一个像素的改变都会触发，只要浏览器的大小改变，哪怕1像素，都会触动这个事件。用于做沉浸式体验。
    ```
    //根据浏览器可视区域的高度改变背景图片的高度
    var banner = document.getElementsByClassName('banner')[0];
    //初始化banner高度
    resizeBanner();
    //只要浏览器宽高发生了变化,哪怕只有1px 那么都会触发
    window.onresize = function () {
        // console.log('当前高度为: ',window.innerHeight||document.documentElement.clientHeight);
        resizeBanner();
    }

    function resizeBanner(){
        // banner的高度 应该和当前用户访问的客户端高度一致,满足沉浸式效果
        var clientH = window.innerHeight||document.documentElement.clientHeight;
        banner.style.height = clientH + 'px';
    }
    ```
+ 阻止冒泡事件
    - 火狐、谷歌、IE11可用:`event.stopPropagation()`
    - IE10以下则是使用：`event.cancelBubble = true`
    - 兼容代码如下：
    ```
    var event = event || window.event;
    if(event && event.stopPropagation){
                event.stopPropagation();
    }else{
                event.cancelBubble = true;
    }
    ```
    - addEventListenner(参数1，参数2，参数3)
        + 调用者是：事件源。		
        + 参数1：事件去掉on;参数2 ：调用的函数;参数3：可有可无。没有默认false.false情况下，支持冒泡。True支持捕获。
+ 事件委托
    - 动态添加的标签没有办法直接给他绑定事件；
    ```
    var ul = document.getElementsByClassName('ul')[0];
    var lis = ul.children;
    var btn1 = document.getElementsByClassName('btn1')[0];
    //这种情况无法针对"未来"产生的元素绑定事件,我们需要"事件委托"
    // for(var i = 0 ; i < lis.length ; i ++){
    // 	lis[i].index = i;
    // 	lis[i].onclick = function(){
    // 		alert(this.innerText);
    // 	}
    // }
    btn1.onclick = function(){
        var index = lis.length+1;
        var liHtml = '<li class="li_'+index+'">li_'+index+'</li>';
        //插入页面
        ul.innerHTML = ul.innerHTML + liHtml;
    }
    //把事件委托给ul
    ul.onclick = function(e){
        //通过e.target可以获取真正触发事件的元素
        var target = e.target;
        if(target.tagName == 'LI'){
            alert(target.innerText);
        }
        
    }
    ```
+ 获取任意类型的CSS样式的属性值
    - `Div.style.width`    
    - `div.currentStyle.width`     IE
    - `Window.getComputedStyle(div,null).width;`    火狐
    - 他们的公共使用变量或者字符串获取属性值的方法都是：去电属性和点，然后加上中括号和属性的字符串形式。
    ```
    Div.style[“width”];
    div.currentStyle[“width”];
    Window.getComputedStyle(div,null)[“width”];
    ```
+ 回调函数
    - 程序执行完毕，再次执行的函数。
    - 在函数中给指定的函数定义一个形参，然后程序执行到最后，调用这个形参后面加一个括号。
    ```
    function animate(el,target,fn){
        
    }
    animate(d1,target,function(){
        setTimeout(function(){
            animate(d1,target2,function(){
                animate(d2,target2);
            });
        },1000)
    });
    ```
## 三大家族的区别（三大家族总结）
### Width和height
+ clientWidth  = width  + padding   //通过设置计算clientWidth （买手机，盒子里的都是我的）
+ clientHeight  = height + padding
+ offsetWidth  = width  + padding + border  (生产手机，要计算盒子的宽高，整体的空间)
+ offsetHeight  = height + padding + border
+ scrollWidth   = 内容宽度（不包含border）(能被卷的东西，如果超出计算整个内容)
+ scrollHeight  = 内容高度（不包含border）
### top和left
+ offsetTop/offsetLeft ：
	- 调用者：任意元素。(盒子为主)
	- 作用：距离父系盒子中带有定位的距离。
+ scrollTop/scrollLeft:(盒子也可以调用，必须有滚动条)
	- 调用者：document.body.scrollTop/.....(window.onscroll==)
	- 作用：浏览器无法显示的部分（被卷去的部分）。
+ clientY/clientX:（clientTop/clientLeft 值的是border）
	- 调用者：event.clientX(event)
	- 作用：鼠标距离浏览器可视区域的距离（左、上）。








 



