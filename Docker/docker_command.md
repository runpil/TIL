
## 빌드하기
```bash
# 실행중인 도커 중지
$ sudo docker-compose stop

# 소스 파일 디렉토리 접속
$ cd ~/src/test_api/notice_board
$ sudo docker build -t notice_board:0.5 --network=host .

$ cd ~/src/test_api/nginx
$ sudo docker build -t nginx:0.2

# 도커 실행
$ sudo docker-compose start
# sudo docker-compose up -d

# 도커 서비스 확인
$ sudo docker-compose ps
```

## 컨테이너 접속
```bash
# 컨테이너 목록 출력
$ docker ps -a

# 컨테이너 접속
$ sudo docker exec -it 4c068fdb3525 /bin/bash
```

## 삭제
```bash
# 컨테이너 삭제
$ sudo docker rm CONTAINER_ID

# 이미지 삭제
$ sudo docker rmi IMAGE_ID

# 모든 이미지 삭제
$ sudo docker image prune -a
```