# append(), extend(), insert()

### 1. append()
array.append(x) 형태로 사용된다. append는 덧붙인다는 뜻으로, 괄호() 안에 값을 입력하면 array 맨 끝에 객체로 추가된다. 요소를 추가할 때는 객체로 추가하게 되는데, 입력한 값이 리스트와 같은 반복 가능한 iterable 자료형이라도 객체로 저장된다. 

```python
>>> nums = [1, 2, 3]
>>> nums.append(4)
[1, 2, 3, 4]

>>> nums.append([5, 6])
[1, 2, 3, 4, [5, 6]] # 리스트가 하나의 객체로 추가되었음
```

<br>


### 2. extend()
array.extend(iterable) 형태로 사용된다. 입력한 iterable 자료형의 항목 각각을 array 끝에 하나씩 추가한다. append와 동일하게 요소를 array 끝에 추가하지만 다른 점은, 괄호() 안에는 iterable 자료형만 올 수 있다는 것이다. iterable 자료형이 아닌 경우 TypeError가 발생한다.

```python
>>> nums = [1, 2, 3]
>>> nums.extend([4, 5])
[1, 2, 3, 4, 5]  #리스트로 주어진 [4, 5]의 요소가 각각 추가 되었음

>>> a = [10]
>>> nums.extend(a) 
[1, 2, 3, 4, 5, 10]
```

<br>


### 3. insert()
array.insert(i, x) 형태로 사용된다. append와 다르게 원하는 위치에 항목을 추가할 수 있다. array의 원하는 위치 i 앞에 추가할 값 x를 삽입한다. i는 위치를 나타내는 인덱스를 숫자로 입력한다. 음수를 입력하면 배열의 끝을 기준으로 처리된다. 추가할 값 x는 객체로 추가되며 iterable 자료형이라도 객체로 저장된다.

```python
>>> nums = [1, 2, 3]
>>> nums.insert(0, [10, 20])  # 0번째(맨앞에) 추가
[[10, 20], 1, 2, 3]

>>> nums.insert(-1, 100)  # 끝에서 1번째 전에 추가
>>> print(nums)
[[10, 20], 1, 2, 100, 3]  # 리스트 맨 끝에 저장되지 않음

>>> nums = [1, 2, 3]
>>> nums.insert(len(nums), 100)
[1, 2, 3, 100]
```

<br>

#### 참고
[파이썬 append( ), extend( ), insert( ) 함수 차이 -티스토리](https://ooyoung.tistory.com/117)
