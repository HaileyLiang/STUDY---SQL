# 1. 数据库与SQL基础

DBMS 数据库管理系统
```txt
Database types
|--- 层次数据库HDB (Hierarchical database)
|--- 关系数据库RDB (Relational)
|--- 面向对象数据库 (OODB：Object Oriented database)
|--- XML数据库
|--- 键值存储系统（Key-Value Store， KVS) 如MongoDB
```

数据库中存储的表结构：
- 数据库行 - 记录
- 数据库列 - 字段
- 行列交汇 - 单元格

SQL语句分为三类：
- DDL 针对数据库中的表 进行增删改 CREATE/DROP/ALTER
- DML 针对表中的记录 进行增删改 SELECT/INSERT/UPDATE/DELETE
- DCL 针对用户权限、确认或取消数据库的变更 COMMIT/ROLLBACK/GRANT/REVOKE

```SQL
CREATE DATABASE shop;
CREATE TABLE product(
    product_id CHAR(4) NOT NULL,
    product_name VARCHAR(100) NOT NULL,
    product_type VARCHAR(32) NOT NULL,
    sale_price INTEGER,
    purchase_price INTEGER,
    regist_date DATE,
    primary key(product_id)
);
```

四种基本的数据类型：
- INTEGER
- CHAR 存储定长字符串 会浪费存储空间，一般不使用
- VARCHAR 可变长字符串
- DATE 

约束：除了数据类型之外，对列中存储的数据进行限制或追加条件的功能
- NOT NULL 非空
- PRIMARY KEY 主键约束，代表该列值唯一

语句例子：
```SQL
-- 删除表
DROP TABLE product；

-- 添加列
ALTER TABLE product ADD COLUMN product_name_pinyin VARCHAR(100);

-- 删除列
ALTER TABLE product DROP COLUMN product_name_pinyin;

-- ALTER TABLE 和 DROP TABLE执行后无法恢复

-- 清空表 TRUNCATE 比drop/delete 清楚数据 速度快
TRUNCATE TABLE product；

-- 数据更新
UPDATE product
    SET regist_date = '2009-10-10';

UPDATE product
    SET sale_price = sale_price * 10 WHERE product_type = '厨房用具';

-- NULL清空，与INSERT语句一样，UPDATE也可以将NULL作为值来用，但只有未设置NOT NULL和主键约束的列才可以情况
UPDATE product
    SET regist_date = NULL WHERE product_id = '0008';

-- 多列更新

```
