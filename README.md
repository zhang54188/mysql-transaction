# mysql-事务隔离级别更改：
  个人使用的是mysql8：
    如果报错：ERROR 1193 (HY000): Unknown system variable 'tx_isolation'就表示你的查询语句的版本过低
    老版本：//查看当前事物级别：SELECT @@tx_isolation;
    新版本：//查看当前事物级别：SELECT @@transaction_isolation;
 当前登录的用户使用的隔离级别 如果用户退出就需要重新设置
  用户登录登录状态设置事务隔离级别：
    //设置read uncommitted级别：
    set session transaction isolation level read uncommitted;
    //设置read committed级别：
    set session transaction isolation level read committed;
    //设置repeatable read级别：
    set session transaction isolation level repeatable read;
    //设置serializable级别：
    set session transaction isolation level serializable;
  永久设置mysql事务隔离级别的方法：
    sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf
    本人的是mysql8所以没有transaction_isolation这个属性 所以我直接添加了个transaction_isolation = READ-COMMITTED（这个是隔离级别名字可以字节选择 我使用的是大写 笔者没有尝试小写 有兴趣下留言
    然后重启service mysql restart没报错的情况下就可以了


  如果重启报错：Job for mysql.service failed because the control process exited with error code.
    See "systemctl status mysql.service" and "journalctl -xe" for details.
   可以按照提示journalctl -xe查看日志分析 这个分析错误地方太多 笔者就不多说了
