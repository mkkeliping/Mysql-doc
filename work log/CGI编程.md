# CGI编程
## Apache介绍及安装
Apache是世界使用排名第一的Web服务器软件。它可以运行在几乎所有广泛使用的计算机平台上，由于其跨平台和安全性被广泛使用，是最流行的Web服务器端软件之一。它快速、可靠并且可通过简单的API扩充，将Perl/Python等解释器编译到服务器中。
### Apache安装
1. sudo apt-get update
2. sudo apt-get install tasksel
3. sudo tasksel
## CGI
CGI(Common Gateway Interface) 是WWW技术中最重要的技术之一，有着不可替代的重要地位。CGI是外部应用程序（CGI程序）与WEB服务器之间的接口标准
是在CGI程序和Web服务器之间传递信息的过程。CGI规范允许Web服务器执行外部程序，并将它们的输出发送给Web浏览器，CGI将Web的一组简单的静态超媒体文档
变成一个完整的新的交互式媒体
>在apache中开启cgi支持.
>>命令：sudo ln -s /etc/apache2/mods-available/cgi.load /etc/apache2/mods-enabled/cgi.load
>需要重启 apache 服务器
>>命令：service apache2 restart
需要运行的cgi文件的存放路径为:
/usr/lib/cgi-bin已存在
>改完目录的权限, 方便对目录下的文件写.
>>命令：sudo mkdir /usr/lib/cgi-bin/sx
在目录/usr/lib/cgi-bin/下创建目录SX,以后的cgi文档会放在其中
>命令：sudo chmod 777 /usr/lib/cgi-bin/sx
>>改变文件夹的权限，将其改为可读可写
>命令：Makefile.
>>install:
cp `*`.cgi /usr/lib/cgi-bin/sx
运行把生成的所有.cgi文夹复制到cgi /usr/lib/cgi-bin/sx目录下
在此处也可以移动其他文件
5.2 MySQL的C接口介绍
	安装mysql的C语言库
sudo apt-get update
sudo apt-get install libmysqlclient-dev
	获取表单数据
cgiFormResultType   cgiFormString(char *name, char *result, int max);
参数：  name, 指定要获取的表单项的名字
       result,将获得的数据存储到result中
       max， 指定最多读取的字符个数
比如： cgiFormString("name", result,  16);可以获得最多16个字符并且保存于result中
	打印字符
int fprintf(FILE *stream, const char *format, ...);
功能： 将格式化的语句输出到指定的流
fprintf(stdin, "helloworld\n")  等价于 printf("helloworld\n)补充函数atoi
	转换char型为数字型
int atoi(const char *nptr);
功能：将一个字符串转换成对应的数字
	初始化函数
MYSQL *mysql_init(MYSQL *mysql)
初始化函数，参数为NULL即可，接收返回值。
失败，NULL
	连接mysql服务器
MYSQL *mysql_real_connect(MYSQL *mysql, const char *host, const char *user, const char *passwd, const char *db, unsigned int port, const char *unix_socket, unsigned long client_flag)
功能：连接mysql服务器
      失败，NULL
	关闭服务器连接
oid mysql_close(MYSQL *mysql)     功能：关闭服务器连接
	返回提示
const char *mysql_error(MYSQL *mysql)
功能：返回出错提示
