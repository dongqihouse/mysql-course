## Create

create的基本语法

create table table_name (
    row_name row_type
);

```sql
use game1;

CREATE TABLE player (
	id INT,
	name VARCHAR(200),
	level INT,
	exp INT,
	gold DECIMAL(10, 2)
);
```