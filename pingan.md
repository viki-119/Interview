### 浏览器地址栏输入url后, 到页面渲染发生了什么?


### http协议;
* [参考链接1](https://www.cnblogs.com/zhou-test/p/9803478.html)
* [参考链接1](https://www.cnblogs.com/sunny-sl/p/6529830.html)

> http状态码

状态码 | 描述
--------|-------
1xx | 临时响应
2xx | 成功
3xx | 已重定向
4xx | 请求错误
5xx | 服务器错误
204 | 浏览器请求执行成功，但没有数据，浏览器不用刷新页面。也不用倒向新的页面；

### TCP的三次握手与四次挥;
* [参考链接1](https://www.cnblogs.com/crazytata/p/9086732.html)
* [参考链接2](https://blog.csdn.net/qq_38950316/article/details/81087809)
* [参考链接3](https://www.jianshu.com/p/ed254fd97125)
* [参考链接4](https://baijiahao.baidu.com/s?id=1618114723935605183&wfr=spider&for=pc)

深入理解Cookie和Session机制;
-------------------------
* cookie客户端保持状态；session服务端保持状态;

regexObj.exec(str)

```js
function getCookie(name) {
  const arr = new RegExp('\\b' + name + '\\=([^;]+)').exec(document.cookie);
  return arr ? arr[1] : '';
}

const cc ="name=123; name=456";
const arr = new RegExp('\\b' + 'name' + '\\=([^;]+)').exec(cc);
console.log(arr);
// ["name=123", "123", index: 0, input: "name=123; name=456", groups: undefined]
```
- **[参考链接](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp/exec)**

regexObj.test(str)
* **方法执行一个检索，用来查看正则表达式与指定的字符串是否匹配。返回 true 或 false。**
* [参考链接](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp/exec)

str.search(regexp)
* **如果匹配成功，则 search() 返回正则表达式在字符串中首次匹配项的索引;否则，返回 -1。**
* [参考链接](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/search)

[参考链接](https://www.cnblogs.com/pengc/p/8714475.html)
[参考链接2](https://www.jianshu.com/p/b5efddc433f5)

为什么禁用cookie就不能得到session？解决方案是什么？
----------------------------------------------
session采用session_id来确定当前对话所对应的服务器session，而session_id是存储在cookie中通过cookie来传递的，禁用cookie相当于失去了session_id,也就得不到session了；

解决方案：
* 1.把session_id直接附加在url路径的后面；url重写
* 2.表单隐藏字段，以便在表单提交时把session_id传回服务器；
* [参考链接1](https://blog.csdn.net/cckevincyh/article/details/52494014)
* [参考链接2](https://blog.csdn.net/ai_shuyingzhixia/article/details/80778183)

### localStorage 和 sessionStorage 理解
#### 相同点:
* 都是用来存储客户端临时信息的对象;
* 只能存储字符串类型的对象;
* 使用相同的API： setItem方法设置;
#### 不同点:
* 1:localStorage生命周期是永久，sessionstorage生命周期为当前窗口或标签页
* 2:相同浏览器的不同页面间可以共享相同的 localStorage（页面属于相同域名和端口），但是不同页面或标签页间无法共享sessionStorage的信息。这里需要注意的是，页面及标 签页仅指顶级窗口，如果一个标签页包含多个iframe标签且他们属于同源页面

[参考链接1](https://www.jianshu.com/p/65e3fb47a23a)

| api | 描述 |
| --- | ------ |
| setItem (key, value) | 保存数据，以键值对的方式储存信息。 |
| getItem (key) | 获取数据，将键值传入，即可获取到对应的value值。 |
| removeItem (key) | 删除单个数据，根据键值移除对应的信息。 |
| clear() | 删除所有的数据。 |
| key(index) | 获取某个索引的key。 |

[参考链接2](https://blog.csdn.net/sskk1118/article/details/78865520)
[参考链接3](https://www.jianshu.com/p/700f5a290c8c)

### cookie 与 localStorage/sessionStorage 区别
* cookie的大小只有4Kb左右（浏览器不同，大小也不同); 而web Storage的大小有5MB

[参考链接1](https://www.cnblogs.com/8023-CHD/p/10944760.html)
[参考链接2](https://blog.csdn.net/hjc256/article/details/88789196)
[参考链接3](https://www.jianshu.com/p/701ea9950f6d)

## css相关:
### display: none; 与 visibility: hidden;
* visibility: hidden;即使不可见的元素也会占据页面上的空间。
* display: none; 不占据页面空间。
* [参考链接](https://www.w3school.com.cn/cssref/pr_class_visibility.asp)

| 值 | 描述 |
| --- | ------ |
| visible | 默认值。元素是可见的。 |
| hidden | 元素是不可见的。 |
| collapse | 当在表格元素中使用时，此值可删除一行或一列，但是它不会影响表格的布局。被行或列占据的空间会留给其他内容使用。如果此值被用在其他的元素上，会呈现为 "hidden"。 |
| inherit | 规定应该从父元素继承 visibility 属性的值。 |


多标签模式和多窗口模式
--------------------
* 多标签模式就是在一个窗口启用多个标签；
* 多窗口模式就是一个窗口只能有一个标签；许打开多个页面实现多标签；
