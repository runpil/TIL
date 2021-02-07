## JSON
- JSON은 JavaScript Object Notation의 약자로 JavaScript 문법에 영향을 받아 개발된 데이터 표현 방식
- JSON은 데이터를 교환하는 한 포멧으로 단순함과 유연함 때문에 널리 사용되고 있다.
- 특히 웹 브라우저와 웹 서버 사이에 데이터를 교환하는데 많이 사용되고 있다.
- Python은 기본적으로 JSON 표준 라이브러리를 제공하고 있다.
- JSON 라이브러리를 사용하면, Python 타입의 Object를 JSON 문자열로 변경할 수 있으며, 또한 JSON 문자열을 다시 Python 타입으로 변환할 수 있다.

## JSON 인코딩
- Python Object(List, Tuple, Dictionary 등)를 JSON 문자열로 변경하는 것을 JSON Encoding이라고 한다.
    ```python
    import json

    customer = {
        'id': 12324,
        'name': 'kim',
        'history': [
            {'date': '2021-02-05', 'item': 'Notebook'},
            {'date': '2021-02-07', 'item': 'Mouse'},
        ]
    }

    # JSON 인코딩
    json_string = json.dumps(customer)

    # 문자열 출력
    print(json_string)
    print(type(json_string))
    {"id": 12324, "name": "kim", "history": [{"date": "2021-02-05", "item": "Notebook"}, {"date": "2021-02-07", "item": "Mouse"}]}
    <class 'str'>

    # indent 옵션으로 JSON 문자열 읽기 편하게 설정
    json_string = json.dumps(customer, indent=4)
    print(json_string)
    {
        "id": 12324,
        "name": "kim",
        "history": [
            {
                "date": "2021-02-05",
                "item": "Notebook"
            },
            {
                "date": "2021-02-07",
                "item": "Mouse"
            }
        ]
    }
    ```

## JSON 디코딩
- JSON 문자열을 Python 타입(List, Tuple, Dictionary 등)으로 변경하는 것을 JSON Decoding이라 한다.
    ```python
    import json

    json_string = '{"id": 12324, "name": "kim", "history": [{"date": "2021-02-05", "item": "Notebook"}, {"date": "2021-02-07", "item": "Mouse"}]}'

    # JSON 디코딩
    dict = json.loads(json_string)

    # Dictionary 데이터 체크
    print(dict['name'])
    for i in dict['history']:
        print(i['date'], i['item'])
    kim
    2021-02-05 Notebook
    2021-02-07 Mouse
    ```