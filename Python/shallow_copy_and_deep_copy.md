## 얕은 복사(Shallow Compy)와 깊은 복사(Deep Copy)
- 얕은 복사
  - 새로운 복합 객체를 만들고, (가능한 범위까지) 원본 객체를 가리키는 참조를 새로운 복합 객체에 삽입한다.
  - 얕은 복사 예제
    ```python
    import copy

    a = ["kim", "lee", "park", "moon"]
    b = copy.copy(a)  # 얕은 복사
    b[2] = 'yoon'

    print('a = ', a)
    print('b = ', b)
    a =  ['kim', 'lee', 'park', 'moon']
    b =  ['kim', 'lee', 'yoon', 'moon']
    ```
    - 변수 b의 요소를 변경해도 a는 변경이 발생하지 않는다.
  - 리스트 요소로 리스트를 포함시킨 변수를 얕은 복사
    ```python
    import copy

    a = ["kim", "lee", ["park", "moon"]]
    b = copy.copy(a)  # 얕은 복사
    b[2][1] = 'yoon'

    print('a = ', a)
    print('b = ', b)
    a =  ['kim', 'lee', ['park', 'yoon']]
    b =  ['kim', 'lee', ['park', 'yoon']]
    ```
    - 복사한 변수 b를 수정하니 a까지 수정이 된다. 
    - 내부 객체까지 복사해오지 않고 공유하는 결과가 나온다.

- 깊은 복사
  - 새로운 복합 객체를 만들고, 재귀적으로 원본 객체의 사본을 새로 만든 복합 객체에 삽입한다.
  - 얕은 복사의 약점인 내부 객체까지도 복사해서 새롭게 대입한다.
  - 깊은 복사 예시
  ```python
    import copy

    a = ["kim", "lee", ["park", "moon"]]
    b = copy.deepcopy(a)  # 깊은 복사
    b[2][1] = 'yoon'
    
    print('a = ', a)
    print('b = ', b)
    a =  ['kim', 'lee', ['park', 'moon']]
    b =  ['kim', 'lee', ['park', 'yoon']]
  ```
