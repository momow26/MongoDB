#MongoDB数据库学习（01）

---

* 1.安装```mongodb```数据库
```
# 通过 wget从官网下载mongodb，不用构建安装，下载的就是源代码，但需要配置环境变量
wget https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-3.6.5.tgz
# 解归档
gunzip mongodb-linux-x86_64-3.6.5.tgz 
# 解压缩
tar -xvf mongodb-linux-x86_64-3.6.5.tar 
# 修改名字，因为名字太长
mv mongodb-linux-x86_64-3.6.5 mongodb-3.6.5
# cd进入mongodb-3.6.5
cd  mongodb-3.6.5
# cd 进入bin，存放执行文件的 地方
cd bin

# 其中有2个 mongod 和mong
#  mongod是服务器，启动服务器用它，需要指定一个路径，类似一个文件存在数据，bson格式的数据，是二进制的json。好处：每一个键值对之间 ，有一个类似指针（偏移量）的 东西，提取数据性能好，读写 数据，查找数据性能提高
# mongo是客户端 ，启动客户端用它，然后进入交互式环境
# pwd查看文件路径
/root/mongodb-3.6.5/bin
#  一般情况下，Linux 下一般把 文件安装在/usr/local目录下，类似于window下的profile目录
# 移动文件到/usr/local目录下
mv mongodb-3.6.5 /usr/local/
# cd /usr/local/
# cd mongodb-3.6.5/
# cd bin
# pwd,记录下该路径，然后配置环境变量
```
---
* 2.配置环境变量
```
# pwd,记录下该路径
/usr/local/mmongodb-3.6.5/bin
# 返回cd ~ （root目录）
vim .bash_profile
# 设置变量
PATH=$PATH:$HOME/bin:/usr/local/mongodb-3.6.5/bin
# 保存退出，然后执行下，执行命令如下
source .bash_profile
# 执行mongod，默认到根目录找，
# 在根目录下 创建路径，如果不存在，（-p）表示给补上
mkdir -p /data/db
#启动服务器
mongod
# 查看配置好的路径
 echo $PATH
 # 显示如下，即表示配置成功
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin:/usr/local/mongodb-3.6.5/bin
```
---
* 3.连接服务器
```
# 连接服务器命令，在后台运行，这里需要使用阿里云服务器私有ip
 mongod --bind_ip 172.18.41.200 &
# 启动客户端，连接阿里云公网
mongo --host 112.74.172.200
# 连接成功，显示如下，表示客户端启动成功
> db
test
# 尝试新建一个数据库，名为momo
> use momo
switched to db momo
> db
momo
# 帮助命令
mongo --help

# 查看连接是否成功
ps -ef | grep mongo
ps -aux | grep mongo
netstat -ntlp
# 查看mongo启动在哪个端口
netstat -nap | grep mongo
```
---
* 4.在```window```下测试
```
# 在阿里云服务器开27017端口
# 下载一个Robo 3T的mongo插件
# 然后用它连接公网ip
fg %1 # 把服务器拿到前台运行
# 查看ip
ipconfig
```
* 5.mongo语法内容，见下期内容


