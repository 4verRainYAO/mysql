# Mysql常用语句

## 1.DDL语句，数据定义语言

### （1）CREATE

建表

```sql
CREATE TABLE PERSON(
 id INT(11) PRIMARY KEY AUTO_INCREMENT COMMENT '人员编号',
 `name` VARCHAR(50) NOT NULL COMMENT '姓名',
 sex VARCHAR(50) NOT NULL COMMENT '性别',
 age INT(20) NOT NULL COMMENT '年龄',
 rank VARCHAR(50) NOT NULL COMMENT '等级',
 department VARCHAR(100) NOT NULL COMMENT '所在部门'
)COMMENT '人员信息表';

//创建表并增加约束
CREATE TABLE 表名称 (
      字段1 类型1 约束1 约束1,
      字段2 类型2 约束2 约束2 
)
```

建库

```sql
create database test
```

#### 常见的表的约束条件

|    约束条件    |      说明      |
| :------------: | :------------: |
|  PRIMARY KEY   |    标识主键    |
|  FOREIGN KEY   |    标识外键    |
|    NOT NULL    |    不能为空    |
|     UNIQUE     | 标识属性值唯一 |
| AUTO_INCREMENT |    属性自增    |
|    DEFAULT     |  为属性默认值  |



### (2)DROP

```sql
DROP DATABASE 数据库名
DROP TABLE 表名
DROP TABLE if exits 表名 
```

### (3)ALTER

#### 添加字段

```sql
ALTER TABLE 表名称 ADD 字段名 字段类型 字段约束
ALTER TABLE 表名称 ADD COLUMN 字段名 字段类型 字段约束
```

#### 修改表名

```sql
ALTER TABLE 修改前表名称 RENAME 修改后表名称
```

#### 添加索引

```sql
ALTER TABLE 表名称 ADD INDEX 索引名称 (字段名)
```

#### 禁用和启用约束

```sql
//禁用约束
ALTER TABLE 表名称 DISABLE KEYS
//启用约束
ALTER TABLE 表名称 ENABLE KEYS
```

#### 删除表字段、主键、索引、外键约束

```sql
//删除表字段
ALTER TABLE 表名称 DROP COLUMN 字段名
//删除主键
ALTER TABLE 表名称 DROP PRIMARY KEY
//删除索引
ALTER TABLE 表名称 DROP INDEX 索引的字段名
//删除外键约束
ALTER TABLE 表名称 DROP FOREIGN KEY 外键的字段名
```

### (4)TRUNCATE

清空表

```sql
TRUNCATE TABLE 表名称
```

## 2.DQL语句，数据查询语言

### select

```sql
select * from table_name
```

#### group by 分组：

```sql
select * from table_name group by column_name
SELECT count(*) ,depno from employee where depno=100 GROUP BY depno;
SELECT count(*) ,depno from employee GROUP BY depno HAVING depno=100;
```

#### Having与Where的区别

where必须放在group by之前，表示先过滤在分组；

having必须放在group by之后，表示先分组在过滤，having还可以结合使用一些聚合函数：

**sum()** 求和

**avg()** 平均值

**min()   max() count()**

#### order by 排序：

```sql
SELECT * from employee ORDER BY depno DESC;//降序
SELECT * from employee ORDER BY depno ASC;//升序
SELECT * from employee ORDER BY depno ;//默认升序
```

## 3.DML语句，数据操作语言

### insert

```sql
insert into employee values (8,'cxk',1000,100)
insert into employee(name,salary,depno) VALUES ('laojiu',2000,101)
```

### update

```sql
update employee e set e.name='jitaimei' where e.id=4
```

### delete 

```sql
delete from employee where id=10
DELETE FROM 表名称 WHERE 列名称 = 值
```

## 4.DCL语句，数据控制语言

#### GRANT

#### REVOKE

#### COMMIT

#### ROLLBACK

主要为以上操作即对数据库安全性完整性等有操作的，可以简单的理解为权限控制等。 

