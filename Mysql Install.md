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
    3. workbench 安装         
        sudo apt-get install mysql-workbench








/* 学校表，包括全国各大高校*/
create table School(
SchoolCode smallint primary key,/*学校编号*/
SchoolName varchar(30) not null,#学校名称，汉字不能超过15个
SchoolBorn date,#学校创办日期
SchoolAdr varchar(40),#学校地址
SchoolHead  varchar(10)#校长名
);


/* 学院表，包括一个学校中的所有学院*/
create table College(
collegeCode smallint primary key,/*学院编号*/
collegeName varchar(30) not null,#学院名称，汉字不能超过15个
collegeHead  varchar(10),#院长名
SchoolCode smallint,
FOREIGN KEY (SchoolCode) REFERENCES School(SchoolCode)
);

/* 专业表，包括每个院的各个专业*/
create table Major(
MajorCode smallint primary key,/*专业编号*/
MajorName varchar(20) not null,#专业名称，汉字不能超过15个
MajorHead  varchar(10),#专业指导老师
collCode smallint,#学院编号
FOREIGN KEY (collCode) REFERENCES College(collegeCode)#外键，被参照表是College，被参照列是collegeCode
);

/* 学生信息表，包括每个专业的各个学生信息*/
create table Student(
stuID smallint primary key,/*学号*/
stuName varchar(10) not null,#学生名称
stuSex  char(2),#学生性别
stuBorn date,#学生出生日期年-月-日
stuPolSta varchar(8),#政治面貌
stuAdr varchar(30)#籍贯
);
