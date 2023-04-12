# 메모리 할당 알고리즘

컴퓨터 성능의 발달로 운영체제는 다중 프로그래밍 환경을 제공한다. 다양한 프로그램들이 적재와 종료를 반복하며 메모리 공간은 규칙적이지 않은 빈 공간이 계속 발생한다.(Scattered Holes) 이때 **여러 빈 공간 중 프로세스를 어느 곳에 할당할지 정하는 알고리즘**이 **메모리 할당 알고리즘**이다.  

<br>

Example)
![](https://velog.velcdn.com/images/jimeaning/post/72c8ab6f-5823-482b-bba1-8c49e9435261/image.png)
빈 공간(Scattered Holes)이 있는 메모리  
<br>
노란색 상자 데이터를 각 알고리즘마다 어떻게 저장하는지 보자  
<br>

### 종류
**1) 최초 적합 (First-Fit)**  
메모리를 처음부터 검사해 **가장 첫 번째**로 사용 가능한 공간에 할당한다.  
장점: 빠른 메모리 할당 가능  
단점: 공간 활용률이 떨어짐  

![](https://velog.velcdn.com/images/jimeaning/post/6d6818ff-7b0f-466d-85ea-d891a1d48612/image.png)

<br>

**2) 최적 적합 (Best-fit)**  
메모리 공간 중 프로세스가 들어갈 수 있는 **가장 작은 공간**에 할당해준다.  
장점: 공간 활용률이 높아짐  
단점: 사용 가능한 메모리가 크기 순으로 정렬돼 있지 않으면 메모리 검색 시간이 늘어난다     

![](https://velog.velcdn.com/images/jimeaning/post/0b2cd3dc-ea91-4950-b83c-1d5f132930b2/image.png)

Best-fit이 가장 좋아보이지만 그만큼 처음부터 끝까지 모두 해봐야 한다는 단점이 있다. 비교를 많이 해야 해서 시간이 오래 걸릴 수 있다  

<br>

**3) 최악 적합 (Worst-fit)**  
프로세스 메모리 공간 중 **가장 큰 곳**에 할당한다  
장점: 큰 메모리에 바로 할당하므로 남은 공간이 크다  
단점: 사용 가능한 메모리의 정렬이 필요하고 공간 활용률이 떨어질 수 있다  

![](https://velog.velcdn.com/images/jimeaning/post/d67f5796-eb88-43e7-9261-def77e30d55d/image.png)

Worst-fit도 Best-fit처럼 하나씩 다 스캐닝하고, 메모리 낭비까지 발생하기 때문에 다른 방법에 비해 선호도가 낮다

<br>

#### 참고
[메모리 할당 알고리즘-티스토리](https://mg-princess.tistory.com/141)  
[운영체제의 메모리 할당 알고리즘-티스토리](https://normaldy.tistory.com/13)