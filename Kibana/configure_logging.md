## Kibana Error 로그만 남기기

- Kibana는 많은 로그를 남긴다. 그 중 Error 로그만 남기게 하려면 kibana.yml 파일에서 아래의 설정을 하면 된다.
  ```
  vi kibana.yml

  logging.quiet: true
  ```
    - default 값은 모든 로그를 남기는 false 이다.