dom操作
======
JavaScript中textContent、innerText和innerHTML的用法以及区别
-------------------------------------
> innerHtml

暴力添加dom节点---innerHTML→非w3c标准但主流浏览器都支持

```js
<body>
<input type="button" value="按钮" id="btn">
<div id="dv">这是一个div</div>
<script>
  document.getElementById("btn").onclick = function () {
    // 通过textContent给dom节点设置文本内容
    document.getElementById("dv").textContent = "改变了";
    // 通过innerText给dom节点设置文本内容
    document.getElementById("dv").innerText = "改变了";
    // 通过innerHTML给dom节点设置文本内容
    document.getElementById("dv").innerHTML = "改变了";
    // textContent获取节点文本内容
    var value = document.getElementById("dv").textContent
    // innerText获取节点文本内容
    var text = document.getElementById("dv").innerText;
    // innerHTML 获取节点文本内容
     var textVal = document.getElementById("dv").innerHTML;
  };
</script>
</body>
```
> innerText和textContent的区别:
* 设置标签中的文本内容,应该使用textContent属性,谷歌,火狐支持,IE8不支持
* 设置标签中的文本内容,应该使用innerText属性,谷歌,火狐,IE8都支持
* 如果这个属性在浏览器中不支持,那么这个属性的类型是undefined
* 判断这个属性的类型 是不是undefined,就知道浏览器是否支持

> innerText和innerHTML的区别
* 如果使用innerText主要是设置文本内容,设置标签内容是没有标签的效果的
* innerHTML是可以设置文本内容
* innerHTML主要的作用是在标签中设置新的html标签内容,是有标签效果的
* 想要设置标签内容,使用innerHTML,想要设置文本内容,innerText或者textContent,或者innerHTML,推荐用innerHTML
* innerText可以获取标签中间的文本内容,但是标签中如果还有标签,那么最里面的标签的文本内容也能获取.---获取不到标签的,文本可以获取
* innerHTML才是真正的获取标签中间的所有内容

