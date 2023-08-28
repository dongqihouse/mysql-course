# 表关联
## 使用Join On

```sql
# 表关联
# 1. 内连接 INNER JOIN 交集
SELECT * FROM player
inner join equip
on player.id = equip.player_id;
# 2. 左连接 LEFT JOIN 左表中所有的是数据     
# 3. 右连接 RIGHT JOIN 右表中所有的是数据
```

## 使用where

```sql
# 表关联还可以用where作为关键字,相当于内连接
SELECT * FROM player p, equip e
WHERE  p.id = e.player_id;
```

如果不指定条件或者条件错误，就会产生笛卡尔积，
导致大量数据
