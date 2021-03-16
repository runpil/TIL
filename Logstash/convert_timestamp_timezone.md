## Convert timestamp timezone in Logstash for output index name

```json
filter {
  ruby {
        init => "require 'time'"
        code => "event.set('indexDate', Time.now.utc.getlocal.strftime('%Y%m%d'))"
    }
}

output {
  elasticsearch {
    hosts => ["xxx.xxx.xxx.xxx"]
    index => "indexName.%{indexDate}"
  }
}
```