---
title: css3
---
# css3
## css私有化前缀
+ 因为css3出现后 浏览器并不能统一所有针对新属性 不同的浏览器需要添加不同的前缀使其生效.(但是现在好像不太需要)
    - webkit chrome浏览器内核
	- moz  火狐
	- ms ie内核
	- o 欧朋浏览器
    ```
    //圆角，radius半径
    -webkit-border-radius: 4px;
    -moz-border-radius: 4px;
    -ms-border-radius: 4px;
    -o-border-radius: 4px; 

    ```
    - 半个椭圆写法，百度可以查到
    ```
    border-radius: 50% / 100% 100% 0 0;
    ```
## css3新增选择器
+ 属性选择器
    - 其特点是通过属性来选择元素，具体有以下5种形式
    - div[attr]
    - div[attr=mydemo]
    - div[attr*=mydemo]   //任意位置
    - div[attr^=mydemo]  //开始位置
    - div[attr$=demos]  //结束位置
```
	<style>
		/*可以选中具有title属性的p1*/
		/*属性选择器是补充作用,一般用[]*/
		.p1[title="p-1"]{
			color: blue;
		}
		.p1[title]{
			font-size: 30px;
		}
		/*title以p开始的属性*/
		.p1[title^="p"]{
			background-color: yellow;
		}
		/*属性选择器 在表单用的多一点*/
		input[name="age"]{
			color: red;
		}
	</style>

    <body>
        <p class="p1" title="p-1">这是p1</p>
        <p class="p1">这是p1</p>
        <p class="p1" title="p-2">这是p1</p>
        <input type="text" name="username">
        <input type="text" name="age">
    </body>
```
+   伪类选择器
    - 结构伪类
        + 重点通过E来确定元素的父元素。
        + E:first-child第一个子元素
        + E:last-child最后一个子元素
        + E:nth-child(n) 第n个子元素
        + E:nth-last-child(n) 同E:nth-child(n) 相似，只是倒着计算；
    ```
    //n是支持简单表达式的
    li:nth-child(2n-1){
    color: red;
    }
    //n<0时无效
    //选中所有的4 的倍数的li 
    li:nth-child(4n){
        color: red;
        }
    //选中前面五个
    li:nth-child(-1n+5){
        color: red;
        }
    //选中后面五个
    li:nth-last-child(-1n+5){
        color: red;
    }
    //所有的偶数
    li:nth-child(even){
        color:red
    }
    //所有的奇数
    li:nth-child(odd){
        color:blue;
    }
    //n可是多种形式：nth-child(2n)、nth-child(2n+1)、nth-child(-1n+5)等；
    //E:empty 选中没有任何子节点的E元素；注意，无法选择有空格或者回撤的标签

    ```
    - 目标伪类
        + E:target 结合锚点进行使用，处于当前锚点的元素会被选中；
        ```
        <a href="#li3">点我</a>
        <li id="li3">li3</li>
        li:target{
                font-size: 30px;
                color: blue;
        }
        ```
