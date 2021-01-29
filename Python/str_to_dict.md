## 딕셔너리 형태의 문자열을 딕셔너리로 형변환
- 딕셔너리 형태의 문자열을 포함하는 리스트 생성
    ```python
    data = ["{'id': 1, 'name': 'kim'}", "{'id': 2, 'name': 'lee'}", "{'id': 3, 'name': 'moon'}"]
    ```
- 데이터 및 타입 확인
    ```python
    print(data)
    ["{'id': 1, 'name': 'kim'}", "{'id': 2, 'name': 'lee'}", "{'id': 3, 'name': 'moon'}"]

    print(type(data))
    <class 'list'>

    for i in data:
        print(i, type(i)
    {'id': 1, 'name': 'kim'} <class 'str'>
    {'id': 2, 'name': 'lee'} <class 'str'>
    {'id': 3, 'name': 'moon'} <class 'str'>
    ```
- 문자열을 딕셔너리로 형변환
    ```python
    from ast import literal_eval

    for i in data:
        print(literal_eval(i), type(literal_eval(i)))
    {'id': 1, 'name': 'kim'} <class 'dict'>
    {'id': 2, 'name': 'lee'} <class 'dict'>
    {'id': 3, 'name': 'moon'} <class 'dict'>
    ```
- 문자열을 딕셔너리로 형변환 후 키의 값 출력하기
    ```python
    from ast import literal_eval

    for i in data:
        print(literal_eval(i)['id'])
    1
    2
    3
    ```