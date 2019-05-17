*    项目部王崇昂 笔记



>    4月/4日
 +   split() 方法用于把一个字符串分割成字符串数组。
 +   push() 方法可向数组的末尾添加一个或多个元素，并返回新的长度。
 +   join() 方法用于把数组中的所有元素放入一个字符串。
 +   元素是通过指定的分隔符进行分隔的。('括号内添加符号')
 +   
 +  
 +  
 +  

 >   4月8号 
 +  git 命令笔记
 +  创建项目：

1. 首先先进入github。网址是：https://github.com/     

2. 如果你还没有在github上注册过账号，那你先要注册一个账号，账号最好是用自己常用的邮箱，方便别人联系你，对你以后的工作极有帮助。下面是刚进入github的页面。

3. 首次要先创建一个仓库，用来存储你的项目。步骤：先用鼠标点右上角的 “ + ”，然后再点 “New repository”  。

4. 接着，在 ''Repository name'' 所对应那一项上写上你本次上传的项目名称，在 “Description” 所对应那一项上写上你本次上传的项目的一些简单介绍；

5. 以方便别人浏览。下面的 “Public” 、"Private" 是权限，是说你这个项目是给全世界的人看，还是私密的。最后点 “Create repository”

    接着会进入以下界面，在这里你要记住 “Quick setup - if you're done this kind of thing before” 这一行下的“SSH”后面的内容，我这里是：https://github.com/STU-BLUESKY/-.git

    > 操作步骤以及错误:

1.  在文件 或者桌面打开  git bash here (在文件内打开  使用的是当前文件目录;在桌面打开还需要打开目  cd 位置  （父级开始 一个父级一行 直到当前目录））

2.  开始操作 ：输入 " git init "  创建大库 初始化

3.  再输入 " git add . ", 这个是将项目上所有的文件添加到仓库中的意思；
     
     如果想添加某个特定的文件，只需把' . '换成这个特定的文件名即可。

4.  接着输入 " git commit -m "first commit "，表示你对这次提交的注释，双引号里面的内容可以根据个人的需要改。

    例如 " git commit -m "第一次提交 " 。

5.  输入 "git remote add origin https://自己的仓库url地址（GitHub 项目的网址）"  将本地的仓库关联到github上，

6.  最后一步，输入 "git push origin master "，这是把代码上传到github仓库的意思。




    > 容易发生的错 :

+  github常见操作和常见错误！

+    如果输入$ git remote add origin git@github.com:djqiang（github帐号名）/gitdemo（项目名）.git 

+   提示出错信息：fatal: remote origin already exists.

    > 解决办法如下：

    1. 先输入$ git remote rm origin

    2. 再输入$ git remote add origin git@github.com:djqiang/gitdemo.git 就不会报错了！

    3. 如果输入$ git remote rm origin 还是报错的话，error: Could not remove config section 'remote.origin'. 我们需要修改gitconfig文件的内容

    4. 找到你的github的安装路径，我的是C:\Users\ASUS\AppData\Local\GitHub\PortableGit_ca477551eeb4aea0e4ae9fcd3358bd96720bb5c8\etc

    5. 找到一个名为gitconfig的文件，打开它把里面的[remote "origin"]那一行删掉就好了！



+  如果输入$ ssh -T git@github.com
    出现错误提示：Permission denied (publickey).因为新生成的key不能加入ssh就会导致连接不上github。

    解决办法如下：

    1. 先输入$ ssh-agent，再输入$ ssh-add ~/.ssh/id_key，这样就可以了。

    2. 如果还是不行的话，输入ssh-add ~/.ssh/id_key 命令后出现报错Could not open a connection to your authentication agent.解决方法是key用Git Gui的ssh工具生成，这样生成的时候key就直接保存在ssh中了，不需要再ssh-add命令加入了，其它的user，token等配置都用命令行来做。

    3. 最好检查一下在你复制id_rsa.pub文件的内容时有没有产生多余的空格或空行，有些编辑器会帮你添加这些的。



    > 使用git在本地创建一个项目的过程

+    $ makdir ~/hello-world    //创建一个项目hello-world
+    $ cd ~/hello-world       //打开这个项目
+    $ git init             //初始化 
+    $ touch README
+    $ git add README        //更新README文件
+    $ git commit -m 'first commit'     //提交更新，并注释信息“first commit”
+    $ git remote add origin git@github.com:defnngj/hello-world.git     //连接远程github项目  
+    $ git push -u origin master     //将本地项目更新到github项目上去
>
+   使用git pull origin master把远程仓库拉下来
+   使用git rm -r --cached +文件名 来删除远程文件夹，但保留本地文件夹
+   使用git commit -m "备注" 来提交操作，并添加描述
+   使用git push -u origin mashter 提交到远程仓库即可
+   使用git clone 拉到本地文件




  