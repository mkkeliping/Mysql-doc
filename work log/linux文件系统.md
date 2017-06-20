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



<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>学生信息管理系统</title>
    <link rel="stylesheet" type="text/css" href="./public/css/bootstrap.min.css">
    <style type="text/css">
    body {
        height: 100%;
        background-color: lightblue;
    }

    ul li {
    	list-style: none;
    }
    
    .header {
        margin-bottom: 50px;
    }
    
    .operation>div {
        padding: 15px;
    }

    .operation.row .text-center button {
    	outline-style: none;
    }
    
    .forms li {
        display: none;
    }
    
    .forms li button {
        margin-right: 30px;
    }
    </style>
</head>

<body>
    <h1 class="header text-center">学生信息管理系统</h1>
    <div class="container">
        <div class="operation row">
            <div class="text-center col-md-3 col-sm-6">
                <button>添加学生信息</button>
            </div>
            <div class="text-center col-md-3 col-sm-6">
                <button>查询学生信息</button>
            </div>
            <div class="text-center col-md-3 col-sm-6">
                <button>修改学生信息</button>
            </div>
            <div class="text-center col-md-3 col-sm-6">
                <button>删除学生信息</button>
            </div>
        </div>
        <ul class="forms">
            <li class="show">
                <form class="form-horizontal" method="get" action="/cgi-bin/sx/add.cgi">
                    <div class="form-group">
                        <label for="stuId" class="col-sm-2 control-label">学生学号</label>
                        <div class="col-sm-10">
                            <input type="text" name="stuId" class="form-control" id="stuId" placeholder="请输入学生学号">
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="name" class="col-sm-2 control-label">学生姓名</label>
                        <div class="col-sm-10">
                            <input type="text" name="name" class="form-control" id="name" placeholder="请输入学生姓名">
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="age" class="col-sm-2 control-label">学生年龄</label>
                        <div class="col-sm-10">
                            <input type="text" name="age" class="form-control" id="age" placeholder="请输入学生年龄">
                        </div>
                    </div>
                    <div class="text-center">
                        <button type="submit" class="btn btn-success">提交</button>
                        <button type="reset" class="btn btn-success">重置</button>
                    </div>
                </form>
            </li>
            <li>
                <form class="form-horizontal" method="get" action="/cgi-bin/sx/sel.cgi">
                    <div class="form-group">
                        <label for="name-sel" class="col-sm-2 control-label">输入姓名查询</label>
                        <div class="col-sm-10">
                            <input type="text" name="name" class="form-control" id="name-sel" placeholder="输入*查询所有">
                        </div>
                    </div>
                    <div class="text-center">
                        <button type="submit" class="btn btn-success">提交</button>
                        <button type="reset" class="btn btn-success">重置</button>
                    </div>
                </form>
            </li>
            <li>
                <form class="form-horizontal" method="get" action="/cgi-bin/sx/mod.cgi">
                    <div class="form-group">
                        <label for="stuId-mod" class="col-sm-2 control-label">学生学号</label>
                        <div class="col-sm-10">
                            <input type="text" name="stuId" class="form-control" id="stuId-mod" placeholder="请输入学生学号">
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="name-mod" class="col-sm-2 control-label">学生姓名</label>
                        <div class="col-sm-10">
                            <input type="text" name="name" class="form-control" id="name-mod" placeholder="请输入学生姓名">
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="age-mod" class="col-sm-2 control-label">学生年龄</label>
                        <div class="col-sm-10">
                            <input type="text" name="age" class="form-control" id="age-mod" placeholder="请输入学生年龄">
                        </div>
                    </div>
                    <div class="text-center">
                        <button type="submit" class="btn btn-success">提交</button>
                        <button type="reset" class="btn btn-success">重置</button>
                    </div>
                </form>
            </li>
            <li>
                <form class="form-horizontal" method="get" action="/cgi-bin/sx/del.cgi">
                    <div class="form-group">
                        <label for="stuId-del" class="col-sm-2 control-label">输入要删除的学生Id</label>
                        <div class="col-sm-10">
                            <input type="text" name="stuId" class="form-control" id="stuId-del" placeholder="输入学生Id">
                        </div>
                    </div>
                    <div class="text-center">
                        <button type="submit" class="btn btn-success">提交</button>
                        <button type="reset" class="btn btn-success">重置</button>
                    </div>
                </form>
            </li>
        </ul>
    </div>
    <script src="./public/js/jquery-3.0.0.min.js"></script>
    <script src="./public/js/bootstrap.min.js"></script>
    <script type="text/javascript">
    $(function() {

    	var btns = $(".operation button");
    	var lis = $(".forms li");
        btns.addClass("btn btn-primary btn-lg");

        for (var i = 0; i < btns.length; i++){
        	btns.eq(i).click(i, function(event){
        		lis.eq(event.data).addClass("show").siblings().removeClass("show");
        	});
        }

    });
    </script>
</body>

</html>



















mysql> show variables like 'character%'
    -> ;
+--------------------------+----------------------------+
| Variable_name            | Value                      |
+--------------------------+----------------------------+
| character_set_client     | utf8                       |
| character_set_connection | utf8                       |
| character_set_database   | latin1                     |
| character_set_filesystem | binary                     |
| character_set_results    | utf8                       |
| character_set_server     | latin1                     |
| character_set_system     | utf8                       |
| character_sets_dir       | /usr/share/mysql/charsets/ |
+--------------------------+----------------------------+
8 rows in set (0.02 sec)

mysql> character_set_database=utf8;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'character_set_database=utf8' at line 1
mysql> character_set_server=utf8;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'character_set_server=utf8' at line 1
mysql> set character_set_server=utf8;
Query OK, 0 rows affected (0.00 sec)

mysql> set character_set_database=utf8;
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql> show variables like 'character%';
+--------------------------+----------------------------+
| Variable_name            | Value                      |
+--------------------------+----------------------------+
| character_set_client     | utf8                       |
| character_set_connection | utf8                       |
| character_set_database   | utf8                       |
| character_set_filesystem | binary                     |
| character_set_results    | utf8                       |
| character_set_server     | utf8                       |
| character_set_system     | utf8                       |
| character_sets_dir       | /usr/share/mysql/charsets/ |
+--------------------------+----------------------------+
8 rows in set (0.01 sec)

mysql> 
