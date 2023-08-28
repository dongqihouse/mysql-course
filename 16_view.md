# 视图
虚拟存在的表，本身并不包含数据。
仅仅是一个查询语句。


## 删除视图
```sql
# 删除视图
DROP view top10;
```

## 创建视图

```sql
# 创建视图
CREATE view top10
as
SELECT * FROM player ORDER BY level desc limit 10
```

## 修改视图

```sql
# 修改为升序
ALTER view top10 
as
SELECT * FROM player ORDER BY level limit 10;
```
