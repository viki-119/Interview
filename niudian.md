this指向
-------
请说明要输出正确的myName的值要如何修改程序?并解释原因
```js
foo = function() {
	this.myName = "Foo function.";
}
foo.prototype.sayHello = function() {
	alert(this.myName);
}
foo.prototype.bar = function() {
	setTimeout(this.sayHello, 1000);
}
var f = new foo;
f.bar();
```
> 效果:弹出undefined,而非"Foo function.";  
> 出错原因: setTimeout函数中使用的this指向全局作用域;  
> 解决方法：绑定词法作用域中this  
```js
foo=function(){
	this.myName="ssss";
}
foo.prototype.sayHello=function() {
	console.log(this.myName);
}
foo.prototype.bar=function(){
	setTimeout(function (self) {
		return function () {
			self.sayHello();
		}
	}(this),7000)
}
var f=new foo;
f.bar()
```
解决方法二: 使用箭头函数
```js
foo = function() {
	this.myName = "Foo function.";
}
foo.prototype.sayHello = function() {
	alert(this.myName);
}
foo.prototype.bar = function() {
	setTimeout(() => this.sayHello(), 1000);
}
var f = new foo;
f.bar();
```

解决方法三: 使用bind
```js
foo = function() {
	this.myName = "Foo function.";
}
foo.prototype.sayHello = function() {
	alert(this.myName);
}
foo.prototype.bar = function() {
	setTimeout(this.sayHello.bind(this), 1000);
}
var f = new foo;
f.bar();
```
[参考链接](http://zhidao.baidu.com/link?url=zBRGLszzd7s7B-C8yNYCk6y03GJ63rlp-Wte27GdYiEeARCrLSSkcsNhKf4WV5lK2UeVJHgzghELVjsKJbtU9K)
