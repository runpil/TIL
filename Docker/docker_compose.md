## Docker Compose
- 여러 개의 컨테이너(container)로 구성된 애플리케이션을 관리하기 위한 간단한 오케스트레이션(Orchestration) 도구
- 예시

    ```bash
    # docker-compose.yml

    version: '3'

    services:
        database:
        image: mysql:5.7.27
        ports:
            - 43306:3306
        environment:
            MYSQL_ROOT_PASSWORD: password
        command: [ '--character-set-server=utf8mb4', '--collation-server=utf8mb4_unicode_ci' ]
        redis:
        image: redis:5.0.5
        ports:
            - 46379:6379
        influxdb:
        image: influxdb
        ports:
            - 48086:8086
    ```

    - MySQL, Redis, InfluxDB 각각의 Docker 설정들을 모두 docker-compose.yml 파일에 작성
    - 아래 명령어를 실행하면 해당 Docker container 들을 띄워준다.

        ```bash
        # -d 는 detach 모드로 Docker container 들을 background 에서 돌리도록 함.
        $ docker-compose up -d
        Starting master_database_1 ... done
        Starting master_redis_1    ... done
        Starting master_influxdb_1 ... done
        ```

- 장점
    - 띄우고 내리는 등의 행위가 편하다.
    - Docker 환경이 파일로 관리된다.
    - 협업 하는 모두가 명령어 하나로 쉽게 같은 환경을 사용할 수 있게된다.
- 참고

    [Docker Compose 로 local 개발 환경 쉽게 관리하기](https://blog.gangnamunni.com/post/docker-compose-for-local-env/)