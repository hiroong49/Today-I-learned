# sort()와 sorted()

### sort()
>리스트명.sort()

sort()는 리스트형의 메소드이다. 리스트 원본값을 직접 수정한다. 정렬된 값은 리턴되지 않고 원본 리스트 값이 정렬된 값으로 수정된다.


O(NlogN)

<br>

### sorted()
>sorted(리스트명)

sorted()는 내장 함수이다. 리스트 원본값은 그대로이고 정렬 값을 반환한다. 원본 리스트는 유지되고 정렬된 새 리스트가 저장된다.

따라서 sorted()는 메모리 사용량이 두 배로 늘어난다. 따라서 속도는 sort()가 더 빠르다.

O(NlogN)

<br>

랜덤 데이터

![](https://velog.velcdn.com/images/jimeaning/post/4ee4ed23-8fdc-4237-984c-4babcbadf01e/image.png)


<br>

# reverse와 reversed
리스트 안 요소를 뒤집는 기능을 가진 함수이다.

### reverse
- list 타입에서 제공하는 함수
- 값을 반환하지 않고 단순히 해당 list를 뒤섞는다
- O(n)  
  배열에서 각각의 위치를 변경하므로 모든 element의 순서를 교환하기 때문
  
### reversed
- 내장함수로 list에서 제공하는 함수가 아니다
- 딕셔너리는 시퀀셜한 타입이 아니므로 지원하지 않는다.  
  즉, 순차적인 인덱스로 접근할 수 없기 때문에 지원하지 않는다.
- reversed는 'reversed' 객체를 반환한다
- 뒤집어진 리스트의 값을 return 한다.
- O(1)  
  메소드 자체는 O(1)


<br>

#### 참고
[정렬 속도 비교](https://www.acmicpc.net/blog/view/58)  
[sorted()와 sort()의 차이 -티스토리](https://hyoveloper.tistory.com/entry/sorted%EC%99%80-sort%EC%9D%98-%EC%B0%A8%EC%9D%B4)  
[sort(), sorted() 차이](https://blog.naver.com/PostView.naver?blogId=wideeyed&logNo=221745416992)  
[reverse, reversed 차이](https://itholic.github.io/python-reverse-reversed/)  
[reverse, reversed 차이 -velog](https://velog.io/@chae-heechan/Python-reverse-reversed-%EC%B0%A8%EC%9D%B4)  
[reverse()와 reversed()비교 시간복잡도 -티스토리](https://hyerios.tistory.com/24)