## vue文件笔记

* 启动服务器

> 下载 vue 依赖包 : npm install

> 启动服务器命令 : npm serve 

* vue 文件

> template标签 ：用来写html标签(不能存放多个标签 须放在一个标签内;否则报错)

> seyle 标签  ： 用来写css样式

>export default

> 在vue 单文件 (组件)里 data 需要加一个函数 再写花括号

>返回值 return : 我们要的数据

* 如何把 vue 文件编译成 html 文件?

>npm run build 写的所有程序 通过这个 打包成html文件

>引入文件 improt  如果想使用 需要注册这个组件   在JS统计里面写一个components：{} 花括号内添加引入文件名  用一个标签的方式 把组件引入到标签中 

>import AppHeaderw from './components/AppHeader(可以不写后缀)'
>       文件名                  当前路径