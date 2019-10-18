js相关
===
### 字符串和数字相加
  ```js
  console.log(1+2); // 3
  console.log('1'+'2'); // 12
  console.log('1'+ 2); // 12  
  console.log(1+ '2'); // 12 
  ```
  * 除了数字与数字相加是数字以外，其余情况相加都是字符串 

parseInt()和Number()比较
-----------------------

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
* parseInt() 解析的是部分字符串，而 Number 解析的是整个字符串
* [参考链接](https://blog.csdn.net/extendworld/article/details/78909352)

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

```js
html::-webkit-scrollbar {
  border-width: 1px;
}
```
可以实现去除滚动条，但是保留占位；

何时使用Component还是PureComponent？
---------------------------------
[参考链接](https://segmentfault.com/a/1190000014979065)