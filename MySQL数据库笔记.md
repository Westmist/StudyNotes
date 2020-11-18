#### 一、数据约束
|关键字|作用|
|:---:|:---:|
UNSIGNED|无符号约束
DEFAULT|默认值约束
ZEROFILL|0填充约束
NOT NULL|非空约束
UNIQUE KEY()|唯一性约束
FOREIGN KEY()|外键约束
PRIMARY KEY()|主键约束

#### 二、查询函数
|方法|作用|
|:---:|:---:|
SELECT NOW()|查询当前时间
SELECT DATABASE()|查询当前的数据库
SELECT WARNING()|查询警告

#### 三、查询命令
|命令|作用|
|:---:|:---:|
SHOW DATABASES|显示所有数据库
SHOW TABLES|显示当前数据库下的所有表
SHOW CREATE TABLE tablename|显示建表语句
SHOW INDEX FROM tablename|显示索引

#### 四、表头操作
* 显示表头信息
> SHOW COLUMNS FROM table
* 表头添加单列
> ALTER TABLE tablename ADD field TYPE [AFTER] tablefiled
* 表头添加多列
> ALTER TABLE tablename ADD (field1 TYPE,field2 TYPE)
* 表头删除单列
> ALTER TABLE tablename DROP field
* 表头删除多列
> ALTER TABLE tablename DROP field1, DROP field2
* 修改表头字段及其约束
> ALTER TABLE tablename CHANGE oldfield newfield NEWTYPE [约束]
* 表头设置索引(索引提高了查询效率但降低了删改整的效率)
> ALTER TABLE tablename ADD INDEX index_name(field);
---
##### 表头约束
* 表头字段添加主键
> ALTER TABLE tablename ADD PRIMARY KEY(field)
* 表头字段添加单个唯一约束
> ALTER TABLE tablename ADD UNIQUE KEY(field)
* 表头字段添加多个唯一约束
> ALTER TABLE tablename ADD UNIQUE KEY(field1,field2)
* 表头字段添加外键约束
> ALTER TABLE tablename ADD FOREIGN KEY(slavefield) REFERENCES mastertable(masterfield)
* 设置默认值
> ALTER TABLE tablename ALTER field SET DEFAULT value
* 删除默认值设置
> ALTER TABLE tablename ALTER field DROP DEFAULT
* 删除主键约束，数据表必须要有一个主键，若删除会自动将下一列设为主键
> ALTER TABLE tablename DROP PRIMARY KEY
* 删除唯一约束
> ALTER TABLE tablename DROP UNIQUE KEY
* 删除外键约束 (MKEYID 为外键id可通过建表语句查看)
> ALTER TABLE tablename DROP FOREIGN KEY MKEYID

#### 五、数据表操作
* 外键引用
> FOREIGN KEY(slavefield) REFERENCES mastertable(masterfield)
* 修改表名称
> ALTER TABLE srctablename RENAME destablename
---
##### 增删改查
* 排序查询(根据fieldA正序查询,如果fieldA相同,则根据fieldB倒序排序)
> SELETC * FROM tablename ORDER fieldA ASC,fieldB DESC
 * 分页查询(对于查询结果越过num1条记录,显示num2条记录)
> SELECT * FROM tablename LIMIT num1,num2
* 联合查询
> SELECT * FROM tablename1 UNION SELECT * FROM tablename2
* 分组查询
> SELECT * FROM tablename GROUP BY (field)
---
#### 聚合函数
* 求平均数并保留小数点后的num位
> ROUND(AVG(field),num)