---
title: html5
---
# html5
#### 一些不常用的功能详见word文档内容
## 表单
+ 输入类型
    - email 输入email格式
    - tel 手机号码  
    - url 只能输入url格式
    - number 只能输入数字
    - search 搜索框
    - range 范围 滑动条
    - color 拾色器
	- time	时间
	- date 日期 不是绝对的
	- --datetime 时间日期(移动支持)
	- month 月份
	- week 星期
    ```
    <form action="">
        用户名: <input type="text" name="username" autocomplete="off">
        邮箱:<input autofocus type="email">
        手机:<input type="tel">
        网址:<input type="url">
        年龄:<input type="number">
        搜索:<input type="search">
        范围::<input type="range">
        肤色:<input type="color">
        生日: <input type="date">
        性别: <input type="text" list="data">
            <datalist id="data">
                <option>男</option>
                <option>女</option>
                <option>不详</option> 
        </datalist>
        <input type="submit">
    </form>
    部分类型是针对移动设备生效的，且具有一定的兼容性，在实际应用当中可选择性的使用。
    ```
## 多媒体
+ 音频播放
    - HTML5通过`<audio>`标签来解决音频播放的问题。
    - 并且可以通过附加属性可以更友好控制音频的播放，如：
        + autoplay 自动播放
        + controls 是否显不默认播放控件
        + loop 循环播放
        + preload 预加载 同时设置autoplay时此属性失效
        + 有的音频格式不支持
        ```
        <audio src="music/小手拍拍.mp3" preload loop controls>不支持</audio>
        ```
+ 视频播放
    - HTML5通过`<video>`标签来解决音频播放的问题。
    - 同样，通过附加属性可以更友好的控制视频的播放
        + autoplay 自动播放
        + controls 是否显示默认播放控件，不添加的话就没有视频控件，这样就不能播放了。但是可以自定义视频控件。
        + loop 循环播放
        + preload 预加载，同时设置了autoplay，此属性将失效
        + width 设置播放窗口宽度
        + height 设置播放窗口的高度
        + 但是有的视频格式不支持
```
<audio src="music/小手拍拍.mp3" preload loop controls>不支持</audio>
<audio>
    <source src="music/小手拍拍.mp3">
    <source src="music/小手拍拍.wav">
    <source src="music/小手拍拍.ogg">
</audio>
<video src="music/小手拍拍.mp4" width="400" height="300"></video>
<video src="D:\html基础_录制\01-html基础标签\01-前端开发简介及电脑基本环境配置.wmv" width="400" height="300" controls></video>
<video controls>
    <source src="素材/movie.ogg" type="">
    <source src="素材/movie.mp4" type="">
    您的浏览器不支持
</video>
```
## DOM扩展
+ 获取元素
    - `document.querySelector(‘div’)`html5新选择器，参数是css选择器参数,选择选中的第一个
    - `document.querySelectorAll('selector')`  选择多个
    ```
    // 使用css选择器即可
    var d1_1 = document.querySelector('.box .d1');
    // 返回集合
    var lis = document.querySelectorAll('.ul .li-item');
    ```
+ 类名操作
    - Node.classList.add('class') 添加class
    - Node.classList.remove('class') 移除class
    - Node.classList.toggle('class') 切换class，有则移除，无则添加
    - Node.classList.contains('class') 检测是否存在class
    ```
    <h2 class="title">欢迎来到不凡学院!</h2>
	<button class="btn1">添加红色</button>
	<button class="btn2">删除红色</button>
	<button class="btn3">变为斜体</button>
	<button class="btn4">恢复正常</button>
	<button class="btn5">toggle颜色</button>
	<script>
		var h2 = document.querySelector('h2');
		var btn1 = document.querySelector('.btn1');
		var btn2 = document.querySelector('.btn2');
		var btn3 = document.querySelector('.btn3');
		var btn4 = document.querySelector('.btn4');
		var btn5 = document.querySelector('.btn5');

		// 1、Node.classList.add('class') 添加class
		// 2、Node.classList.remove('class') 移除class
		// 3、Node.classList.toggle('class') 切换class，有则移除，无则添加
		// 4、Node.classList.contains('class') 检测是否存在class

		btn1.onclick = function(){
			h2.classList.add('danger');
		}
		btn2.onclick = function(){
			h2.classList.remove('danger');
		}
		btn5.onclick = function(){
			console.log(h2.classList.contains('danger'));
			h2.classList.toggle('danger');
		}
	</script>
    ```
