## LIKE 검색시 대괄호 처리 방법
```sql
select col1, col2
from test_table
where like ('%' + replace(col1, '[', '[[]') + '%')
```