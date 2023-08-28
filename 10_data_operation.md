# Insert INTO

```sql
INSERT player (id, name, level, exp, gold) values (0, '张三', 1, 1, 1);
INSERT player values (1, '张三1', 1, 1, 1);
INSERT player (id,name) values (1, '张三1');

INSERT player (id,name) values (2, '张三2'), (3, '李四2');
```

1. keys是可选的，可以不写，也可以写部分key
2. 可以同事增加多组value

## Delete From

```sql
DELETE FROM player where gold=1;
```


## Update

```sql
UPDATE player SET level = 1 WHERE id = 3;
UPDATE player SET level = 1;
UPDATE player SET exp = 2 WHERE exp is NULL;
```

## Select

```sql
select * from player
```

