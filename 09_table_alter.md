## Alter

```sql

DESC player;

ALTER TABLE player MODIFY COLUMN name VARCHAR(200);
ALTER table player modify column level Int default 1;
ALTER table player rename column name to nick_name;
ALTER table player add column last_login datetime; 
ALTER table player drop column last_login;
DROP table player;
```

alter table的操作
1. 增 add column
2. 删 drop column
3. 改 rename to 和 modify column
   1. modify操作可以增加默认值