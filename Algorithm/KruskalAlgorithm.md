# 크루스칼 알고리즘

크루스칼 알고리즘은 그래프 내의 모든 정점들을 가장 적은 비용으로 연결하기 위해 사용된다.

즉, 그래프에는 정점(vertex)과 간선(edge)가 있는데, 간선에 가중치가 포함되어 있다.  
그래프 내의 **모든 정점을 포함하고 사이클이 없는 연결 선을 그렸을 때 가중치의 합이 최소가 되는 상황을 구하고 싶을 때** 크루스칼 알고리즘을 사용한다.  
**최소 신장 트리를 구하기 위한 알고리즘**이다.

<br>

### 신장 트리(Spanning tree)와 최소 신장 트리

**신장 트리의 정의**
> 그래프에서 (1) 모든 정점을 포함하고, (2) 정점 간 서로 연결이 되며 사이클이 존재하지 않는(tree의 기본 조건) 그래프


예를 들어 아래와 같은 그래프가 있을 때

![](https://velog.velcdn.com/images/jimeaning/post/24868c43-dd5c-4e44-9d61-3ba1e7a446c0/image.png)

이러한 신장 트리들이 나올 수 있다.

![](https://velog.velcdn.com/images/jimeaning/post/45353c53-7673-4daa-9fad-2d83ac1d2dc4/image.png)

모든 정점이 포함되어 있으면서, 모든 노드는 적어도 하나의 간선으로 연결되어 있다. 또한 연결 관계에서 사이클을 형성하지 않는다.

따라서 신장 트리는 **정점의 개수가 n일 때, 간선이 n-1개**이다.

이러한 신장 트리들 중에서 가중치의 합이 최소가 되는 신장 트리를 최소 신장 트리라고 한다.

<br>

### 크루스칼 알고리즘의 과정

크루스칼 알고리즘은 **그리디 알고리즘**의 일종이다.

즉 그래프 간선들을 **가중치의 오름차순**으로 정렬하고, **사이클을 형성하지 않는 선에서 정렬된 순서대로 간선을 선택**한다.

---
[1] 그래프 간선을 가중치 오름차순으로 정렬한다.

![](https://velog.velcdn.com/images/jimeaning/post/45159f92-0747-4ae8-8709-9e251af8359f/image.png)

[2] a-b부터 선택한다

![](https://velog.velcdn.com/images/jimeaning/post/858c9fac-2882-4799-b9d8-1a387dacf779/image.png)


[3] a-d를 선택한다

![](https://velog.velcdn.com/images/jimeaning/post/afaafb21-0752-4741-87e1-b64abdb13627/image.png)

[4] b-d를 선택하면 a-b-d 사이클이 형성되므로 선택하지 않고, b-c를 선택한다. 

![](https://velog.velcdn.com/images/jimeaning/post/bc63e11c-bf2f-40c1-8431-3cd34b093e74/image.png)

[5] 선택된 간선의 개수가 정점의 개수-1만큼 되면 종료한다.

![](https://velog.velcdn.com/images/jimeaning/post/ab94b774-6022-41fa-a6c0-a904df7d2128/image.png)

<br>

#### 참고
[알고리즘 - 크루스칼 알고리즘(Kruskal Algorithm), 최소 신장 트리(MST)](https://chanhuiseok.github.io/posts/algo-33/)