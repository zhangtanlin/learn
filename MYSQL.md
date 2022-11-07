# MYSQL
MYSQL

## 特殊用法
可以使用 brew list 软件名 (比如 brew list oclint)确定安装位置。<br>

## 文档
- [mysql设置开机启动](https://blog.csdn.net/Nero_G/article/details/73457249)

## 设置mysql可以远程访问
``` sql
mysql -u root -p
-- 切换到mysql数据库（安装时自带的数据库）
mysql>use mysql;
-- 允许外部访问
mysql>update user set host = '%' where user = 'root';
-- 设置
mysql>select host, user from user;
```
