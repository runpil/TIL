## 'tqdm 패키지'로 for문 진행 상황 확인하기
- for문을 사용하면 작업이 진행 중인지, 얼마나 완료된 것인지 궁금할 때가 있다.
- print 해서 볼 수도 있지만, tqdm 패키지를 이용하면 쉽게 고품질의 상태바를 출력할 수 있다.
- tqdm 패키지 설치
  ```bash
  $ pip install tqdm
  ```
- tqdm 패키지로 for문 진행 상황 확인하기
    ```python
    import time
    import random
    from tqdm import tqdm

    for i in tqdm(range(1, 100)):
        time.sleep(random.randrange(1, 10))
    ```
