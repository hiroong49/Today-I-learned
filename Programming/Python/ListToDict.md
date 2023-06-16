# 리스트에서 딕셔너리로 변환

### 1. Dictionary Comprehension 사용

```python
string_list = ['A','B','C']
dictionary = {string : 0 for string in string_list}
print(dictionary)
```

```python
{'A': 0, 'B': 0, 'C': 0}
```

이 방법을 조금 변경하면

```python
string_list = ['A','B','C']
dictionary = {string : i for i,string in enumerate(string_list)}
print(dictionary)
```

```python
{'A': 0, 'B': 1, 'C': 2}
```

value값을 1씩 증가하도록 표현하는 딕셔너리도 가능하다.

*enumerate*  
기본적으로 인덱스와 원소로 이루어진 튜플(tuple)을 만들어주는 함수  
(자세한 내용은 [이 곳](https://github.com/jimeaning/Today-I-learned/blob/main/Programming/Python/Enumerate.md) 참고..)


<br>

### 2. dict.fromkeys(key, value) 이용

```python
string_list = ['A','B','C']
dictionary = dict.fromkeys(string_list,0)
print(dictionary)
```

```python
{'A': 0, 'B': 0, 'C': 0}
```

value에 아무것도 적지 않으면 value는 None이 된다

```python
string_list = ['A','B','C']
dictionary = dict.fromkeys(string_list)
print(dictionary)
```

```python
{'A': None, 'B': None, 'C': None}
```

<br>

### list의 값을 value로 갖는 dict 만들기

1번 방법에서 key와 value가 바뀌는 상태

```python
string_list = ['A','B','C']
dictionary = {i : string_list[i] for i in range(len(string_list))}
print(dictionary)
```


```python
{0: 'A', 1: 'B', 2: 'C'}
```

<br>

#### 참고
[List to Dict (리스트를 딕셔너리로 변환) 총 정리!! -티스토리](https://security-nanglam.tistory.com/427)