# Index

### index()
리스트 중에서 특정한 원소가 몇 번째 인덱스에 처음으로 등장했는지를 알려준다. 만약 두 번 이상 원소가 중복되어 존재하는 경우에는 맨 처음 등장하는 인덱스를 출력한다.

> list.index(searchvalue)

<br>

```python
>>> a = [123, 421, 212, 11, 24, 102, 29, 92, 10]

>>> a.index(421)
1
```

<br>

### indexOf()

특정 문자의 위치를 찾기 위해서 사용하는 함수이다.

> list.indexOf(searchvalue[, position])
- indexOf 함수는 리스트에서 특정 문자열(searchvalue)를 찾고, 검색된 문자열이 '첫 번째로' 나타내는 위치 index를 리턴한다.
- 파라미터
  - searchvalue : 필수. 찾을 문자열
  - positon : optional. 기본값은 0. searchvalue를 찾기 시작할 위치
- 찾는 문자열이 없으면 -1을 리턴한다
- 문자열을 찾을 때 대소문자를 구분한다

<br>

- 예시
```python
# 배열에서 2가 처음으로 나타나는 위치의 인덱스 값을 리턴한다

print(arr.indexOf(2))
```

- position 값을 입력한 경우
```python
# 배열에서 1번 째 인덱스부터 2가 처음으로 나타나는 위치의 인덱스 값을 리턴한다

print(arr.indexOf(2), 1)
```

<br>

### lastIndexOf()

리스트 뒤에서부터 searchvalue가 처음으로 발견된 위치의 인덱스를 반환한다. 발견하지 못하면 -1을 반환한다.

> list.lastIndexOf(searchValue[, fromIndex])

- 매개변수
  - searchValue : 필수. 찾고자 하는 문자열. 대소문자 구분.
  - fromIndex : optional. 검색을 시작할 인덱스로 기준을 지정할 수 있다. 만약 음수거나 리스트의 길이보다 크면 전체를 검사한다.


<br>

- 예시
```python
str = 'Brave new world';

print('The index of the first w from the beginning is ' + str.indexOf('w'))
// output>  8

print('The index of the first w from the end is ' + str.lastIndexOf('w')) 
// output>  10

print('The index of "new" from the beginning is ' + str.indexOf('new'))
// output>  6

print('The index of "new" from the end is ' + str.lastIndexOf('new'))
// output>  6
```

<br>

#### 참고
[list.index()란?](https://m.blog.naver.com/sw4r/221976911807)  
[특정 문자 위치 찾기 indexOf](https://hianna.tistory.com/379)