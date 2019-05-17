

>##   MYSQL 
* MYSQL是一个关系型数据库管理系统,由瑞典MYSQL AB公司开发,目前Oracle旗下产品。MYAQL是最流行的关系型数据库管理系统之一,在WEB应用方面,MYSQL是最好的ROBMS(Relational Database Management System,关系数据库管理系统) 应用软件。
* MySQL是一种关系数据库管理系统，关系数据库将数据保存在不同的表中，而不是将所有数据放在一个大仓库内，这样就增加了速度并提高了灵活性。 

>## SQL语言
>####  如何使用终端操作数据库   

>### 1.如何登陆 
>* mysql -uroot -p（密码）  --- 登陆
>* exit;  退出登录

>### 2.如何查询数据库服务器中所有数据库
>* show databases;           ---查看数据库里所有的数据
>###  3.如何选中某一个数据库进行操作
>* use （数据库id）;          ---- 选中数据库 
>* select * from (数据名)  输入分号进行结束   ---查询数据
>* select * from admin where Admin_ID=1;    ---只查询Admin ID为1的数据
>* show tables;  ---- 查看某个数据库中所有的数据表；
(Empty set(0.01 sec) 译为没有数据)

>### 4.如何在数据库服务器中创建我们的数据库;
>* create database text;

>### 5.如何创建一个数据表？
>    create table pet(
        name varchar(20), 
        owner varchar(20),
        species varchar(20),
        sex char(1),
        birth date,
        death date);
    )
    上面这些都叫做数据字段
    后面这个东西叫做数据类型
    pet                     --------数据表的名字
    describe   （   数据表名字）    -----查看数据表的结构

>### 6.如何在语言中操作数据库 
>查看数据表是否创建成功
   show tables;   ---查看所有数据表
    +----------------+
    | Tables_in_test |
    +----------------+
    | pet            |
    +----------------+
    1 row in set (0.00 sec)
    
