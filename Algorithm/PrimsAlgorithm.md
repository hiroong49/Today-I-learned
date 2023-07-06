# 프림 알고리즘

무향 연결 그래프가 주어질 때, '최소 신장 트리'라고 부르는 서브 그래프를 찾는 알고리즘이다. [크루스칼 알고리즘]()과 같은 용도이지만 효율성이 달라질 수 있다.

프림 알고리즘은 MST를 찾기 위한 그리디 패러다임의 알고리즘이다. 즉 프림 알고리즘을 통해 최소 신장 트리를 구할 수 있다.

---

**[0]** 임의의 정점을 선택하여 비어있는 T에 포함시킨다. (T는 이제 노드가 한 개인 트리이다)  

![](https://velog.velcdn.com/images/jimeaning/post/acc073e0-4383-43dd-9874-ec61d773c957/image.png)

**[1]** T에 있는 노드와 T에 없는 노드 사이의 간선 중 가중치가 최소인 간선을 찾는다.

![](https://velog.velcdn.com/images/jimeaning/post/d822284c-7706-4070-8fe0-fc7c13c438b1/image.png)

**[2]** 찾은 간선이 연결하는 두 노드 중, T에 없던 노드를 T에 포함시킨다. (1에서 찾은 간선도 같이 T에 포함된다)  

![](https://velog.velcdn.com/images/jimeaning/post/52a47629-723a-4ca6-b9d4-162396bac58e/image.png)


**[3]** 모든 노드가 T에 포함될 때까지 1, 2를 반복한다

![](https://velog.velcdn.com/images/jimeaning/post/a0242aea-217b-47d1-91a1-2781b24e152a/image.png)

이렇게 가중치의 합이 23인 트리가 완성되었고, 이 트리가 그래프의 MST이다.

<br>

**프림 알고리즘 구현 방법**  
1. 배열을 사용해 T와 각 노드를 연결하는 최소 간선 가중치를 찾는 방법.  
   시간 복잡도: O(V^2)
2. 힙을 사용해 최소의 간선 가중치를 찾는 방법.
   시간 복잡도: O(E log E), 즉, O(E log V)  
   V = 정점의 개수, E = 간선의 개수

<br>

#### 참고
[프림 알고리즘 ( Prim's algorithm )](https://www.weeklyps.com/entry/%ED%94%84%EB%A6%BC-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-Prims-algorithm)