<!--
 * @Author: your name
 * @Date: 2020-04-01 19:10:32
 * @LastEditTime: 2020-09-23 06:13:43
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \undefinedd:\Github\Xmind-and-md\md\mysql\mysql.md
 -->
## 注释:
1. 单行注释
   1. -- 注释内容
   2. #注释内容(mysql特有)
2. 多行注释
   1. /*注释内容*/
## SQL分类
1. DDL(Data Definition Language)数据定义语言//用来定义数据库对象:数据库，表，列等。关键字:create,drop,alter等
2. DML(Data Manipulation Language)数据操作语言//用来对数据库中的表数据进行增删改查关键字:insert,delect,update
3. DQL(Data Query Language)数据查询预言//用老查询数据库中表的记录(数据).关键字:select,where等
4. DCL(Data Control Language)数据控制语言(了解)//授权
## 查询
show create database mysql;查询mysql的字符集
create database 数据库名 character set GBK;创建数据库并设置字符集为GBK
clter database 数据库名 character set utf8;修改指定数据库字符集为utf8
select database();查询当前正常使用的数据库名称
desc 表名；查询表结构

## 增加
create table 新表名 like 原表名;复制表
## 修改
alter table 表名 rename to 新表名;
alter table 表名 character set 字符集;
alter table 表名 add 列名 数据类型
alter table 表名 change 列名 新列名 新数据类型;
alter table 表名 modify 列名 型数据类型;
alter table 表明 drop 列名


limit//分页限定

运算符:
>,<,<=,>=,=,<>
BETWEEN...AND
IN(集合)
LIKE
IS NULL
and 或 &&
or 或 ||
not 或 !

聚合函数:
count 计算个数
max 最大值
min 最小值
sum 和
avg 平均值



列名为主键，count(列名)会比count(1)快  
列名不为主键，count(1)会比count(列名)快  
如果表多个列并且没有主键，则 count（1） 的执行效率优于 count（*）  
如果有主键，则 select count（主键）的执行效率是最优的  
如果表只有一个字段，则 select count（*）最优。

## 外键约束
1. 在创建表的时候添加外键
```sql
create table 表名(
   ···
   外键列
   constraint 外键名称 foreign key (外键列名称) references 主键名称(主键列名称);
)
```
2. 删除外键
```sql
ALTER TABLE 表名 DROP FOREIGN KEY 外键名称;
```
3. 创建表之后添加外键
```sql
ALTER TABLE 表名 ADD CONSTRAINT 外键名称 FOREIGN KEY (外键字段名称) REFERENCES 主键名称(主表列名称);
```
## 级联更新与删除
```sql
ALTER TABLE 表名 ADD CONSTRAINT 外键名称 FOREIGN KEY (外键字段名称) REFERENCES 主键名称(主表列名称) ON UPDATE CASCADE;
```
```sql
ALTER TABLE 表名 ADD CONSTRAINT 外键名称 FOREIGN KEY (外键字段名称) REFERENCES 主键名称(主表列名称) ON DELETE CASCADE;
```
```sql
ALTER TABLE 表名 ADD CONSTRAINT 外键名称 FOREIGN KEY (外键字段名称) REFERENCES 主键名称(主表列名称) ON UPDATE CASCADE ON DELETE CASCADE;
```

## 三大范式
1. 第一范式(1NF): 每一列都是不可分割的原子数据项
2. 第二范式(2NF): 在1NF基础上,非码属性必须依赖于码(在1NF基础上消除非主属性对主码的部分函数依赖)
   1. 函数依赖:A-->B,如果A属性(属性组)的值,可以确定唯一B属性的值。则称B依赖于A
      - 例:学号-->姓名。 (学号,课程名称)-->分数
   2. 完全函数依赖:A-->B,如果A是一个属性组,则B属性值的确定需要依赖A属性组中的所有属性值
      - 例:(学号,课程名称)-->分数
   3. 部分函数依赖:A-->B,如果A是一个属性组,则B的属性值的确定只需要依赖于A属性组中的某一些值即可。
      - 例:(学号,课程名称)-->姓名
   4. 传递函数依赖:A-->B,B-->C.如果通过A属性(属性组)的值,可以确定唯一B属性的值,可通过B属性(属性组)的值可以确定唯一C属性的值,则称C传递函数依赖与A
      - 例:学号-->系名,系名-->系主任
   5. 码:如果在一张表中,一个属性或属性组,被其他所有属性所完全依赖,则称这个属性(属性组)为该表的码
      - 例:该表中的码为:(学号,课程名称)
        - 主属性:码属性组中的所有属性
        - 非主属性:除过码属性组的属性