+ 伪元素（伪标签）选择器
    - 是一个行内元素，需要转换成块元素
    - E:after、E:before 在旧版本里是伪类，在新版本里是伪元素，新版本E:after、E:before会被自动识别为E::after、E::before，按伪元素来对待，这样做的目的是用来做兼容处理。
    - 伪标签 在js中不能被选中
    - E::first-letter文本的第一个字母或字；
    - E::first-line 文本第一行；  文本第一行高亮..
    - E::selection 可改变选中文本的样式；
    - `content``伪元素多的属性可以用来添加内容，但是鼠标光标不能选中
    - 用于清除浮动,在这个元素after写上`clear:both;`
    ```
    .clear::after{
        content:'';
        /*转换为块状元素*/
        display:block;
        clear:both;
        height:0;
        overflow:hidden;
        visibility:hidden;
    }
    ```
    - 僚机，这个元素的after和before，可以加样式和动画。
## 颜色
+ 一种新增的颜色表达方式
+ Red、Green、Blue、Alpha（透明度）即RGBA
+ Hue（色调）、Saturation（饱和度）、Lightness（亮度）、Alpha（透明度）即HSLA
+ 关于透明度
    - opacity只能针对整个盒子设置透明度，子盒子及内容会继承父盒子的透明度；
    - transparent 不可调节透明度，始终完全透明；
    - 什么时候用
        + 一般元素透明用opacity
        + 遮罩层rgba背景透明
        + 制作三角的时候用transparent
    - 制作三角形:写一个元素给他加上很宽的边框，然后让元素的长宽为0，就只剩边框了，让其中三个边框变透明就成了三角形了。
    ```
    .an{
        width: 0px;
        height: 0px;
        /*background-color: pink;*/
        margin: 100px;
        border: 90px solid transparent;
        /*border-right-color: green;*/
        border-bottom-color: yellow;
        /*border-left-color: purple;*/
		}

    ```
## 阴影
+ 文本：text-shadow，可分别设置偏移量、模糊度、颜色（可设透明度）。
    - 水平偏移量 正值向右 负值向左；
    - 垂直偏移量 正值向下 负值向上；
    - 模糊度是不能为负值；
    - 可以有多个影子，用逗号隔开
    - 在后面写上`inset`就可以变成内阴影；
    - 案例：浮雕文字
    ```
    .tu{
	     text-shadow: -1px -1px 1px #fff, 1px 1px 1px #000;
    }
    .ao{
        text-shadow: -1px -1px 1px #000, 1px 1px 1px #fff;
    }
    .d2:hover{
			/*内阴影*/
        box-shadow: 20px 20px 0 0 blue inset,-20px -20px 0 0 blue inset;
    
		}
    ```
+ 盒子：box-shadow
    - blur： 模糊半径
    - spread:  扩展范围
    - color: 颜色
    - 案例：扔在桌子上的图片
    ```
    .pic{
        width: 200px;
        height: 200px;
        margin-left: 100px;
        border: 30px solid #e5e5e5;
        transform: rotate(30deg);
        box-shadow: 0 40px 30px -20px rgba(0,0,0,.5);

    }
    <img class="pic" src="m1.jpg" alt="">

    ```
## 盒子模型
+ 用box-sizing 来指定盒模型，他有两个属性，content-box、border-box。
+ content-box:对象的实际宽度等于设置的width值和border、padding之和
+ border-box： 对象的实际宽度就等于设置的width值，即使定义有border和padding也不会改变对象的实际宽度，即 ( Element width = width ) 。
## 边框
+ 边框图片
    - 设置的图片将会被“切割”成九宫格形式，然后进行设置；
    - 一种比较特别难写的格式，有一种生成器可以用。
## 渐变
+ 线性渐变
    - `linear-gradient`线性渐变指沿着某条直线朝一个方向产生渐变效果。
    ```
    background: linear-gradient(direction, color-stop1, color-stop2, ...);
    ```
    - 有的浏览器不兼容，所以需要兼容写法。兼容写法格式和正常的格式不太一样。
    ```
    .d1{
        width: 400px;
        height: 400px;
        /*background: linear-gradient(direction, color-stop1, color-stop2, ...);*/
        /*1.方向 正常需要写 to xx*/
        background: linear-gradient(to right,red,orange,yellow,green,#004400,blue,purple);
        /*如果存在兼容属性 只需要实现正常写法和chrome/mac写法*/
        /*1. 线性渐变 -webkit-兼容: 1 方向不能带to;2方向和正常写法相反*/
        background: -webkit-linear-gradient(left,red,orange,yellow,green,#004400,blue,purple);
    }
    ```
    - 也可以写角度，就是开始渐变的角度,百分数是写这个渐变从块的哪个（20%）位置开始变，到哪里（50%）结束渐变；
    ```
    background: linear-gradient(45deg,red 20%,green 50%);

    ```
    - 也可以写一种重复效果，但是真的比较丑
    ```
    //在10%到30%之间红色和绿色渐变；
    background: repeating-linear-gradient(red 10%,green 30%);

    ```
+ 径向渐变
    - `radial-gradient`径向渐变指从一个中心点开始沿着四周产生渐变效果,是一个圆的效果。
    ```
    background: radial-gradient(center, shape size, start-color, ..., last-color);
    ```
    - 不兼容，必须设置私有化前缀
    ```
    //百分数代表了中心点的位置，后面也可以写很多颜色，实现多颜色的渐变。
    background: radial-gradient(20% 20%,red,green);
    background: -webkit-radial-gradient(20% 20%,red,green);
    ```
## 背景
+ 背景在CSS3中也得到很大程度的增强，比如背景图片尺寸、背景裁切区域、背景定位参照点、多重背景等。
+ background:url  repeat  position
+ background-image
+ background-size(使用的比较多)
    - 设置背景图片的尺寸,是需要根据高度还是宽度适配.
    - width height 直接设置宽高 百分比
    - cover会自动调整缩放比例，保证图片始终填充满背景区域，如有溢出部分则会被隐藏。
    - contain会自动调整缩放比例，保证图片始终完整显示在背景区域。整个背景图片完整显示在背景区域.
    ```
    background-size: 100% 100%;
    background-size: 400px 400px;
    background-size: content;
    background-size: cover;
    ```
+ background-origin
    - (原点，起点)设置背景定位的原点
    - border-box以边框做为参考原点；
    - padding-box以内边距做为参考原点；
    - content-box以内容区做为参考点；
+ background-clip
    - 设置背景区域clip(裁切)；与background-size比较相似，但是background-size是将图片压缩等使图片完整的显示在盒子里。但是background-clip是裁剪，将图片超出的部分裁剪掉。
    - border-box裁切边框以内为背景区域；
    - padding-box裁切内边距以内为背景区域；
    - content-box裁切内容区做为背景区域；
+ 多背景
    - 就是可以用‘，’分割开多张图片作为背景图片；
    ```
    background: url(img/avatar.jpg) no-repeat 0 0 ,url(img/avatar.jpg) no-repeat 0 200px ;
    ```
## 过渡
+ 过渡是CSS3中具有颠覆性的特征之一，可以实现元素不同状态间的平滑过渡（补间动画），经常用来制作动画效果。
+ transition:param1 param2 
    - param1    要过渡的属性
    - param2    过渡的时间.
+ transition-property设置过渡属性,想要哪个属性产生效果就写哪个属性(直接写就行了)。一般设置`all`所有的属性都可以跟着动。
+ transition-duration设置过渡时间，
+ transition-timing-function设置过渡速度，时间函数，贝塞尔曲线
```
transition-timing-function: cubic-bezier(.2,1.47,.86,-0.58);
```
+ transition-delay设置过渡延时  超过时间后执行动画.就是延迟执行。
+ transform-origin 旋转的中心点
```
transform-origin: center bottom;
```
+ 简写`transition: all ease .4s;`
## 2D转换
+ 缩放 scale(x, y) 可以对元素进行水平和垂直方向的缩放，x、y的取值可为小数，不可为负值；
```
//变成之前的2倍大小，xy相同的时候可以只写一个。
transform: scale(2);
```
+ 移动 translate(x, y) 可以改变元素的位置，x、y可为负值；
```
transform: translate(100px,100px)
```

+ 旋转 rotate(deg) 可以对元素进行旋转，正值为顺时针，负值为逆时针；
```
//旋转360度
transform: rotate(360deg);
```
+ 可以组合起来写，但是组合的顺序不同动画执行的顺序也不同,效果也不同。
```
transform: translate(100px,100px) rotate(360deg) ;

```
## 透视
+ `perspective`电脑显示屏是一个2D平面，图像之所以具有立体感（3D效果），其实只是一种视觉呈现，通过透视可以实现此目的。
透视可以将一个2D平面，在转换的过程当中，呈现3D效果。透视会产生“近大远小”的效果
+ `perspective`有两种写法
    - 作为一个属性，设置给父元素，作用于所有3D转换的子元素;perspective 眼睛的距离
    `perspective: 500px; `设置给父类元素的时候会造成横看成岭侧成峰的效果。
        + 设置给父类元素的时候可以设置视角，不同的视角所呈现的效果也是不同的。默认是在中间。就是left50%和top50%，如果是0 0的话就是做左上角。`perspective-origin: 0 600px ;`
    - 作为transform属性的一个值，做用于元素自身`transform: perspective(500px);`设置给子类的时候会造成透视效果但是不会有横看成林侧成峰的效果。
+ `ransform-style`3D呈现
    - flat：所有子元素在 2D 平面呈现
    - preserve-3d：保留3D空间`transform-style: preserve-3d;`使当前元素转为3d舞台;
+ `backface-visibility：visible/ hidden` 设置元素背面是否可见;默认是visible，展示背面元素。
## 动画
+ 动画是CSS3中具有颠覆性的特征之一，可通过设置多个节点来精确控制一个或一组动画，常用来实现复杂的动画效果。
+ 必要元素
    - 通过@keyframes指定动画序列；
    - 通过百分比将动画序列分割成多个节点；
    - 在各节点中分别定义各属性
    - 通过animation将动画应用于相应元素；
+ 重要属性
    - `animation-name: an1;`动画的名称
    - `animation-duration: 3s;`动画的持续时间
    - `animation-timing-function: ease;`时间函数
    - `animation-delay: 1s;`延迟，只是第一次
    - `animation-iteration-count: 1;`循环次数，infinite无限循环
    - `animation-direction: alternate;`动画是否重置后再开始播放
        + `alternate`动画直接从上一次停止的位置开始执行，倒着来播放。
        + `normal`	动画第二次直接跳到0%的状态开始执行
    - `animation-play-state`播放状态（ `running` 播放 和`paused` 暂停 ）这个可以用于js中的点击事件。
    ```
    btn1.onclick = function () {
        // animation-play-state  播放状态（ running 播放 和paused 暂停 ）
        d1.style.animationPlayState = 'paused';
    }
    btn2.onclick = function () {
        d1.style.animationPlayState = 'running';
    }
    ```
    - `animation-fill-mode: both;`动画执行完毕后状态
        + `forwards`	当动画完成后，保持最后一个属性值（在最后一个关键帧中定义）。
        + `backwards`	在 `animation-delay` 所指定的一段时间内，在动画显示之前，应用开始属性值（在第一个关键帧中定义）。
        + `both`	设置对象状态为动画结束或开始的状态，结束时状态优先
    - 简写方式`animation: an1 3s ease 1s infinite alternate both;`开头和结尾顺序不能乱，持续时间和延迟时间的顺序也不能乱，其他的内容顺序可以打乱。
    ```
    .d1{
        width: 200px;
        height: 200px;
        background-color: green;
        animation-name: an1;
        animation-duration: 3s;
        animation-timing-function: ease;
        animation-delay: 1s;
        animation-iteration-count: 1;
        animation-fill-mode: both;
    }
    /*关键帧,开始和结束必须要有，中间的过程可以写一个和多个，主要看需求*/
    @keyframes an1{
        0%{
            width: 100px;
            height: 100px;
            background-color: red;
            transform: translateX(0) translateY(0);
        }
        50%{
            width: 200px;
            height: 220px;
            background-color: orange;
            transform: translateX(300px) translateY(300px);
        }
        100%{
            width: 50px;
            height: 100px;
            background-color: pink;
            transform: translateX(600px) translateY(0);		
        }
    }
    ```
+ 扭曲`skew`
    - 比较少用`transform: skewX(30deg) skewY(30deg);`
    - skew(x-angle,y-angle)
    - skewX(angle)
    - skewY(angle)

## 动画状态监听
+ 需求：当一个动画执行完毕后 执行另一个动画
```
d1.onclick = function (){
    this.classList.add('an1');	
}

d1.addEventListener('animationstart',function(){
    count ++ ;
    console.log('animationstart');
})
// 动画重复
d1.addEventListener('animationiteration',function(){
    console.log('animationiteration ');
})
d1.addEventListener('animationend',function(){
    if(count ==1){
        console.log('animationend ');
        d1.classList.remove('an1');
        d1.classList.add('an2');
        //移除监听 
    }
    
})
```
+ animationstart - CSS 动画开始后触发
+ animationiteration - CSS 动画重复播放时触发
+ animationend - CSS 动画完成后触发
## 过渡状态监听
+ 只能监听结束`transitionend`
```
d1.addEventListener('transitionend',function () {
    console.log('end...')
})

```

















 












    