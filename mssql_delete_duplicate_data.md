## 중복된 데이터 하나만 남기고 삭제

```sql
delete pc
-- select *
from (
       select row_number() over(partition by counterdate order by counterdate) as row_number
            , counterdate, countervalue
       from perfmon.dbo.perfmon_counter
) as pc
where row_number > 1
```