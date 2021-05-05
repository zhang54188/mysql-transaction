# mysql-事务隔离级别更改：
  个人使用的是mysql8：
    如果报错：ERROR 1193 (HY000): Unknown system variable 'tx_isolation'就表示你的查询语句的版本过低
    老版本：//查看当前事物级别：SELECT @@tx_isolation;
    新版本：//查看当前事物级别：SELECT @@transaction_isolation;
  设置事务隔离级别：
    //设置read uncommitted级别：
    set session transaction isolation level read uncommitted;
    //设置read committed级别：
    set session transaction isolation level read committed;
    //设置repeatable read级别：
    set session transaction isolation level repeatable read;
    //设置serializable级别：
    set session transaction isolation level serializable;
