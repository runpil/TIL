## highlighting 옵션
- highlighting 옵션은 사용자가 입력한 검색어를 강조해준다.
- 검색 결과는 _source 필드가 아닌 별도의 highlight라는 필드를 통해서 결과가 제공된다.
- 데이터 입력
```
POST my_index/_bulk
{"index":{"_id":1}}
{"message":"The quick brown fox"}
{"index":{"_id":2}}
{"message":"The quick brown fox jumps over the lazy dog"}
{"index":{"_id":3}}
{"message":"The quick brown fox jumps over the quick dog"}
{"index":{"_id":4}}
{"message":"Brown fox brown dog"}
{"index":{"_id":5}}
{"message":"Lazy jumping dog"}
```
- hightlighting 옵션 사용
```
GET my_index/_search
{
  "query": {
    "match": {
      "message": "quick dog"
    }
  },
  "highlight": {
    "fields": {
      "message": {}
    }
  }
}
```
- 결과 확인
  - 
 ```
 {
  "took" : 56,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 5,
      "relation" : "eq"
    },
    "max_score" : 0.87627405,
    "hits" : [
      {
        "_index" : "my_index",
        "_type" : "_doc",
        "_id" : "3",
        "_score" : 0.87627405,
        "_source" : {
          "message" : "The quick brown fox jumps over the quick dog"
        },
        "highlight" : {
          "message" : [
            "The <em>quick</em> brown fox jumps over the <em>quick</em> <em>dog</em>"
          ]
        }
      },
      {
        "_index" : "my_index",
        "_type" : "_doc",
        "_id" : "2",
        "_score" : 0.6744513,
        "_source" : {
          "message" : "The quick brown fox jumps over the lazy dog"
        },
        "highlight" : {
          "message" : [
            "The <em>quick</em> brown fox jumps over the lazy <em>dog</em>"
          ]
        }
      },
      {
        "_index" : "my_index",
        "_type" : "_doc",
        "_id" : "1",
        "_score" : 0.6173784,
        "_source" : {
          "message" : "The quick brown fox"
        },
        "highlight" : {
          "message" : [
            "The <em>quick</em> brown fox"
          ]
        }
      },
      {
        "_index" : "my_index",
        "_type" : "_doc",
        "_id" : "5",
        "_score" : 0.35847887,
        "_source" : {
          "message" : "Lazy jumping dog"
        },
        "highlight" : {
          "message" : [
            "Lazy jumping <em>dog</em>"
          ]
        }
      },
      {
        "_index" : "my_index",
        "_type" : "_doc",
        "_id" : "4",
        "_score" : 0.32951736,
        "_source" : {
          "message" : "Brown fox brown dog"
        },
        "highlight" : {
          "message" : [
            "Brown fox brown <em>dog</em>"
          ]
        }
      }
    ]
  }
}
```
