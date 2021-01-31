## 동적으로 변수이름 생성하기
```python
seq = [1, 2, 3]

for i in seq:
    globals()['seq' + str(i)] = 'abc' + str(i)
    print(globals()['seq' + str(i)])
abc1
abc2
abc3
```
```python
print(seq1)
print(seq2)
print(seq3)
abc1
abc2
abc3
```