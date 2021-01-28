## Elasticsearch Query DSL

- 빠른 테스트를 위해 docker image 다운로드

    ```bash
    # elasticsearch 이미지 검색
    docker search elasticsearch

    # 이미지 다운로드
    docker pull nshou/elasticsearch-kibana

    # 실행
    docker run -d -p 9200:9200 -p 5601:5601 nshou/elasticsearch-kibana
    ```

- 데이터 입력

    ```json
    # my_index 인덱스에 벌크로 데이터 입력
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

- match_all
    - 해당 인덱스의 모든 도큐먼트를 검색하는 쿼리
    - 다음 두 예제는 결과가 동일

    ```json

    # 쿼리 없이 실행
    GET my_index/_search

    # match_all 쿼리로 실행
    GET my_index/_search
    {
    	"query": {
    		"match_all": {}
    	}
    }
    ```

- match
    - 풀 텍스트 검색에 사용되는 가장 일반적인 쿼리

    ```json
    # message 필드에 dog가 포함된 모든 문서 검색
    GET my_index/_search
    {
    	"query": {
    		"match": {
    			"message": "dog"
    		}
    	}
    }
    ```

    - match 검색에 여러 개의 검색어를 집어넣게 되면 디폴트로 OR 조건으로 검색되어 입력된 검색어 별로 하나라도 포함된 문서를 모두 검색

    ```json
    # match 쿼리로 message 필드에서 quick dog로 검색
    GET my_index/_search
    {
    	"query": {
    		"match": {
    			"message": "quick dog"
    		}
    	}
    }
    ```

    - 검색어가 여럿일 때 검색 조건을 and로 바꾸려면 operator 옵션을 사용할 수 있다.

    ```json
    # match 쿼리 AND 조건으로 quick dog 검색
    GET my_index/_search
    {
    	"query": {
    		"match": {
    			"message": {
    				"query": "quick dog",
    				"operator": "and"
    			}
    		}
    	}
    }
    ```

- match_phrase
    - 입력된 검색어를 순서까지 고려하여 검색 수행
    - "lazy dog"라는 구문을 공백을 포함해 정확히 일치하는 내용 검색

    ```json
    # match_phrase 쿼리로 "lazy dog" 구문 검색
    GET my_index/_search
    {
    	"query": {
    		"match_phrase": {
    			"message": "lazy dog"
    		}
    	}
    }
    ```

    - slop 옵션을 이용하여 지정된 값 만큼 단어 사이에 다른 검색어가 끼어드는 것을 허용

    ```json
    # match_phrase 쿼리에 slop:1로 "lazy dog" 구문 검색
    GET my_index/_search
    {
    	"query": {
    		"match_phrase": {
    			"message": {
    				"query": "lazy dog",
    				"slop": 1
    			}
    		}
    	}
    }
    ```

    - slop 크기를 1로 했기 때문에 lazy와 dog 사이에 jumping이 있는 "Lazy jumping dog" 값도 검색 된다.