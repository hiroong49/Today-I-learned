# sort()와 sorted()

### sort()
>리스트명.sort()

sort()는 리스트형의 메소드이다. 리스트 원본값을 직접 수정한다. 정렬된 값은 리턴되지 않고 원본 리스트 값이 정렬된 값으로 수정된다.

<br>

### sorted()
>sorted(리스트명)

sorted()는 내장 함수이다. 리스트 원본값은 그대로이고 정렬 값을 반환한다. 원본 리스트는 유지되고 정렬된 새 리스트가 저장된다.

따라서 sorted()는 메모리 사용량이 두 배로 늘어난다. 따라서 속도는 sort()가 더 빠르다.

<br>

랜덤 데이터

![](https://velog.velcdn.com/images/jimeaning/post/4ee4ed23-8fdc-4237-984c-4babcbadf01e/image.png)


<br>


#### 참고
[정렬 속도 비교](https://www.acmicpc.net/blog/view/58)  
[sorted()와 sort()의 차이 -티스토리](https://hyoveloper.tistory.com/entry/sorted%EC%99%80-sort%EC%9D%98-%EC%B0%A8%EC%9D%B4)  
[sort(), sorted() 차이](https://blog.naver.com/PostView.naver?blogId=wideeyed&logNo=221745416992)
