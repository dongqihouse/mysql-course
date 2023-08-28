# Subquery
子查询： 使用一个查询的结果作为
另外一个查询的条件


## 子查询用作where子句
```sql

# 查询大于平均等级的玩家
SELECT * FROM player WHERE level > (SELECT AVG(level) FROM player);
```

## 在Select语句中

```sql

# 查询所有玩家等级和平均等级的差值
SELECT name, level,
ROUND((SELECT AVG(level) FROM player)) as average,
level - ROUND((SELECT AVG(level) FROM player)) as diff
FROM player;
```

这里要注意round里面的子查询`(SELECT AVG(level) FROM player)`一定要用括号括起来。

## 利用子查询来迁移数据

```sql

# 子查询创建新表，并迁移数据
CREATE table new_player1 (SELECT * FROM player WHERE level < 5);
SELECT * FROM new_player1;

# 表创建完成之后，迁移数据
INSERT INTO new_player1 (SELECT * FROM player WHERE level BETWEEN 6 AND 10);
```

## Exists和子查询

```sql

# exist子查询
SELECT EXISTS (SELECT * FROM player WHERE level > 100);
SELECT EXISTS (SELECT * FROM player WHERE level > 1);
```