# 내부 단편화, 외부 단편화

### 내부 단편화 (Internal Fragmentation)
내부 단편화는 메모리를 할당할 때 **프로세스가 필요한 양보다 더 큰 메모리가 할당되어서 공간이 낭비**되는 상황이다.   
<br>

![](https://velog.velcdn.com/images/jimeaning/post/55934257-d63d-437b-a956-6ca2497fcbd2/image.png)
![](https://velog.velcdn.com/images/jimeaning/post/ceae2118-fc0e-44f1-904e-8dbd412fa3bd/image.png)

그림과 같이 100MB의 메모리에 80MB 크기의 프로세스를 올리게 되면 20MB 만큼의 내부 단편화가 발생하게 된다. 즉, 적은 크기의 잔여 메모리가 발생해 해당 메모리를 사용할 수 없게 된다.  
<br>

### 외부 단편화 (External Fragmentation)
메모리가 할당되고 해제되는 작업이 반복적으로 일어날 때, 할당된 메모리와 메모리 사이에 중간중간 사용하지 않는 작은 메모리가 생긴다. 외부 단편화는 **남아 있는 총 메모리 공간이 요청한 메모리 공간보다 크지만 남아 있는 공간이 연속적이지 않아 발생하는 현상**이다  

![](https://velog.velcdn.com/images/jimeaning/post/845bdbc9-df26-400e-ace9-a94b66a46e10/image.png)

남아 있는 메모리 공간은 총 100MB(50MB+50MB)로 요청한 메모리 공간인 80MB 보다 크지만, 남아 있는 공간이 연속적이지 않아 Process C를 할당할 수 없게 된다. 따라서 남아 있는 메모리 공간이 낭비되는 문제가 발생한다.  
<br>

### 외부 단편화 해결방법 - 압축 (Compaction)
외부 단편화 문제를 해결하기 위해 압축 기법을 사용할 수 있다. 압축 기법은 주기억장치 내 분산되어 있는 **단편화된 공간들을 통합하여 하나의 커다란 빈 공간을 만드는 작업**이다.  

위 예시를 압축하면 다음과 같다.

![](https://velog.velcdn.com/images/jimeaning/post/5458984d-8d39-438b-93a9-15a2ddaba7d5/image.png)

흩어져 있던 공간을 연속된 공간, 즉 하나의 공간으로 만들면 기존에 할당할 수 없었던 프로세스를 할당할 수 있게 된다.  

![](https://velog.velcdn.com/images/jimeaning/post/9d6a7d4e-04af-48d4-9380-2d14aed9eafc/image.png)

<br>

#### 참고
[내부 단편화, 외부 단편화란? | 외부단편화 해결 방법-티스토리](https://code-lab1.tistory.com/54)  
