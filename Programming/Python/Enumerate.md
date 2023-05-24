# enumerate()

enumerate() 함수는 기본적으로 인덱스와 원소로 이루어진 튜플(tuple)을 만든다. 따라서 인덱스와 원소를 각각 다른 변수에 할당하고 싶다면 인자 풀기(unpacking)를 해줘야 한다.

```python
>>> for entry in enumerate(['A', 'B', 'C']):
...     print(entry)
...
(0, 'A')
(1, 'B')
(2, 'C')
```

```python
>>> for i, letter in enumerate(['A', 'B', 'C']):
...     print(i, letter)
...
0 A
1 B
2 C
```

<br>

### 시작 인덱스 변경
```python
>>> for i, letter in enumerate(['A', 'B', 'C'], start=1):
...     print(i, letter)
...
1 A
2 B
3 C
```

<br>

#### 참고
[enumerate() 내장 함수로 for 루프 돌리기](https://www.daleseo.com/python-enumerate/)