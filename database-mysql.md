### 数据库设计
- 每张表的建表语句中必须包含创建时间（created_at）和更新时间（updated_at）两个字段
- 时间字段的精度CURRENT_TIMESTAMP(3)
- 默认添加外键索引（命名i_xxx），默认没有外键约束
- 若业务规则中明确指定字段不能重复，则需要加对应的UNIQUE INDEX（命名uni_xxx_xxx）
- 表中字段若为VARCHAR类型，用空字符串```NOT NULL DEFAULT ''```代替```NULL```。这样可以统一查询语句，无需针对null或non-null额外处理