3. 第三范式(3NF): 在2NF基础上,任何非主属性不依赖于其他非主属性(在2NF基础上消除传递依赖)

## 备份与恢复
备份:mysqldump -u用户名 -p密码 数据库名称 > 保存的路径
还原:登录数据库后(手动创建一个数据库):source 文件路径

## 多表查询
1. 内连接
   1. 隐式内连接:使用WHERE条件消除无用数据
   2. 显式内连接:SELECT 字段列表 from 表名1 【inner】 join 表名2 on 条件
2. 外连接
   1. 左外连接
      - SELECT 字段列表 FROM 表1 LEFT 【OUTER】 JOIN 表2 ON 条件
   2. 右外连接
      - SELECT 字段列表 FROM 表1 RIGHT 【OUTER】 JOIN 表2 ON 条件
   3. 全外连接(Mysql不支持)
      - SELECT * FROM 表1 FULL OUTER JOIN 表2 ON 条件

## 用户管理
- CREATE USER '用户名'@'主机名' INENTIFIED BY '密码';//添加
- DROP USER '用户名'@'主机名;//删除
- UPDATE USER SET PASSWORD = PASSWORD('密码') WHERE USER = '用户名';//修改密码
- SET PASSWORD FOR '用户名'@'主机名' = PASSWORD('新密码');//修改密码

## 权限管理
- SHOW GRANTS FOR '用户名'@'主机名';//查询
- GRANT 权限列表 ON 数据库名.表名TO '用户名'@'主机名';//添加
- GRANT ALL ON *.* TO '用户名'@'主机名';//授予全部权限
- REVOKE 权限列表 ON 数据库名.表名 FROM '用户名'@'主机名';

## other
- UNION语句:用于将不同表中的相同列中查询的数据展示出来;(不包括重复数据)
- UNION ALL语句:用于将不同表中相同列中查询的数据展示出来;(包括重复数据)

## 建表关键字
Mysql关键字|含义
:-:|:-:
NULL|数据可包含NULL值
NOT NULL|数据不可包含NULL值
DEFAULT|默认值
PRIMARY KEY|主键
AUTO_INCRMENT|自动递增用于整数类型
UNSIGNED|无符号
CHARACTER SET name|指定一个字符集


## 严格数据类型与近似数据类型
1. 严格数据类型
> INEGER、SMALLINT、DECIMAL、NUMERIC
2. 近似数据类型
> FLOAT、REAL、DOUBLE PRECISION

## 数据库元数据
命令|描述
:-:|:-:
SELECT VERSION()|服务器版本信息
SELECT DATABASE()|当前数据库名或返回空
SELECT USER()|当前用户名
SHOW STATUS|服务器状态
SHOW VARIABLES|服务器环境变量

## 索引
1. 普通索引
   1. 创建索引
   > CREATE INDEX 索引名称 ON 表名(字段名(length))
   1. 修改索引
   > ALTER TABLE 表名 ADD INDEX 索引名(字段名)
   1. 创建表时指定
   ```sql
   CREATE TABLE 表名(
      ID NOT NULL,
      username varchar(16) NOT NULL,
      INDEX [索引名字] (字段名(length))
   );
   ```
   1. 删除索引
   > DROP INDEX [索引名称] ON 表名;
2. 唯一索引
   1. 创建索引
   > CREATE UNIQUE INDEX 索引名称 ON 表名(字段名(length));
   2. 修改索引
   > ALTER table 表名 ADD UNIQUE [索引名] (字段名(length))
   3. 创建表时指定
   ```sql
   CREATE TABLE 表名(
      ID INT NOT NULL,
      username varchar(16) NOT NULL,
      UNIQUE [索引名称] (字段名(length))
   )
   ```
3. other
> AlTER TABLE 表名 ADD PRIMARY KEY (列名)
该语句添加一个主键，这意味着索引值必须唯一的且不能为NULL
>ALTER TABLE 表名 ADD UNIQUE 索引名(列名)
这条语句创建的索引的值必须是唯一的(除了NULL外，NULL可能会出现多次)
>ALTER TABLE 表名 ADD INDEX 索引名(列名)
添加普通索引,索引值可出现多次
>ALTER TABLE 表名 ADD FULLTEXT 索引名(列名)
该语句指定了索引为FULLTEXT,用于全文索引.