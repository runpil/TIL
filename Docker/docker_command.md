## 이미지 관련
```bash
# 이미지 목록 보기
$ docker images
$ docker image ls

# 이미지 검색
$ docker search [이미지 이름]

# 이미지 받기
$ docker pull [이미지 이름]
$ docker pull [이미지 이름]:[버전]

# 이미지 삭제
$ docker rmi [이미지 ID]

# 모든 이미지 삭제
sudo docker image prune -a
```

## 컨테이너 관련
```bash
# 컨테이너 목록 보기
$ docker ps
$ docker ps -a

# 컨테이너 실행
$ docker run [option] image[:TAG]
ex) docker run -it --name server ubuntu:latest /bin/bash

# 컨테이너 시작
$ docker start [컨테이너 ID 또는 컨테이너 이름]

# 컨테이너 재시작
$ docker restart [컨테이너 ID 또는 컨테이너 이름]

# 컨테이너 접속
$ docker attach [컨테이너 ID 또는 컨테이너 이름]

# 컨테이너 정지
$ docker stop [컨테이너 ID 또는 컨테이너 이름]
# Bash Shell에서 exit 또는 Ctrl + D 입력하면 컨테이너 정지
# Ctrl + P + Q 입력하면 컨테이너 빠져나오기

# 컨테이너 삭제
$ docker rm [컨테이너 ID 또는 컨테이너 이름]

# 모든 컨테이너 삭제
$ docker rm `docker ps -a -q`
# 
```

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