## Python으로 Elasticsearch 연동
### Elasitcsearch package 설치
```
pip install elasticsearch
```
### Elasticsearch 연결
```python
from elasticsearch import Elasticsearch

userpw = "elastic:elaticpw"
elastic = [
    'https://{}@192.168.30.10:9200'.format(userpw),
    'https://{}@192.168.30.11:9200'.format(userpw),
    'https://{}@192.168.30.12:9200'.format(userpw)
]

es = Elasticsearch(
	elastic, 
	cs_certs=False, 
	verify_certs=False
)
```
### 인덱스 생성
```python
es.indices.create(
    index = "test-es", 
    body = {
        "mappings": {
            "type1": {
                "properties": {
                    "field1": { 
                        "type": "text" 
                      }
                  }
              }
          }
      }
  )
```
### 인덱스 읽기
```python
es.search(
    index = "test-es",
    body = {
        "query": {
            "match_all": {}
        }
    }
)
```
### 인덱스 삭제
```python
es.indices.delete(index = "test-es")
```
### Alias 변경
```python
es.indices.update_aliases (
    {
        "actions": [
            { "add": { "alias": "test", "index": "test-es" } },
            { "remove": { "alias": "test-e", "index": "test-es" } }
        ]
    }
)
```
