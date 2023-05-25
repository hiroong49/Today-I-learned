# 순열과 조합

### 순열 permutation
서로 다른 n개에서 r개를 선택할 때 **순서를 고려하여 중복없이** 뽑을 수 있는 경우의 수

순서를 고려하기 때문에 (A, B)와 (B, A)는 다르다.

형식 : **permutations(객체, r)**  
반복 가능한 객체(리스트, 튜플, 문자열) 안에서 r개를 선택한다.  
조건 : from itertools import permutations  

```python
import itertools

arr = ['A', 'B', 'C']
nPr = itertools.permutations(arr, 2)
print(list(nPr))

결과 : [('A', 'B'), ('A', 'C'), ('B', 'A'), ('B', 'C'), ('C', 'A'), ('C', 'B')]
```

<br>

### 조합 combination
서로 다른 n개에서 r개를 선택할 때 **순서를 고려하지 않고 중복없이** 뽑을 수 있는 경우의 수  

순서를 고려하지 않기 때문에 (A, B)와 (B, A)는 같다.

형식 : **combinations(객체, r)**  
반복 가능한 객체(리스트, 튜플, 문자열) 안에서 r개를 선택한다.  
조건 : from itertools import combinations

```python
import itertools

arr = ['A', 'B', 'C']
nCr = itertools.combinations(arr, 2)
print(list(nCr))

결과 : [('A', 'B'), ('A', 'C'), ('B', 'C')]
```

<br>

#### 참고
[순열과 조합 -티스토리](https://pearlluck.tistory.com/468)  
[permuation, combination -벨로그](https://velog.io/@dramatic/Python-permutation-combination-%EC%88%9C%EC%97%B4%EA%B3%BC-%EC%A1%B0%ED%95%A9)