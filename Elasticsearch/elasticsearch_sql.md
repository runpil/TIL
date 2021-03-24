## Elasticsearch에서 SQL 사용하기
### 1줄로 표현
```
GET _sql?format=txt
{
    "query": "SELECT * FROM user"
}
```

### 여러줄로 표현
```
GET _sql?format=txt
{
    "query": """
    SELECT country, gender, COUNT(1) count
    FROM user
    WHERE country IN ('UK', 'US')
    GROUP BY country, gender
    ORDER BY country DESC
    """
}
```

### 지원하는 format (기본값은 json)
```
GET _sql?format=txt
GET _sql?format=json
GET _sql?format=yaml
```