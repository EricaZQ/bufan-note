---
title: jquery
---
# jquery
## jQuery是什么
+ jQuery 是js对dom操作的一个封装，我们可以通过使用jQuery快速的进行dom/bom的curd(增删改查)操作.
    - c create
	- u update
	- r read
	- d delete
+ 它封装JavaScript常用的功能代码，提供一种简便的JavaScript设计模式，优化HTML文档操作、事件处理、动画设计和Ajax交互。
+ 目前这个阶段，主要学习如何来使用jQuery操作DOM，其实就是学习jQuery封装好的那些功能方法，这些方法叫做API（Application Programming Interface应用程序编程接口）。
+ jq能实现的js都能实习  js能实现的jq不一定能实现
## jQuery的基本使用
+ jQuery有多个版本，并不是版本越新越好，需要看项目中依赖或者使用的jQuery插件来决定。
+ 但是各个版本的基础功能是一样的，常用的api也是一样的。
+ jQuery有开发版本和压缩版本，开发的时候一般使用开发版本，可以查看源码。上线的时候使用压缩版本，体积较小。
+ 如果使用了第三方jquery插件（日历、滚动、瀑布流等），必须先引入jquery，再引入该插件。
## 入口函数
+ `$(document).ready(function(){});`
+ `$(function(){});`  推荐
## js和jq事件处理对比
+ 事件源
    - 类选择器   .d1   类 是为了告诉程序员这个标签是什么，它跟谁是一样（类）的，类一般所有的标签都有。`$('.d1')`
    - Id选择器   #div1   id=’goods_1’   id是为了区分为一，是js中使用的，id是在需要的时候才有，多用于列表等重复性标签`$('#div1')`
    - 标签选择器    div  `$('div')`
+ 事件
    - js中事件：`onclick`    `onmouseover`  `onmousemove`
    - jQuery中事件： `click`     `mouseover`   `mousemove`
+ 事件处理程序
    - js：`onclick = function(){ }`
    - jQuery：`click(function(){  });`
