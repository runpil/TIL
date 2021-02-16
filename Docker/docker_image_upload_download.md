## 도커 이미지 업로드 & 다운로드
- 도커 이미지 업로드
  ```bash
  # 도커 허브 접속
  sudo docker login
  id / pw

  # build
  sudo docker build -t test_web:0.03 .

  # tag 생성
  sudo docker tag test_web:0.03 testhub/test_web:0.03

  # 이미지 생성 확인
  sudo docker images

  # push
  sudo docker push testhub/test_web:0.03
  ```
- 도커 이미지 다운로드
  ```bash
  # 도커 이미지 다운로드
  sudo docker login

  # 이미지 pull
  sudo docker pull testhub/test_web:0.03

  # 도커 이미지 확인
  sudo docker images
  ```