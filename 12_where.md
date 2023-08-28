# Where 条件语句

### 逻辑运算符
Not > And > OR
```sql
SELECT * FROM player where level > 1 and level < 5 or exp > 1 and exp < 5;
```

可以使用（）改变优先级
```sql
SELECT * FROM player where level > 1 and (level < 5 or exp > 1) and exp < 5;
```

#### In

```sql
SELECT * FROM player where level in (1, 3, 5);
```

#### Between and
```sql
SELECT * FROM player where level BETWEEN 1 AND 5;
```

#### Like 模糊匹配

```sql
SELECT * FROM player where name LIKE '王%';
SELECT * FROM player where name LIKE '王_';
```
1. %匹配任意字段
2. _匹配一个字段


### 正则匹配
1. . 表示任意一个字符
2. ^ 开头 $ 结尾
3. [abc] 匹配其中一个字符
4. [a-z] 匹配范围内一个字符
5. a|b a或b

```sql
SELECT * FROM player where name REGEXP '^王.$';

# zhangsan开头的邮箱
SELECT * FROM player where email REGEXP '^zhangsan';
SELECT * FROM player where email LIKE 'zhangsan%';
# a/b/c开头的玩家
SELECT * FROM player where email REGEXP '^[abc]';
# net结尾的玩家
SELECT * FROM player where email REGEXP 'net$';
SELECT * FROM player where email LIKE '%net';
```
### Null
```sql
# Null 判断
SELECT * FROM player WHERE email is NULL;
SELECT * FROM player WHERE email <=> NULL;
```

### Order by

```sql
# Order by
# order by 默认 asc 升序排列
SELECT * FROM player ORDER BY level;
# 可以显示声明desc为降序
SELECT * FROM player ORDER BY level DESC;
# 并且可以多条件排序，下面是按照等级降序，然后相同的按照经验升序
SELECT * FROM player ORDER BY level DESC, exp ASC;
# 不仅可以使用列名，也可以使用序号
SELECT * FROM player ORDER BY 5 DESC, exp ASC;
```

### 聚合函数

```sql
# 聚合函数
# 1. AVG
SELECT AVG(level) FROM player; 
# 2. COUNT
SELECT COUNT(*) FROM player; 
# 3. MAX
# 4. MIN
# 5. SUM 
```

### Group by 和 HAVING

```sql

# GROUP BY
# 统计性别人数
SELECT sex, COUNT(*)  FROM player GROUP BY sex;
# 等级分组
SELECT level, COUNT(level)  FROM player GROUP BY level;

# HAVING 针对分组后的数据进行过滤
SELECT level, COUNT(level)  FROM player GROUP BY level HAVING COUNT(level) > 4 ORDER BY COUNT(level) DESC
```

###  SUBSTR 和 LIMIT

```sql

# SUBSTR截取字符串
SELECT SUBSTR(name, 1, 1), COUNT(SUBSTR(name, 1, 1)) FROM player
GROUP BY SUBSTR(name, 1, 1)
HAVING COUNT(SUBSTR(name, 1, 1)) >= 5
# limt a, b (参数a 限制的数量，参数b 偏移量)
```


### distint去重

```sql

# distint去重
SELECT DISTINCT sex FROM player;
```


### UNION 交集 INTERSECT 交集 EXCPET 差集

```sql

# union 并集，默认去重，如果不想去重可以使用union all
# 和 or 类似，不过or是合并查询条件，union是合并查询结果
SELECT * FROM player WHERE level > 1 and level < 5  
UNION ALL 
SELECT * FROM player WHERE exp > 1 and exp < 5;

# 交集
SELECT * FROM player WHERE level >= 1 and level <= 3  
INTERSECT  
SELECT * FROM player WHERE exp >= 1 and exp <= 3;

# 差集
SELECT * FROM player WHERE level >= 1 and level <= 3  
EXCEPT  
SELECT * FROM player WHERE exp >= 1 and exp <= 3;
```
