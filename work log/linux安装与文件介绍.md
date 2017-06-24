# linux             
## linux 介绍                

   Linux是一套免费使用和自由传播的类Unix操作系统，是一个基于POSIX和UNIX的多用户、多任务、支持多线程和多CPU的操作系统。它能运行主要的UNIX工具软件、应用程序和网络协议。它支持32位和64位硬件。Linux继承了Unix以网络为核心的设计思想，是一个性能稳定的多用户网络操作系统.                 
   Linux是一套免费使用和自由传播的类Unix操作系统，是一个基于POSIX和UNIX的多用户、多任务、支持多线程和多CPU的操作系统。它能运行主要的UNIX工具软件、应用程序和网络协议。它支持32位和64位硬件。Linux继承了Unix以网络为核心的设计思想，是一个性能稳定的多用户网络操作系统。               

## linux工作过程             
* 硬件----> kernel---------> shell --------->软件         
* kernel 核心功能：事件的调度和同步。进程间的通信(消息传递)。存储器管理。进程管理。       
* shell 核心功能：                   
  *作为命令语言，它交互式解释和执行用户输入的命令或者自动地解释和执行预先设定好的一连串的命令；作为程序设计语言，它定义了各种变量和参数，并提供了许多在高级语言中才具有的控制结构，包括循环和分支。*
  *图形界面：linux shell 包括 X window manager (BlackBox和FluxBox），以及功能更强大的CDE、GNOME、KDE、 XFCE*
  *命令行方式：文字操作系统与外部最主要的接口就叫做shell。shell是操作系统最外面的一层。shell管理你与操作系统之间的交互：等待你输入，向操作系统解释你的输入，并且处理各种各样的操作系统的输出结果。*
## linux安装
* 把bios调节尾enable型，有些电脑按F2即可，我的电脑是联想G50笔记本，可以按电脑电源旁的小按钮即可进入设置环境       
* 装虚拟机            
* 打开虚拟机，装入linux，注意在中间设置所占内存设置的大点，防止不够，接着点击继续，在安装的过程中，注意设置安装环境和设置密码                  

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
* /：根目录，所有的目录、文件、设备都在/之下，/就是Linux文件系统的组织者，也是最上级的领导者。                    
* /bin：bin 就是二进制（binary）英文缩写。在一般的系统当中，都可以在这个目录下找到linux常用的命令。系统所需要的那些命令位于此目录。         
* /var：这个目录的内容是经常变动的，看名字就知道，可以理解为vary的缩写，/var下有/var/log 这是用来存放系统日志的目录。/var/ www目录是定义Apache服务器站点存放目录；/var/lib 用来存放一些库文件，比如MySQL的，以及MySQL数据库的的存放地。
* etc 软件安装
* lib 库用来存放系统动态连接共享库的
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
### 基本文件操作1     

* 文件的创建        
 touch: 创建一个空的文件。
*  删除                 

  rm  /m1/f1       删除/m1目录下的f1
  rm  –f   /m1/   删除m1目录下的所有文件 
  rm  -rf  /m1      强制删除一个目录 
* 复制                

    格式：cp   [参数]   <源路径>  <目标路径>  
    参数：-f：文件在目标路径中存在时，则直接覆盖                          
     -i：文件在目标路径中存在时, 提示是否覆盖                      
      -r：复制指定中所有内容和结构                              
        -b：生成覆盖文件的备份                        
         -a：保持文件原有属性                            
* 移动                  
　　mv
　　功能：移动文件、重命名文件                                   
 格式：mv　［参数］ <源路径>  <目标路径>                                 
  mv   /m1/f1     /m2/   移动/m1目录下f1文件到/m2目录下                           
   mv    f1   f2          将当前目录下的f1文件改名f2                           
    mv   -f  /d1/*  /d2/    移动/d1中的所有文件到/d2目录中                  
      
* 创建目录
   mkdir 
        功能：建立目录                         
        　格式：mkdir  [参数]  <目录名>                       
         参数：-m  属性值：指定目录的属性 (r、w、x或4、2、1)                      
    * 删除目录                   
    rmdir
        功能：删除空目录                     
        格式：rmdir  [参数]  <目录名>                            
   ### 基本文件操作2
   * 显示目录
   命令：pwd+文件名         
   * 切换目录
   命令：cd          
   cd ../:进入父目录下的某个文件            
   cd ./:进入当前目录下的某个文件             
   cd :进入主目录
   cd .. :返回父文件                
   * 显示文件            
   命令：ls
   ls :显示当前文件夹的文件
   ls -a :显示所有文件，包括隐藏文件
   
* 检查文件类型         
命令：file +文件名              
* 显示文件内容               
命令：cat +文件名                           
* 解压文件                            
命令：tar  -xvf  all.tar                         
* 显示不同                  
命令：diff              
格式：diff 　文件１　　文件2                 
* 命令自动补齐                    
命令：按table键自动补齐



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