>##### 数据表结构
    +---------+-------------+------+-----+---------+-------+
    | Field   | Type        | Null | Key | Default | Extra |
    +---------+-------------+------+-----+---------+-------+
    | name    | varchar(20) | YES  |     | NULL    |       |
    | owner   | varchar(20) | YES  |     | NULL    |       |
    | species | varchar(20) | YES  |     | NULL    |       |
    | sex     | char(1)     | YES  |     | NULL    |       |
    | birth   | date        | YES  |     | NULL    |       |
    | death   | date        | YES  |     | NULL    |       |
    +---------+-------------+------+-----+---------+-------+
    Field   --- 字段   
    Type   ---字段的类型
    Null    ---是否允许为空    
    Key   ---约束相关的东西
    Default   ---默认值     
    Extra   ---额外得一些东西
    +----------+-------+---------+------+------------+-------+
    | name     | owner | species | sex  | birth      | death |
    +----------+-------+---------+------+------------+-------+
    | Puffball | Diane | hamster | f    | 1993-03-30 | NULL  |
    | 马胜秦   | QSM   |         | n    | 2002-00-00 | NULL  |
    +----------+-------+---------+------+------------+-------+
    name名字
    owner---主人 
    species---种类   
    sex---性别    
    birth---生日   
    death---死亡日期
    select * from pet  ---查看数据表中的记录(加分号会报错!)
     insert into (数据表的名字）---往数据表中添加数据记录
     values ('Puffball','Diane','hamster','f','1993-03-30',NULL);


     MySQL 常用的数据类型？
     数值
     日期/时间
     字符串（字符）类型

     delete from 数据表名 where name='name值';  ---删除数据
     delete from pet where name='马胜秦';   可以删除上面数据表 数据
     update 数据表名 set name='' where 拥有者 （主人）='主人的明'---修改数据
     update pet set name='第一条数据' where species='hamster'

     总结  数据记录常见操作
     insert ---增加
     delete---删除
     update ---修改
     select---查询
### 5.MYSQL 键表约束

 > <strong><center>主键约束</center></strong>
<font color='red'>他能够唯一确定一张表中一条记录，也就是我们通过给某个字段添加约束，就可以使得该字段不重复且不为空;</font>
如何创建
create table user(
    id int primary  key,
    name varchar(20)
)
联合主键（任何一个值也不能为空（null））
 create table user2(
     id int,name varchar(20),
     password varchar(20),
     primary key(id,name)
     );
     创建数据表
insert into user2 values (1,'张三','123');
insert into user2 values (2,'张三','123');
为什么id不一样 name一样还能进行主键呢 
只要联合的主键值加起来不重复就ok

 > <strong><center>自增约束</center></strong>
create table user3(
     id int primary key auto_increment,
     name varchar(20)
     );
 insert into user3 (name) values('zhangsan');
 insert into user3 (name) values('zhangsan');
我们并没有上传id值   它（auto_increment）自动给我们生成id为123排序
；
   +----+----------+
    | id | name     |
    +----+----------+
    |  1 | zhangsan |
    |  2 | zhangsan |
    +----+----------+
    desc （数据表名）查看表结构

>* 主键建表后添加删除
    create table user4(
        id int,
        name varchar(20)
        );
    创表时忘记创建主键约束怎么办
    修改表结构  添加主键
    alter table user4 add primary key(id);---添加主键元素
    alter table user4 drop primary key;   ---删除主键
    update delete insert                  ----对记录操作；
    add drop                              ---对表结构操作
    alter table user4 modify id int primary key;  ---修改字段、添加约束
    创建表  或者创建表之后  进行修改、添加、删除  一些的操作

 > <strong><center>外键约束</center></strong>
    <font color='blue'>外键约束:
    涉及到两个表:父(主)表、子(副)表.</font>
     新建两个表  班级表 、学生表
     班级表
     create table classes(
         id int primary key,
         name varchar(20)
     );
     学生表
     create table students(
         id int primary key,
         name varchar(20),
        class_id int,
        foreign key(class_id) references classes(id)
     )
      class_id int : (班级表的id 是int类型 所以学生表的id也得是int类型)
      foreign key(class_id) references classes(id):
      class  id必须来自于classes 的id字段
    有什么作用？
    现在往班级表(classes)插入数据
    insert into classes  values (1,'一班');
    insert into classes  values (2,'二班');
    insert into classes  values (3,'三班');
    insert into classes  values (4,'四班');
    +----+------+
    | id | name |
    +----+------+
    |  1 | 一班 |
    |  2 | 二班 |
    |  3 | 三班 |
    |  4 | 四班 |
    +----+------+
    现在往学生表(students)插入数据
    insert into students  values (1001,'张三',1);
    insert into students  values (1002,'张三',2);
    insert into students  values (1003,'张三',3);
    insert into students  values (1004,'张三',4);
   <font color='red'>错误: insert into students  values (1005,'李四',5);  </font>
    这个表里面不能相加相应的外键约束
    班级是主(父)表   学生是副(子)表
    副(子)表里面的东西要参照主表  主(父)表里面不存在的 添加的话就会出错
    1、主(父)表内没有的数据  在 副(子)表中是不可以使用的  
    2、 主(父)表里面中的记录被副(子)表引用 是不可以删除的  
    3、假如想把4班删除的话  不可以的  因为classes主(父)表被引用了
    报错:你是不能够删除或者更新classes的内容 
    <font color='blue'>概念 : 外键约束是两个表  一个表要被另一个表所引用  而且添加或者删除不可执行的;</font>

 > <strong><center>唯一约束</center></strong>
<font color='blue'>约束修饰的字段的值不可以重复</font>
    create table user5(
        id int,
        name varchar(20)
        );
        给user5添加一个唯一约束
        alter table user5 add unique(name);
        效果
        +-------+-------------+------+-----+---------+-------+
        | Field | Type        | Null | Key | Default | Extra |
        +-------+-------------+------+-----+---------+-------+
        | id    | int(11)     | YES  |     | NULL    |       |
        | name  | varchar(20) | YES  | UNI | NULL    |       |
        +-------+-------------+------+-----+---------+-------+     
        UNI意思是  name不可以重复 
        create table user6(    ===   create table user6(
        id int,                ===   id int,
        name varchar(20),      ===   name varchar(20) unique
         unique(name)          ===   );
        );                    
        
        create table user7( 
        id int,  
        name varchar(20),
        unique(id,name)
        );  
         insert into user7  values(1,'zhangsan');
         insert into user7  values(2,'zhangsan');
         insert into user7  values(1,'lisi');
        添加两个unique  key的UNI变成了MUL  但是它还是唯一约束 依旧不可以重复  
        添加两个unique   id和name这两个键加起来不重复就行
        alter table user7 drop index 删除的属性id/name     ---删除唯一约束
        alter table user7 modify name varchar(20) unique;  ---添加 modify

        1、建表时添加约束
        2、建表时没添加约束  可以用 alter ()  add  ()
        3、alter  () modify ()
        
        4、删除  alter () drop ()

> <strong><center>非空约束</center></strong>
<font color='blue'>非空约束 : 修饰的字段不能为空</font>
            create table user9(
                id int,
                name varchar(20)  not null   (如果name为空的话 就会出错)
            );
        +-------+-------------+------+-----+---------+-------+
        | Field | Type        | Null | Key | Default | Extra |
        +-------+-------------+------+-----+---------+-------+
        | id    | int(11)     | YES  |     | NULL    |       |
        | name  | varchar(20) | NO   |     | NULL    |       |
        +-------+-------------+------+-----+---------+-------+
        区别:
        id null为yes允许
        name null为no 不允许
        insert into user9 (name) values('zhangsan');
        insert into user9 (name) values('lisi');
        可以看出来id 是允许为空的
        +------+----------+
        | id   | name     |
        +------+----------+
        | NULL | zhangsan |
        | NULL | lisi     |
        +------+----------+

> <strong><center>默认约束</center></strong>
<font color='blue'>默认约束:当我们插入字段值得时候，如果没有传值 就会默认值</font>
     create table user10(
                id int,
                name varchar(20),
                age int default 10
            );
          +-------+-------------+------+-----+---------+-------+
        | Field | Type        | Null | Key | Default | Extra |
        +-------+-------------+------+-----+---------+-------+
        | id    | int(11)     | YES  |     | NULL    |       |
        | name  | varchar(20) | YES  |     | NULL    |       |
        | age   | int(11)     | YES  |     | 10      |       |
        +-------+-------------+------+-----+---------+-------+
        insert into user10 (id,name) values(1,'zhangsan');
        +------+----------+------+
        | id   | name     | age  |
        +------+----------+------+
        |    1 | zhangsan |   10 |
        +------+----------+------+
        我们并没有添加age的值   age为默认值
        如果添加age的值  就不会是默认值

>### 数据库的三大设计范式.sql;
>1.  第一范式     ----1NF
<font color='green'>数据表中所有字段都是不可分割的原子值</font>
什么意思  ---  create table student2(
         id int primary key,
         name varchar(20),
        address varchar(30)
     )
    //创建一个表
    insert into student2 values(1,'张三','中国四川省1号');
    insert into student2 values(2,'李四','中国四川省2号');
    insert into student2 values(3,'王五','中国四川省3号');
<font color='green'>字段值还可以继续拆分的,就不满足第一范式</font>

* 原版   我正在去秦皇岛

     事件
我正在去秦皇岛

* 多分几个类型   
比如 我正在去秦皇岛  可以拆为

    谁    在干嘛   去哪里
    我    正在去   正在去  
  create table student3( 
         name varchar(20),
        doing  varchar(30),
        where varchar(30)
     );
    insert into student3 values('我','正在去','正在去');
-----
####  <font color='red'>基础知识</font> 
>   create table (数据表名)   ----创建数据表 
    select * from      ---查看数据表记录
    insert into (数据表名) values ('内容','内容');  ---添加内容
    insert into user2 (name) values ('张三');          ---单独添加(name可以更改) 
    drop table (数据表名字)     ---删除数据表  
    show tables;      ----显示所有数据表 
    drop database name   ---删除数据库 
     delete from (数据表名) where id='id值'  ---用id删除单个数据; 
----
```html
    数据类型:         占用字节数:                 表示范围:                                   适用场景:    	
      char            char(n)	                                                  ---使用char(2)来表示类型或状态(建议用tinyint代替)
    varchar          varchar(n)	                 1~8000                           ---只包含英文字符的字符串
      int             4个字节	          -2,147,483,648 到 2,147,483,647	    ---表示整型，比如自增ID和表示數量
    datetime           8字节          1753 年 1 月 1 日到 9999 年 12 月 31 日       ---表示日期和时间
      time                                                                        ---表示时间间隔，比如计时和耗時
```   
    create table pet(
        id int,
        name  varchar(20),
        age varchar(20),            name、age、sex列的数据类型是 varchar，包含字符，且这些字段的最大长度为 20个字符
        sex varchar(20),
    )