+ 自定义属性
    - 在HTML5中我们可以自定义属性，其格式如下data-*=""，例如：
    - data-info="我是自定义属性"，通过`Node.dataset['info']` 我们便可以获取到自定义的属性值。
    - `Node.dataset`是以类对象形式存在的
    - 当我们如下格式设置时，则需要以驼峰格式才能正确获取
      `data-my-name="mm"`，获取`Node.dataset['myName']`
    ```
    <body>
        <!-- data-xx 形式可以在标签内部追加不同的内容  -->
        <button data-color="blue" data-text="今天郑州天气晴朗万里无云" class="btn news">新闻</button>
        <button data-color="pink" data-text="今天詹姆斯得了世界杯冠军" class="btn sports">体育</button>
        <button data-color="yellow" data-text="今天金正恩去越南开心" class="btn pol">政治</button>
        <p class="content">
            
        </p>
        <script>
            var news = document.querySelector('.news');
            var stports = document.querySelector('.sports');
            var pol = document.querySelector('.pol');
            var btns = document.querySelectorAll('.btn');
            var target = document.querySelector('.content')
            for(var i = 0 ; i < btns.length ; i ++){
                btns[i].onclick = function () {
                    console.log(this)
                    //可以通过标签对象.dataset获取自定义属性的值
                    target.style.backgroundColor = this.dataset.color;
                    target.innerText = this.dataset.text;
                }
            }

        </script>
    </body>
    ```
## html5新增API
+ 多媒体
#### 也可以自定义视频控件，不要写这个属性`controls`就没有视频控件。
    - 方法
        + load() 加载
        + play() 播放
        + pause() 暂停
    - 属性
		+ currentTime 视频播放的当前进度，读写属性，可以给他写值
        + duration:视频的总时间
        + paused:视频播放的状态.
    - 事件
        + oncanplay: 事件在用户可以开始播放视频/音频（audio/video）时触发。
        + ontimeupdate:通过该事件来报告当前的播放进度.
        + onended:播放完时触发
```
<video class="vd1" src="movie.ogg"></video>
<button class="btn1" onclick="play()">播放</button>
<button class="btn2" onclick="pause()">暂停</button>
<script>
    var vd1El = document.querySelector('.vd1');
    function play(){
        vd1El.play();
    }
    function pause(){
        vd1El.pause();
    }
    vd1El.oncanplay = function(){
        console.log(vd1El.duration)
    }
    vd1El.ontimeupdate = function(){
        console.log(vd1El.currentTime);   
    }
    vd1El.onended = function(){
        console.log('jieshu')
    }
</script>
```
+ 拖拽
    - 在HTML5的规范中，我们可以通过为元素增加draggable="true"来设置此元素是否可以进行拖拽操作，其中图片、链接默认是开启的。
    - 拖拽元素
        + 页面中设置了draggable="true"属性的元素
    - 目标元素
        + 页面中任何一个元素都可以成为目标元素
    - 事件监听
        + 拖拽元素
        + ondrag 		应用于拖拽元素，整个拖拽过程都会调用
        + ondragstart	应用于拖拽元素，当拖拽开始时调用
        + ondragleave	应用于拖拽元素，当鼠标离开拖拽元素时调用
        + ondragend	应用于拖拽元素，当拖拽结束时调用
        + 目标元素
        + ondragenter	应用于目标元素，当拖拽元素进入时调用
        + ondragover	应用于目标元素，当停留在目标元素上时调用
        + ondrop		应用于目标元素，当在目标元素上松开鼠标时调用
        + ondragleave	应用于目标元素，当鼠标离开目标元素时调用
```
<div class="d1" draggable="true"></div>
<div class="d1" draggable="true"></div>
<div class="d1" draggable="true"></div>
<div class="d1" draggable="true"></div>
<div class="d1" draggable="true"></div>
<div class="box"></div>
<script>
    var d1El = document.querySelectorAll('.d1');
    var boxEl = document.querySelector('.box');
    var tempDiv  = null;
    for(var i = 0 ;i < d1El.length ; i++){
        d1El[i].ondragstart = function(){
            tempDiv = this;
        }
    }
    //无法触发ondrop事件 阻止默认，HTML不允许两个标签在一起。
    boxEl.ondragover = function(e){
        e.preventDefault();
        console.log('ondragover')

    }
    boxEl.ondrop = function(){
        this.appendChild(tempDiv);
        console.log('ondrop')
    }
</script>
```
## Web存储
#### 随着互联网的快速发展，基于网页的应用越来越普遍，同时也变的越来越复杂，为了满足各种各样的需求，会经常性在本地存储大量的数据，传统方式我们以document.cookie来进行存储的，但是由于其存储大小只有4k左右，并且解析也相当的复杂，给开发带来诸多不便，HTML5规范则提出解决方案。Storage 存储, window.sessionStorage,window.localStorage(向本地保存数据,有可能在浏览器内存里面，有可能在硬盘上面.)
+ 特性
    - 设置、读取方便
    - 容量较大，sessionStorage约5M、localStorage约20M
    - 只能存储字符串，可以将对象JSON.stringify() 编码后存储
+ window.sessionStorage
    - 生命周期为关闭浏览器窗口
    - 在同一个窗口下数据可以共享
+ window.localStorage
    - 永久生效，除非手动删除
    - 可以多窗口共享
+ 方法详解
    -setItem(key, value) 设置存储内容
    -getItem(key) 读取存储内容
    -removeItem(ke   -y) 删除键值为key的存储内容
    -clear() 清空所有存储内容
    -key(n) 以索引值来获取存储内容
+ 例子是记住用户名和密码



    









