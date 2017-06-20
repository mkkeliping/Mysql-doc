# linux文件系统
## linux文件系统介绍
*文件系统是操作系统用于明确存储设备或分区上的文件的方法和数据结构；即在存储设备上组织文件的方法。贯彻一切操作接文件的思想，*
## 文件系统分类
* 磁盘文件系统：指本地主机中实际可以访问到的文件系统，比如磁盘。
* 网络文件系统：是可以远程访问的文件系统，这种文件系统在服务器端仍是本地的磁盘文件系统，客户机通过网络远程访问数据，比如NFS。
* 专有/虚拟文件系统：不驻留在磁盘上的文件系统，比如proc，sys等。sys是系统用的，不占内存，用来处理临时文件。   
* 注：在linux中0代表输入1代表标准输出2代表错误，标准端口被占用
## 文件查看
* cat cpuinfo查看cpu信息
图片
* cat meminfo 查看内存
图片
* cat kmsy 所有kernel 启动时所有信息
图片
### 基本的根目录文件
* etc 软件安装
* lib 库
* media 多媒体光驱
* opt 第三方编译器
* root根用户目录
* sys系统用的
* lost+found 文件系统
### proc 介绍
* fb显卡驱动
* zrp中断
* softirqs软中断

## 基本文件操作
### 基本文件操作
* 文件的创建（toush ***）
*  删除
  rm  /m1/f1       删除/m1目录下的f1
  rm  –f   /m1/*   删除m1目录下的所有文件 
  rm  -rf  /m1      强制删除一个目录 
* 复制http://www.jb51.net/LINUXjishu/43202.html
重命名、移动
* 列出文件列表
* 查看文件内容

create table Student(
stuID smallint primary key,/*学号*/
stuName varchar(10) not null,#学生名称
stuSex  char(2) check(stuSex in('男','女')),#学生性别
stuBorn date,#学生出生日期年-月-日
stuPolSta varchar(8),#政治面貌
stuAdr varchar(30),#籍贯
stutel char(11),#学生电话
stumajor smallint,#学生所属系号
foreign key (stumajor) references Major(MajorCode)#外键，被参照表是Major，被参照列是MajorCode
);
