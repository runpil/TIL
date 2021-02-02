## pycodstyle
- 코드가 PEP 8 가이드에 맞는지 검사해주는 도구
```bash
# 설치
$ pip install pycodestyle

# 출력시 PEP 8을 준수하지 않는 행과 열을 표시
# 오류(error)는 E로 시작, 경고(warning)은 W로 시작
$ pycodestyle cicle.py
circle.py:7:1: E122 continuation line missing indentation or outdented
circle.py:9:1: E901 TokenError: EOF in multi-line statement

# 프로그램 성공적 종료 확인
# 0이 아닌 수의 값을 반환한다면 프로그램이 정상적으로 종료되지 않은 것
$ echo$?
0

# --ignore 옵션을 사용하여 특정 종류의 오류 무시하기
# 파일 내 E9 오류를 무시, 다양한 종류의 오류가 많이 있을 때, 한 번에 한 종류씩 집중해서 해결 가능
$ pycodestyle --ignore=E9 circle.py
```