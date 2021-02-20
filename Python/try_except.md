## try / except
- 빈칸이거나 숫자가 입력되지 않았을 때 traceback 에러가 발생하고 이는 프로그래머가 게으른 것이다.
- traceback 에러는 파이썬이 매우 혼란스럽고 다음에 무엇을 해야하는지 모르는 것을 의미한다. 그래서 파이썬은 멈추고 프로그램도 멈추게 된다.
- 코드에서 프로그램이 중단될 수 있는 부분을 예상할 수 있어야 하고 해결할 수 있어야 한다.
- 위험하고 중단될 수 있는 코드를 try로 감싸면 이 부분이 중단될 수 있으니 실패하면 except 부분을 실행하라는 의미
- 전체에 try블록을 넣지 않고 중단될 것 같은 부분만 try 블록을 넣는다.
- try / except 예시

    ```python
    # traceback 에러 발생
    $ vi try_except.py

    astr = 'Hello Bob'
    istr = int(astr)
    print('First', istr)
    astr = '123'
    istr = int(astr)
    print('Second', istr)

    $ python try_except.py
    Traceback (most recent call last):
        File "try_except.py", line 2, in <module>
        istr = int(astr)
    ValueError: invalid literal for int() with base 10: 'Hello Bob'
    ```

    ```python
    # try / except 로 에러 처리
    $ vi try_except2.py

    astr = 'Hello Bob'
    try:
        istr = int(astr)
    except:  # except 블록은 try 블록이 잘못됐을때만 실행
        istr = -1

    print('First', istr)

    astr = '123'
    try:
        istr = int(astr)
    except:
        istr = -1

    print('Second', istr)

    $ python try_except2.py
    First -1
    Second 123
    ```

    ```python
    # try / except 로 에러 처리
    $ vi try_except3.py

    rawstr = input('Enter a number: ')
    try:
        ival = int(rawstr)
    except:
        ival = -1

    if ival > 0:
        print('Nice work')
    else:
        print('Not a number')

    $ python try_except3.py
    Enter a number: 43
    Nice work

    $ python try_except3.py
    Enter a number: a
    Not a number
    ```