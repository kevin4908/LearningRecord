# ubuntu 下 mysql 5.7的安装
### 1. 安装服务端和客户端
```shell
sudo apt-get install mysql-server -y
sudo apt-get install mysql-client -y
sudo apt-get install libmysqlclient -y
```
如果中途有问题就执行下 ```sudo apt-get update ```

在执行``` sudo apt-get install mysql-server -y``` 时，会让输入root用户密码，输入两次，请牢记

### 2. 查询是否安装成功
``` sudo netstat -tap | grep mysql ```
查询结果有mysql表示安装成功

### 3. 设置mysql远程访问
编辑mysql配置文件，把其中 bind-address = 127.0.0.1 注释掉

```sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf```

使用root用户进入mysql命令行，密码在安装时设置的不要忘记哦

```mysql -uroot -proot```

```mysql> GRANT ALL PRIVILEGES ON *.* TO root@'%' IDENTIFIED BY 'root';```

```*.*```:第一个*代表数据库名;第二个*代表表明。
```root```代表授权的账户名称。
 ```'%'``` : 代表授权的账户IP可以指定，这里代表任意IP都可以访问。
 最后一个```root```是设置当前账户的密码

### 4. 重启```mysql```
重启命令: ``` sudo service mysql restart```

服务管理命令
启动: ``` sudo service mysql start```

停止: ``` sudo service mysql stop```

服务状态: ``` sudo service mysql status```