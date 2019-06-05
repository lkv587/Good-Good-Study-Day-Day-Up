### SecureCRT常用命令:

* 查看容器 docker ps|grep XXX

* 进入容器 docker exec -it xxx /bin/bash

#### 查看日志

* tail -f /opt/tomcat7/logs/catalina_ln.out

* yum list 		package1 显示指定程序包安装情况package1
* yum install 	package1 安装指定的安装包package1

#### curl
* get
    curl url+params
* post
    curl -d "params" url
#### vi命令
    vi catalina_ln.out
* 向下搜索 / xxx n
* 向上搜索 ? xxx n下一个
* :q! 退出vi

#### 服务启动/停止
* ./init.d/tomcat stop
* ./init.d/tomcat start
* service xxx restart
* netstat -tunlp
* yum reinstall xxx
* ps -ef|grep java
* kill -9 1102(进程)

### 常用命令：
#### ls 只列出文件名 （相当于dir，dir也可以使用）
-A:列出所有文件，包含隐藏文件。
-l：列表形式，包含文件的绝大部分属性。
-R：递归显示。
--help：此命令的帮助。
#### cd 改变目录
cd /:进入根目录
cd ：回到自己的目录（用户不同则目录也不同，root为/root，xxt为/home/xxt
cd ..：回到上级目录
pwd：显示当前所在的目录
#### less 文件名：查看文件内容。
四.q 退出打开的文件。
五.上传文件： rz 选择要传送的文件，确定。
六.下载文件： sz 指定文件名,enter敲，即下载到了secureCRT/download目录下。
七：删除文件： rm 删除文件 ，rmdir 删除空目录。

八.显示 最近输入的20条命令：history 20

九.获得帮助命令 --help查看命令下详细参数： 如：rz --help ， sz --help 。


十.cd 进入某个文件夹的命令：
mkdir+文件夹名 创建某个文件夹的命令
sz+文件名 从服务器端向本机发送文件的命令
rz 从本机向服务器端传送文件的命令
ll 列出当前目录下的所有文件,包括每个文件的详细信息
dir 对当前文件夹
vi 打开当前文件
十一.在编辑某个文件的时候：
a 切换到编辑模式
ctrl+c 退出编辑模式
dd 删除整行
:q 退出当前文件
:w 写入并保存当前文件
-f 强行xx的参数。。。

# 2

实用命令：
--1.
docker ps|grep business
--2.
docker exec -it convoy_jsystem_business /bin/bash
--3.查看tomcat运行日志
tail -f /opt/tomcat7/logs/catalina_ln.out

--yum list 		package1 显示指定程序包安装情况package1
--yum install 	package1 安装指定的安装包package1

vi catalina_ln.out
/ sendMsg n
? sendMsg n
:q! 退出vi

通过关键字搜索查看日志
cat jeewx-2015-09-20.log | grep 验证码
查看固定时间日志
cat jeewx-2015-09-20.log | grep '2015-09-20 18:50:15'
查看最近50行日志
tail -n 50 -f catalina.out

Linux查看日志命令总结：
cat
显示整个文件
tail
tail 命令用于显示文本文件的末尾几行
head
从文本文件的头部开始查看，head 命令用于查看一个文本文件的开头部分
more
以百分比的形式查看日志
less
跟more功能差不多，只不过less支持前后翻阅文件
