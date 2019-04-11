
mysql连接错误

1、Authentication type： (mysql8.0.0以上版本)

用户的 Authentication type 默认为 caching_sha2_password，导致数据库连接错误，抛出如下异常：
Illuminate\Database\QueryException : SQLSTATE[HY000] [2054] The server requested authentication method unknown to the client
解决方案：修改密码认证方式
ALTER USER 'youusername'@'localhost' IDENTIFIED WITH mysql_native_password BY 'yourpassword';
