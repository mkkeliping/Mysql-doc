# MySQL Install
## 介绍MySQL及C/S工作流程

MySQL是一个关系型数据库管理系统，由瑞典MySQL AB 公司开发，目前属于 Oracle 旗下产品。MySQL以其速度、高可靠性、简单易用，广泛应用,一些大型企业也在逐渐应用，如：Facebook、维基百科等网站。    

图品
## MySQL安装
> MySQL安装
>> 1. vim  .vimr     
        解释：如果没有找到vimrc或gvimrc，它缺省工作VI兼容的模式，这意味着，你只能使用VI所具备的功能，而vim中的大量扩展功能将无法使用。也许这就是          你的vim如此难用的原因。                                                                                                
         在Linux安装数据库时，进行.vimrc配置：先进入.vimrc然后把原来的删除，然后按I进入编辑状态，粘贴下文，配置环境。    
         *deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse
         deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse
         deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse
         deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse          
         `##测试版源`     
         deb http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse       
         `# 源码`  
         deb-src http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse
         deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse
         deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse
         deb-src http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse       
         `##测试版源`    
          deb-src http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse       
         `# Canonical 合作伙伴和附加`   
         deb http://archive.canonical.com/ubuntu/ xenial partner
         deb http://extras.ubuntu.com/ubuntu/ xenial main*           
      2. sudo vim /etc/apt/sources.list     
        解释 ：打开源列表        
      3. sudo apt-get update    
        解释：更新源      
      4. sudo apt-get install tasksel        
        解释：安装       
      5. mysql -u root -p         
       解释：连接本地数据库注意输入上述命令后回车出现Enter password:然后在输入密码            
       连接远程主机MySQL需要输入mysql -h110.110.110.110 -u root -p 123;其中前面是主机，本主机可以省去。      
       
 > MySQL 其他设置命令       
 >> 1. 退出MYSQL命令： exit （回车)            
       2. 修改密码：mysqladmin -u用户名 -p旧密码 password 新密码








 databases
    -> ^C  bases

^C
mysql> show databases
    -> ;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.09 sec)

mysql> create database STU
    -> create database STU;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'create database STU' at line 2
mysql> create database STU create database STU;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'create database STU' at line 1
mysql> create database STU;
Query OK, 1 row affected (0.16 sec)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| STU                |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.05 sec)

mysql> drop database STU;
Query OK, 0 rows affected (0.32 sec)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.00 sec)

mysql> 
mysql> create database STU;
Query OK, 1 row affected (0.00 sec)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| STU                |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.00 sec)

mysql> use STU
Database changed
mysql> select database();
+------------+
| database() |
+------------+
| STU        |
+------------+
1 row in set (0.00 sec)

mysql> select now();
+---------------------+
| now()               |
+---------------------+
| 2017-06-15 02:08:07 |
+---------------------+
1 row in set (0.01 sec)

mysql> create table information;
ERROR 1113 (42000): A table must have at least 1 column
mysql> create table information
    -> 
    -> 
    -> (ID int(4) not null primary key auto_increment,
    -> Name VARCHAR(20) not nul;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'nul' at line 5
mysql> create table information   (ID int(4) not null primary key auto_increment, Name VARCHAR(20) not nul,
    -> 
    -> Sex VARCHAR(4),
    -> Sex VARCHAR(4) not null,
    -> Sdept VARCHAR(40))
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'nul,

Sex VARCHAR(4),
Sex VARCHAR(4) not null,
Sdept VARCHAR(40))' at line 1
mysql> desc information;
ERROR 1146 (42S02): Table 'STU.information' doesn't exist
mysql> create table information   (ID int(4) not null primary key auto_increment, Name VARCHAR(20) not null,  Sex VARCHAR(4), Sex VARCHAR(4) not null, Sdept VARCHAR(40));
ERROR 1060 (42S21): Duplicate column name 'Sex'
mysql> create table information   (ID int(4) not null primary key auto_increment, Name VARCHAR(20) not null,  Sex VARCHAR(4), Sex VARCHAR(4) not null, Sdept int(4));
ERROR 1060 (42S21): Duplicate column name 'Sex'
mysql> create table information   (ID int(4) not null primary key auto_increment, Name VARCHAR(20) not null,  Sex VARCHAR(4), Sex VARCHAR(4) not null, Sdept int(4),);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 1
mysql> create table information   (ID int(4) not null primary key auto_increment, Name VARCHAR(20) not null,  Sex VARCHAR(4), Sex VARCHAR(4) not null, Sdept int(4),);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 1
mysql> create table information   (ID int(4) not null primary key auto_increment, Name VARCHAR(20) not null,  Sex VARCHAR(4), Sex VARCHAR(4) not null, Sdept int(4),FOREIGN KEY (Sdept)REFERENCES School(Sdept));
ERROR 1060 (42S21): Duplicate column name 'Sex'
mysql> (ID int(4) not null primary key auto_increment, Name VARCHAR(20) not null,  Sex VARCHAR(4), Sex VARCHAR(4) not null, Sdept int(4),FOREIGN KEY (Sdept)REFERENCES School(Sdept));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ID int(4) not null primary key auto_increment, Name VARCHAR(20) not null,  Sex V' at line 1
mysql> create table information   (ID int(4) not null primary key auto_increment, Name VARCHAR(20) not null, Sex VARCHAR(4) not null, Sdept int(4),FOREIGN KEY (Sdept)REFERENCES School(Sdept))
    -> ;
ERROR 1215 (HY000): Cannot add foreign key constraint
mysql> create table School (Sdept int(8) not null primary key, Sname VARCHAR(40) not null);
Query OK, 0 rows affected (0.05 sec)

mysql> create table information   (ID int(4) not null primary key auto_increment, Name VARCHAR(20) not null, Sex VARCHAR(4) not null, Sdept int(4),FOREIGN KEY (Sdept)REFERENCES School(Sdept))
    -> ;
Query OK, 0 rows affected (0.08 sec)

mysql> desc information
    -> ;
+-------+-------------+------+-----+---------+----------------+
| Field | Type        | Null | Key | Default | Extra          |
+-------+-------------+------+-----+---------+----------------+
| ID    | int(4)      | NO   | PRI | NULL    | auto_increment |
| Name  | varchar(20) | NO   |     | NULL    |                |
| Sex   | varchar(4)  | NO   |     | NULL    |                |
| Sdept | int(4)      | YES  | MUL | NULL    |                |
+-------+-------------+------+-----+---------+----------------+
4 rows in set (0.07 sec)

mysql> desc School
    -> ;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| Sdept | int(8)      | NO   | PRI | NULL    |       |
| Sname | varchar(40) | NO   |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> 