[参考链接](https://blog.csdn.net/tswc_byy/article/details/82711093)

css篇
=====
vertical-align
--------------
> vertical-align 属性设置元素的垂直对齐方式。
[参考链接](https://www.w3school.com.cn/css/pr_pos_vertical-align.asp)



box-sizing的使用场景:
--------------------
值       | 描述    
---------|-----------
content-box: | 宽度和高度分别应用到元素的内容框。在宽度和高度之外绘制元素的内边距和边框。
border-box: | 为元素设定的宽度和高度决定了元素的边框盒。就是说，为元素指定的任何内边距和边框都将在已设定的宽度和高度内进行绘制。通过从已设定的宽度和高度分别减去边框和内边距才能得到内容的宽度和高度
inherit: | 规定应从父元素继承 box-sizing 属性的值。
[参考链接](https://www.w3school.com.cn/cssref/pr_box-sizing.asp)
[参考链接](https://www.cnblogs.com/maxueting/p/11162344.html)

js篇
====
onmousemove, onmouseleave 和 onmouseout 的区别。
----------------------------------------------
> onmouseleave: 事件在鼠标移出元素时触发。
> onmouseleave: 类似于onmouseout事件。 唯一的区别是 onmouseleave事件不支持冒泡
[参考链接](https://www.runoob.com/try/try.php?filename=tryjsref_onmousemove_leave_out)
[参考链接](https://www.runoob.com/jsref/event-onmouseleave.html)


js对象的深拷贝
------------

[参考链接](https://blog.csdn.net/lyt_angularjs/article/details/86599820)
[参考链接](https://www.cnblogs.com/renbo/p/9563050.html)

数组相关
-------
```js
Array.prototype.afterArray=function(){
  console.log('this=',this);
  this.splice(0,1);
};
arr=[1,1,1,5,1,1,1,6];
for (var i=0;i<arr.length;i++) {
  console.log('前arr=',arr);
  console.log('i=',i);
  console.log('arr.length=',arr.length);
  console.log('arr[i]=',arr[i]);
  if (arr[i] === 1) {
      arr.afterArray();
  }
  console.log('后arr=',arr);
}
```

对象地址不是值(容易出错)
------------------
```js
const obj = {
  name: 'momo',
  age: 22,
}
const cc = [obj];
const arr = [...cc];
const yrr = [...cc];
obj.address ='漕宝路120号'
console.log('arr===yrr', arr===yrr)//arr===yrr false
console.log('arr', arr)//
console.log('yrr', yrr)//
```
> 解析 : 虽然arr和yrr是不同的数组,但是arr和yrr里的第一个元素共用同一个对象索引,所以arr和yrr打印出含有address信息的数组;

window对象的子对象
-----------------

> Bom模型: 浏览器 对象 模型

> window.document: Dom模型;
* window对象是最大的对象,所有对象都在其内部;
* 因此写document默认就是在最全局的window对象或子对象；

```js
window.navigator :表示浏览器的相关信息；
  navigator对象的属性
    appCodeName:浏览器的代码名(例如,Mozilla)；
    appName:浏览器名称；
    appVersion:浏览器版本;
    userAgent：用户代理信息;//由客户机送到服务器的用户与代理头标文本
    cookieEnabled:是否支持cookie;
    platform:返回运行浏览器的操作系统平台。(不好用)
    cpuClass:获取平台cpu（兼容性差）

  用法：window.navigator.appName | navigator.appName
```

```js
window.screen:表示分辨率信息；
  screen对象的属性;
      width:
      height:
      availWidth:可用宽分辨率；
      availHeight:可用高分辨率；
  用法：screen.width;
```

```js
window.location:地址栏，可以控制页面跳转;
  location对象的属性;
    host: 主机
    port: 端口
    href: 地址
    pathname：路径
    protocol：协议
    search：查询字符串
    assign(url):页面跳转
  用法:
    1.获取当前地址  location.href;2.location.href="http://www.baidu.com"
```

```js
window.history:历史记录,控制前进后退；
  history对象的属性：
    length: 历史记录的条数(指窗口上的历史记录)；
    back: 后退；
    forward: 前进；
    go(number);

  用法：history.length;
    history.forward(1);
    history.go(1);
  
  从哪里进入回退到哪里
    window.history.go(-1);
    window.history.back();
    // window.history.back(-1)
```

### 字符串和数字相加
  ```js
  console.log(1+2); // 3
  console.log('1'+'2'); // 12
  console.log('1'+ 2); // 12  
  console.log(1+ '2'); // 12 
  ```
> 除了数字与数字相加是数字以外，其余情况相加都是字符串

parseInt()和Number()比较
-----------------------

[参考链接](https://wangdoc.com/javascript/types/number.html)
```js
console.log(parseInt('12'));// 12
console.log(parseInt('a12'));// NaN
console.log(parseInt('12a'));// 12
console.log(parseInt('0xA'));// 10
```

```js
console.log(Number('12'));// 12
console.log(Number('a12'));// NaN
console.log(Number('12a'));// NaN
console.log(Number('0xA'));// 10
```
**parseInt() 解析的是部分字符串，而 Number 解析的是整个字符串**
[参考链接](https://blog.csdn.net/extendworld/article/details/78909352)

```js
new Number(value); 
var a = new Number('123'); // a === 123 is false
var b = Number('123'); // b === 123 is true
a instanceof Number; // is true
b instanceof Number; // is false
```
应用场景:
* 如果参数无法被转换为数字，则返回 NaN。
* 在非构造器上下文中 (如：没有 new 操作符)，Number 能被用来执行类型转换。

```js
console.log(new Number('123').valueOf());// 123
console.log(new Number('123')); //Number {123}
console.log(Number('123')); // 123 //不需要使用valueOf()方法
console.log(Number(null)); // 0
console.log(Number(undefined)); // NaN
console.log(5 + null) // 5
console.log(5 + undefined) // NaN
console.log(null == undefined) // true
console.log(null === undefined) // false
console.log(new Number().valueOf() === 0); // true
console.log(Number() === 0); // true
```
[参考链接](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number)

[参考链接- null | undefined](https://wangdoc.com/javascript/types/null-undefined-boolean.html)

toString()和String()区别
-----------------------
```js
let a;
let b = null;
a.toString() //Uncaught TypeError: Cannot read property 'toString' of undefined
b.toString() //Uncaught TypeError: Cannot read property 'toString' of null
String(a) // "undefined"
String(b) // "null"
```
|  属性 | 描述
|:------|:-----
|相同点: | 都是将其他类型的变量转换为字符串变量
|不同点: | toString() 无法转换null和undefined

一句话知识
---------
|知识点   |
|:-------|
|伪元素::before ::after 与content配合使用，其实属于行内元素；
|行内元素和内联元素是一个东西；叫法不一样而已
|input属于内联块元素 inline-block
|button属于内联块元素 inline-block
|a属于内联元素 inline
|https默认端口号: 443;
|http默认端口号: 80;

[HTTP、HTTPS常用的默认端口号](https://blog.csdn.net/ypt523/article/details/79636647)


```js
html::-webkit-scrollbar {
  border-width: 1px;
}
```
可以实现去除滚动条，但是保留占位；

es6
===
```js
var a = [];
for (var i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i);
  };
}
a[6](); // 10
```
上面代码中，变量i是var命令声明的，在全局范围内都有效，所以全局只有一个变量i。每一次循环，变量i的值都会发生改变，而循环内被赋给数组a的函数内部的console.log(i)，里面的i指向的就是全局的i。也就是说，所有数组a的成员里面的i，指向的都是同一个i，导致运行时输出的是最后一轮的i的值，也就是 10。

如果使用let，声明的变量仅在块级作用域内有效，最后输出的是 6。
```js
var a = [];
for (let i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i);
  };
}
a[6](); // 6
```
另外，for循环还有一个特别之处，就是设置循环变量的那部分是一个父作用域，而循环体内部是一个单独的子作用域。
```js
for (let i = 0; i < 3; i++) {
  console.log('ss', i);
  let i = 'abc';
  console.log('abc', i);
}
// abc
// abc
// abc
```
上面代码正确运行，输出了 3 次abc。这表明函数内部的变量i与循环变量i不在同一个作用域，有各自单独的作用域。

> 解构

```js
const cc = {name: 'Zhongshan', obj: {age: 12}};
const {name: myName, obj: myObj} = cc;
console.log(myName) // 'Zhongshan'
console.log(name) // ''
console.log(obj) // Uncaught ReferenceError: obj is not defined
console.log(myObj) // {age: 12}
```

React篇
========
react-transition-group 一个官网提供的动画过度库。
---------------------------------------------

[参考链接](https://github.com/kk412027247/react-turntable)
[参考链接](https://segmentfault.com/a/1190000015487495)


何时使用Component还是PureComponent？
---------------------------------
> 大部分功能相同  

> PureComponent通过prop和state的浅比较来实现shouldComponentUpdate

> 某些情况下可以用PureComponent提升性能(PureComponent最佳情况是展示组件)

> 如果prop和state每次都会变，那么PureComponent的效率还不如Component，因为你知道的，进行浅比较也是需要时间

> 若有shouldComponentUpdate，则执行它，若没有这个方法会判断是不是PureComponent，若是，进行浅比较

[参考链接(简书)](https://www.jianshu.com/p/b7733dc8f826)
[参考链接](https://segmentfault.com/a/1190000014979065)

React创建组件的三种方式及其区别
----------------------------
| 索引 | 描述
:------:|-----
1 | 函数式定义的无状态组件
2 | es5原生方式React.createClass定义的组件
3 | es6形式的extends React.Component定义的组件

**函数式定义的无状态组件:**
创建无状态函数式组件形式是从React 0.14版本开始出现的。它是为了创建纯展示组件，这种组件只负责根据传入的props来展示，不涉及到要state状态的操作。

**官网介绍**
在大部分React代码中，大多数组件被写成无状态的组件，通过简单组合可以构建成其他的组件等；这种通过多个简单然后合并成一个大应用的设计模式被提倡。

| 优势  | 描述
:-------|-----
1 | 组件不会被实例化，整体渲染性能得到提升
2 | 组件不能访问this对象
3 | 组件无法访问生命周期的方法
4 | 无状态组件只能访问输入的props，同样的props会得到同样的渲染结果，不会有副作用

[参考链接](https://www.jianshu.com/p/214f4d5d178f)

componentWillUnmount使用场景:
---------------------------
> 在组件被卸载的和销毁之前立即调用； 包括切换路由；在此方法内实现必要的清理，例如使计时器无效，取消网络请求，删除监听事件。

react 16版本新特性
-----------------
> 抛弃了一些生命周期
 * componentWillMount
 * componentWillReceiveProps
 * componentWillUpdate

> getDerivedStateFromProps

> getSnapshotBeforeUpdate

[参考链接](https://www.jianshu.com/p/50fe3fb9f7c3)
Error
==========
> Unnecessary semicolon  [ˈsɛmɪˌkolən] 不必要的分号;

> Component should use es6 class instead of createClass (react/prefer-es6-class)

快捷键
=====
> Ctrl+Shift+Esc 打开任务管理器  

> Win+X 打开控制面板


Git命令
======
* git status查看本地修改与服务器的差异。 
* git add . 将这些差异文件添加，这样就可以提交了。  
* git commit –m '这里是注释'提交更改到服务器。  
* git checkout master更改到master库。  
* git pull将服务器最新的更改获取到本地。  
* git merge local master将本地的local合并到远程的master上。
* git push origin master正式提交到远程的master服务器上。  

[参考链接](http://blog.csdn.net/dengsilinming/article/details/8000622)

> 打印安装日志到console
- npm install --loglevel silly  

GitBash
-------
> [bash快捷键命令](http://www.2cto.com/os/201310/248101.html)   

> [粘贴：Fn+Insert](http://jingyan.baidu.com/article/b2c186c8d64f7ec46ef6ff1a.html)

linux常用命令：
============
- mkdir 文件夹名 :这个是新建文件夹的命令  
- vi   以编辑的模式进入文件，如果没有相应的文件名则先创建这个文件，然后编辑模式；(如果不能编辑,按下i键试一下)编辑完成按esc键退出然后再输入如下命令;  
- :wq  保存并退出;:wq!  
- :q!  不保存并退出;  
- cat :由第一行开始显示文件内容  
- head：只看前几行；  
- tail：只看最后几行；
- rm -rf 目录名字:删除文件夹以及文件夹中的所有文件命令    
- rm -f 文件名:删除文件命令    
- rm 文件名:删除当前目录下的文件(注意：此操作不会把文件放到回收站而是直接删除)   
- pwd 指显示当前的路径;  
- ll  查看当前目录下的文件目录(详细信息);  
- ls  指查看当前目录下的目录;  
- ls -lh  # human readable,以 k/M 显示大小  
- ls -alh 查看当前目录下的文件(包括隐藏文件及文件夹);  
- ll –t  当前目录按时间顺序显示文件；  
- cd  ..  是返回上一级目录的意思；  
- cp /tmp/xxx.html  ./yyy.html :这个命令的意思是说把tmpt  目录下的xxx.html 文件copy到当前目录下并且把名字改为yyy.html 
- sudo 命令 后面一定要跟绝对路径  
- $PWD 是通配符  
- clear: 清屏命令,不是真正意义上的清屏.  