> ##  JQuery 
* jQuery 是一个 JavaScript 库,jQuery 极大地简化了 JavaScript 编程。
----
querySelector
* 该方法返回满足条件的单个元素。按照深度优先和先序遍历的原则使用参数提供的CSS选择器在DOM进行查找，返回第一个满足条件的元素
[百度](https://baidu.com)
####  $符号
*  (美元符号)本质上就是一个函数，但是函数也是对象，于是(美元符号)除了可以直接调用外，也可以有很多其他属性。

 * 注意，你看到的(美元符号)函数名可能不是jQuery(selector, context)，因为很多JavaScript压缩工具可以对函数名和参数改名，所以压缩过的jQuery源码$函数可能变成a(b, c)。

#### 修改Text和HTML

* jQuery对象的text()和html()方法分别获取节点的文本和原始HTML文本
* 无参数调用text()是获取文本，传入参数就变成设置文本，HTML也是类似操作
