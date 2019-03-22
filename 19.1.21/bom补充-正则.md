---
title: 正则表达式
---
# 正则表达式
## 正则表达式概述
#### 正则表达式，又称规则表达式。（英语：Regular Expression，在代码中常简写为regex、regexp或RE），计算机科学的一个概念。正则表通常被用来检索、替换那些符合某个模式(规则)的文本。正则表达式是对字符串操作的一种逻辑公式，就是用事先定义好的一些特定字符、及这些特定字符的组合，组成一个“规则字符串”，这个“规则字符串”用来表达对字符串的一种过滤逻辑。给定一个正则表达式和另一个字符串，我们可以达到如下的目的：1. 给定的字符串是否符合正则表达式的过滤逻辑（称作“匹配”）；2. 可以通过正则表达式，从字符串中获取我们想要的特定部分。由于正则表达式主要应用对象是文本，因此它在各种文本编辑器场合都有应用。如：表单验证、高级搜索。
## 正则表达式的特点
+ 灵活性、逻辑性和功能性非常的强；
+ 可以迅速地用极简单的方式达到字符串的复杂控制。
+ 对于刚接触的人来说，比较晦涩难懂。 
+ 就算会写，写的过程没问题，写完再看几乎不认识。
比如：匹配国内电话号码：`\d{3}-\d{8}|\d{4}-\d{7}`
验证手机号：`/^((13[0-9])|(15[^4,\D])|(18[0,5-9]))\d{8}$/ `  很难记住。
## 正则表达式声明
+ 通过直接量定义
    - var 变量名= /表达式/`var qqReg = /^[1-9][0-9]{4,10}$/;`
+ 方法
    - `test()` 正则对象方法，检测测试字符串是否符合该规则，返回true和false，参数（测试字符串） 
    - 语法格式:`Boolean = reg.test(str);`
    ```
    var reg = /./;
    var reg2 = /\d/;
    var reg3 = /\D/;
    var reg4 = /\w/;
    var reg5 = /\W/;
    console.log(reg.test('asdfasdf'));
    console.log(reg2.test('1234abc')); //true? 匹配 
    console.log(reg3.test('1234'));
    console.log(reg4.test('*+'));
    console.log(reg5.test('*+'));
    ```
    - `replace()`用于在字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串。
    - 语法格式：(返回值是新字符串)`Str.replace（reg,new）;`正则表达式的匹配模式支持的2个标志。
 	    + g：表示全局模式（global），即模式将被应用于所有字符串而非发现一个而停止
        + i：表示不区分大小写（ease-insensitive）模式，在确定匹配想时忽略模式与字符串的大小写
    ```
    var str1 = 'abcdefgabc';
    var str2 = 'abcdefgabcABc';
    // 注意: replace并不能修改原来的值
    // replace 只能替换第一次出的值
    // 如何实现一个replaceAll的作用
    var s1 = str1.replace('abc','123');
    // replace可以接收一个正则表达式
    // g global 全局匹配
    // i ignore  忽略大小写
    var reg = /abc/gi;
    var s2 = str2.replace(reg,'123'); 
    console.log(s1);
    console.log(s2);
    ```
+ 正则内部类
    - 预定义类
        + ^如果出现在正则规则第一位 是以**开始的意思，如果出现在正则中间，表示取非 。   
        + `.` [^\n\r] 除了换行和回车之外的任意字符（“”不行）
        + `\d`	 [0-9]  数字字符
        + `\D`	[^0-9]	非数字字符
        + `\s`  [ \t\n\x0B\f\r]	 空白字符 
        + `\S`	[^ \t\n\x0B\f\r] 非空白字符
        + `\w`	[a-zA-Z_0-9] 单词字符   字母数字下划线（注册要求用户名）
        + `\W`	[^a-zA-Z_0-9] 非单词字符  
    - 简单类
        + `//`中什么特殊符号都不写，和[]的加入；
        + `/abc/.test(“abc”);`      一个规则对一个字符       
   	    + `/[abc]/.test(“abcd”);`   一个[***]对一个字符
    - 负向类
        + 中括号内，前面加个元字符^进行取反，不是括号里面的字符（一部分也不行）。
    ```
    // 用于匹配字符串中是否包含abc的字符
    var reg = /abc/;
    var reg2 = /a/;
    // 只能匹配一位
    var reg3 = /[abc]/;
    var reg4 = /[^abc]/; //取非
    console.log(reg.test('abc'));  //true
    console.log(reg.test('abcde')); // true
    console.log(reg.test('ab')); // false
    console.log(reg.test('aebc')); // false
    console.log(reg3.test('aebc')); //  true
    console.log(reg3.test('ab')); //  true
    console.log(reg4.test('ab')); //  false
    console.log(reg4.test('aebc')); // true
    ```
    - 范围类
        + 比如a-z,0-9`console.log(/[a-z]/.test('1234'));`
    - 组合类
        + 用中括号匹配不同类型的单个字符。`console.log(/[a-f5-9]/.test("123"))`
	- 正则边界（重点）
        + ^ 会匹配行或者字符串的起始位置
        + $ 会匹配行或字符串的结尾位置
        + 注：^在[]中才表示非！这里表示开始
        + ^$在一起 表示必须是这个（精确匹配）
    ```
    var reg = /[a-z]/;
    var reg2 = /[0-9]/;
    // 第一位字符3-5,第二位字符a-c
    var reg3 = /[3-5][a-c][1]/;
    // ^ 开始 ; $ 结尾
    var reg4 = /^[3-5][a-c][1]$/;
    // ^在[]中才表示非！
    var reg5 = /^[^3-5][a-c][1]$/;
    console.log(reg.test('z'));
    console.log(reg2.test('9'));
    console.log(reg3.test('23fa'));
    console.log(reg3.test('23a1'));
    console.log(reg4.test('3b1')); // true
    console.log(reg4.test('c3b1')); // false
    console.log(reg5.test('3b1')); // false
    ```