## JavaScript和jQuery的区别
### Javascript是一门编程语言，我们用它来编写客户端浏览器脚本。jQuery是javascript的一个库，包含多个可重用的函数，用来辅助我们简化javascript开发。jQuery能做的javascipt都能做到，而javascript能做的事情，jQuery不一定能做到。
### 所有的前端框架的基础都是javascript，动画基础都是前面跟大家讲过的动画原理。包括以后会讲的vue.js，Angular.js 甚至市面上各种前段框架，基础都是JavaScript。只要框架能实现，js原生写法都能实现。
## jQuery基本选择器
符号|说明|用法
---|---|---
$(“#demo”) |	选择id为demo的第一个元素 |	$(“#demo”).css(“background”,”red”)
$(“.d1”) | 选择所有类名（样式名）为dl的元素 | $(“.d1”). css(“background”,”red”);
$(“div”) | 选择所有标签名字为div的元素 | $(“div”). css(“background”,”red”);
$(“*”) | 选择所有元素 | $(“*”). css(“background”,”red”)
$(“.arr.arr-l”) | 选择多个指定的元素，这个地方是选择出了 .liItem元素和div元素 | $(“.arr.arr-l”). css(“background”,”red”)
## jQuery层级选择器
符号|说明|用法
---|---|---
空格 | 后代选择器，选择所有的后代元素 | $(“div  span”). css(“background”,”red”);
> | 子代选择器，选择所有的子代元素 | $(“div > span”). css(“background”,”red”)
+ | 紧邻选择器，选择紧挨着的下一个元素 | $(“div + p”). css(“background”,”red”)
~ | 兄弟选择器，选择后面的所有的兄弟元素 | $(“div ~ p”). css(“background”,”red”)
## jQuery过滤选择器
符号|说明|用法
---|---|---
:eq(index) | index是从0开始的一个数字，选择序号为index的元素。选择第一个匹配的元素。 | $(“li:eq(1)”). css(“background”,”red”)
:gt(index) |	Index 是从0开始的一个数字，选择序号大于index的元素 |	$(“li:gt(2)”). css(“background”,”red”)
:lt(index)	| Index是从0开始的一个数字，选择小于index 的元素 | $(“li:lt(2)”). css(“background”,”red”)
:odd |	选择所有序号为奇数行的元素 |	$(“li:odd”). css(“background”,”red”)
:even |	选择所有序号为偶数的元素 |	$(“li:even”). css(“background”,”red”)
:first |	选择匹配第一个元素 |	$(“li:first”). css(“background”,”red”)
:last |	选择匹配的最后一个元素 |	$(“li:last”). css(“background”,”red”)
## jQuery属性选择器
符号|说明|用法
---|---|---
$(“a[href]”)  title  type  … | 选择所有包含href属性的元素 | $(“a[href]”). css(“background”,”red”)
$(“a[href=’baidu’]”) | 选择href属性值为baidu的所有a标签 | $(“a[href=’baidu]”). css(“background”,”red”)
$(“a[href!=’baidu’]”) | 选择所有href属性不等baidu的所有元素，包括没有href的元素 | $(“a[href!=’baidu’]”). css(“background”,”red”)
$(“a[href^=’web’]”) | 选择所有href属性以web开头的元素 | $(“a[href^=’web’]”). css(“background”,”red”)
$(“a[href$=’cn’]”) | 选择所有href属性以cn结尾的元素 | $(“a[href$=’cn’]”). css(“background”,”red”)
$(“a[href*=’i’]”) | 选择所有href属性包含i这个字符的元素，可以是中英文 | $(“a[href*=’i’]”). css(“background”,”red”)
$(“a[href][title=’内容’]”) | 选择所有符合指定属性规则的元素，都符合才会被选中。 |	$(“a[href][title=’内容’]”). css(“background”,”red”)
## jQuery筛选选择器
符号|说明|用法
---|---|---
find(selector) | 查找指定元素的所有后代元素（子子孙孙）| $(“#j_wrap”).find(“li”).css(“color”, “red”);选择id为j_wrap的所有后代元素li
children() | 查找指定元素的直接子元素（亲儿子元素） | $(“#j_wrap”).children(“ul”).css(“color”, “red”);选择id为j_wrap的所有子代元素ul
siblings() | 	查找所有兄弟元素（不包括自己）|	$(“#j_liItem”).siblings().css(“color”, “red”);选择id为j_liItem的所有兄弟元素
next() |	下一个兄弟 |
nextAll() |		后面所有的兄弟 |
nextUntil() |	后面所有的兄弟直到… |
prev() |	前面的兄弟
prevAll()	|	前面所有的兄弟
prevUntil()	 |	前面所有的兄弟直到…
parent() |	查找父元素（亲的） |	$(“#j_liItem”).parent(“ul”).css(“color”, “red”);选择id为j_liItem的父元素
parents()	|	所有的父节点 |
parentsUntil()	| 所以有的父节点直到
eq(index) |	查找指定元素的第index个元素，index是索引号，从0开始	 | $(“li”).eq(2).css(“color”, “red”);选择所有li元素中的第二个
## mouseover事件跟mouseenter事件的区别
+ mouseover/mouseout事件，鼠标经过的时候会触发多次，每遇到一个子元素就会触发一次。
+ mouseenter/mouseleave事件，鼠标经过的时候只会触发一次
## DOM对象跟jQuery对象相互转换
+ jQuery对象转换成DOM对象:
    - `$(“#btn”)[0]`
    - `$(“#btn”).get(0)`
+ DOM对象转换成jQuery对象：
    - `$(document)`就是在dom对象外面加一个`$`.
+ .css()方法是jQuery的，所以this必须是jQuery对象。需要把dom元素转换为jQuery对象。this ==> $(this)
## jQuery属性和样式
+ 获取css`$('.d1').css('background-color');$('.d1').css(['color','size'])`
+ 设置CSS`$('div').css('color','red')`
+ 获取属性的值`$(input).attr('value')`
+ 设置属性的值`$(input).attr('value','xxx')`
+ 设置或返回被选元素的属性和值`$(input).prop('checked')`
+ 你甚至都能在后面写一个函数
```
$('input').attr('value',function(){
    return 'xxx'
})
```
+ 设置多个属性的值
```
$('input').attr({
    type:'number',
    value:'23333'
})
```
+ 有删除就有移除，移除某一个属性`removeAttr()` `$('input').removeAttr('value')`
+ 获取html结构`$('div').html()`
+ 获取文本`$(div).text()`
+ 插入html`$('div').html('<p>hi</p>')`
+ 插入文本`$('div').text('张全蛋')`
+ 获取表单元素的value值`$(input).val()`
+ 添加类名`$(div).addClass('new')`
+ 删除类名`$(div).removeClass('new')`
+ 类名切换，有就删除，没有就添加。`$('div').toggleClass('new')`
+ 检测类名`$('.box').hasClass('box')`
+ .css是直接添加行内样式了，.addclass是添加class了。
+ 在平常给一个元素添加样式到底用.css还是.addClass呢？他们有什么优先级呢？经常需要动态改变，比如说需要后台传来的值来设置css，那么就是.css更好，静态的结构，那就是addClass更优。
## jQuery创建dom节点以及节点属性
+ 直接使用$来把html结构表示出来 `$('<span>我一个快乐的SPAN</span>')`
+ 他甚至可以把class等属性直接写里面。`$('<span class='hi'>哈哈</span>')`
+ 插入就是append和appendTo。此为append`$body.append($('<span>嘿嘿</span>'))`而appendTo就是反过来，需要插入的内容放在前面，把节点放在后面`$('<span>李双蛋与王花花</span>').appendTo($('.div'))`，这两个都是插入在内部。但是都是在内部最后追加！
+ 如果你想插入到内部并且在最前面的话 就是prepend()与prependTo.方法和append以及appendTo是一样的。
+ 插入在外部就是after和before，一个是在之后插入，一个是在之前插入。方法和append差不多。
+ 清空节点empty()，指的是清空所有的内部子节点。`$('div').empty()`
+ 删除节点并且移除自身以及全部的子节点`$('div').remove()`
+ 删除节点的同时也会把这个节点的事件给全部的清空，但是如果你想让该节点消失，但是这个节点的事件不丢失，你可以使用detach()，他会把这个节点的事件保存在内存里。
+ 有了添加有了删除，还有一个clone方法。专门用于DOM克隆。`$('.box').clone()`其中可以有一个参数，true和false来控制深克隆和浅克隆。深克隆的话他会把你的事件也克隆， 浅克隆只是复制了结构。
```
$('.box').click(function(){
    $(this).append($(this).clone(true).css('color','pink'))
})
```
+ 克隆/添加/删除都有了，那就该替换了replaceWith。
```
$('.box').replaceWith('<span>你距离成功太远了。</span>')
```
## jq动画
+ `hide`隐藏
+ `show`出现
+ `toggle`有就隐藏,没有就出现
```
//以下是通过display控制的.
$('#hide').click(function(){
    $('.box').hide()
})
$('#show').click(function(){
    $('.box').show()
})
$('#toggle').click(function(){
    $('.box').toggle()
})
```
+ `slideup`上卷
+ `slidedown`下拉
+ `slideToggle`有就上拉,没有就下来
```
//以下效果从下至上。竖向动作，slideToggle 通过高度变化来切换所有匹配元素的可见性
$('#slideup').click(function(){
    $('.box').slideUp()
})
$('#slidedown').click(function(){
    $('.box').slideDown()
})
$('#slideToggle').click(function(){
    $('.box').slideToggle()
})
```
+ `fadeOut`淡出
+ `fadeIn`淡入
+ `fadeToggle`有就淡出,没有就淡入
```
//这个是通过透明度来控制的
$('#fadeOut').click(function(){
    $('.box').fadeOut()
})
$('#fadeIn').click(function(){
    $('.box').fadeIn()
})
$('#fadeToggle').click(function(){
    $('.box').fadeToggle()
})
```
+ 淡入淡出都是从0到1,我们也可以自定义让他到想要的透明度.
```
$('#fadeTo').click(function(){
    var op = $('input').val()
    $('.box').fadeTo( 1000, op ,function(){
        alert('我已经到达了'+op)
    });
    //必需的 duration参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。必需的 opacity 参数将淡入淡出效果设置为给定的不透明度（值介于 0 与 1 之间）。可选的 callback 回调函数。
})
```
+ animate自定义动画
    - `$(el).animate(style,speed,callback)`
    - 第一个就是css，第二个就是动画的速度，，第三个就是回调。速度和函数不必须的时候可以省略不写。
    - speed有"slow"，"normal"，"fast"这三个预设值，默认是normal。也可也自定义一个毫秒值
```
$('.box').animate({
    height:"300px",
    width:'600px',
    opacity:'.5',
},3000,function(){
    alert('end...')
})

```
+ 停止动画`stop()`
    - `stop(stopAll,goToEnd);`
    - `stopAll`  是否全部停止，默认false 停止队列中所有的动画
    - `goToEnd`  是否将停止的动画  停止在当前动画的最后一个状态  

## jqs事件机制
+ jQuery 事件的绑定
    - 简单事件绑定：
        + `click(handler)`单击事件
        + `blur(handler)` 失去焦点事件
        + `mouseenter(handler)`鼠标进入事件
        + `mouseleave(handler)`鼠标离开事件
        + `dbclick(handler)`双击事件
        + `change(handler)` 改变事件，如：文本框值改变，下来列表值改变等
        + `focus(handler)`获得焦点事件
        + `keydown(handler)`键盘按下事件
    - on方式
    ```
    $('ele').on('click',function(){

    })
    //多个事件绑定在同一个 函数
    $("#elem").on("mouseover mouseout",function(){ });
    //多个事件 绑定不同的函数
    $("#elem").on({
        mouseover:function(){},  
        mouseout:function(){}
    });
    ```
+ 事件解绑
    - off解绑on方式绑定的事件
    ```
    //全部移除
    $('ele').off()
    //指定移除
    $('ele').off('click')

    ```
## 尺寸位置操作（bom）
+ 高度和宽度操作
    - height()    取值类型为num  可以直接参与运算
    - height(200) 也可以直接改变值
    - width()
    - width(100)
+ 坐标值操作
    - offset() 
    - 作用：获取或设置元素相对于文档的位置
    - 之前的offsetLeft  找有定位的父类 相对于有定位的父类的距离
    ```
    $(selector).offset();
    $(selector).offset({left:100, top: 150});
    ```
    - 注意点：设置offset后，如果元素没有定位(默认值：static)，则被修改为relative
    - position() 
    - 作用：获取相对于其最近的具有定位的父元素的位置。
    ```
    $(selector).position();
    ```
    - 注意：只能获取，不能设置。
    - scrollTop() 
    - 作用：获取或者设置元素垂直方向滚动的位置
    ```
    $(selector).scrollTop();
    $(selector).scrollTop(100);
    ```
    - scrollLeft() 
    - 作用：获取或者设置元素水平方向滚动的位置
    ```
    $(selector).scrollLeft(100);
    ```











