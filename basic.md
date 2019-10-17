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

### parseInt()和Number()比较

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

[参考链接](https://blog.csdn.net/extendworld/article/details/78909352)


何时使用Component还是PureComponent？
---

[参考链接](https://segmentfault.com/a/1190000014979065)