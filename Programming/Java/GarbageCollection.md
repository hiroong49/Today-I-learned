# Garbage Collection

가비지 컬렉션은 자바의 메모리 관리 방법 중 하나이다. JVM의 Heap 영역에서 동적으로 할당했던 메모리 영역 중 필요없게 된 메모리 영역을 주기적으로 삭제하는 프로세스이다.  
C나 C++에는 가비지 컬렉션이 없어 프로그래머가 수동으로 메모리 할당과 해제를 해줘야 한다. 반면, Java는 JVM에 탑재되어 있는 가비지 컬렉터가 메모리 관리를 대행해주기 때문에 개발자는 메모리 관리나 누수(Memory Leak) 문제를 완벽하게 관리하지 않아도 돼 개발에만 집중할 수 있다.  
<br/>

### 가비지 컬렉션의 단점
1. 개발자는 메모리가 언제 해제되는지 정확하게 알 수 없다.
2. 가비지 컬렉션(GC)이 동작하는 동안 다른 동작을 멈추기 때문에 오버헤드가 발생한다.  
-> GC가 너무 자주 실행되면 소프트웨어 성능 하락의 문제가 되기도 한다. 따라서 미사일과 같은 실시간으로 계속 동작해야 하는 시스템은 잠깐의 소프트웨어 일시정지로도 목표한 결과가 달라질 수 있기 때문에 GC 사용이 적합하지 않다.  
<br/>

### 가비지 컬렉션의 대상이 되는 객체
객체는 Heap영역에서 생성된다. Method Area나 Stack Area와 같은 Root Area에서 Heap Area에 생성된 객체의 주소만 참조하는 형식으로 구성된다.  
만약 Heap Area에서 생성된 객체가 메서드가 끝나는 등의 특정 이벤트로 인하여 Heap Area 객체의 메모리 주소를 가지고 있는 참조 변수가 삭제되면, 참조하지 않는 객체가 발생하게 된다. 이러한 객체를 **Unreachable**하다고 표현하며, 주기적으로 가비지 컬렉터가 제거하는 대상이 된다.  
>Reachable: 객체가 참조되는 상태  
Unreachable: 객체가 참조되고 있지 않은 상태(GC 대상)  

<br/>

### 가비지 컬렉션 동작 과정
먼저 JVM은 메모리 사용을 중단하기 위해 애플리케이션 실행을 멈추는 stop-the-world를 실행한다. stop-the-world를 실행하면 GC를 실행하는 쓰레드를 제외한 모든 쓰레드가 작업을 멈춘다. 그리고 GC가 끝나면 다시 작업을 재개한다.  
GC 작업은 Young 영역에 대한 Minor GC와 Old 영역에 대한 Major GC로 구분된다.
- Young 영역: 새롭게 생성한 객체들이 위치한다. 대부분의 객체는 금방 접근 불가능한 상태가 되기 때문에 많은 객체가 Young 영역에서 생성되었다가 사라진다.
- Old 영역: Young 영역에서 계속 사용되어 살아남은 객체가 복사되는 영역이다. Young 영역보다 크게 할당되며 더 적은 GC가 발생한다.  

<br/>
Young 영역은 1개의 Eden 영역과 2개의 Survivor 영역으로 구성된다.  

Young 영역에 대한 GC
1. 새로운 객체가 Eden 영역에 생성됨.
2. Eden 영역에 GC가 동작하고, 그 중 살아남은 객체가 Survivor0으로 이동함.
3. 2번의 동작이 반복되어 Survivor0이 꽉 차게 됨.
4. Survivor0 영역에 GC가 동작하고, 살아남은 객체들은 Survivor1으로 이동하고 Survivor0을 비우게 됨. (2개의 Survivor 영역 중 1개는 반드시 비어 있어야 한다)
5. 위의 동작들이 반복되어 특정 횟수만큼 살아남은 객체는 Old 영역으로 이동함. 
    
Old 영역에 대한 GC  
Old 영역이 가득 차 Survivor 영역에서 Old 영역으로 Promotion이 불가능할 때 Old 영역에 대한 GC(Major GC)가 실행됨.  
<br/>

### 가비지 컬렉션 알고리즘 종류
- Serial GC: mark-sweep-compact 알고리즘을 사용한다. Old 영역에서 살아있는 객체를 식별하고(Mark), 살아있는 객체만을 남긴다.(Sweep) 그리고 난 후 객체들을 앞부분부터 채워 객체가 존재하는 부분과 존재하지 않는 부분으로 나눈다.(Compaction)
- Parallel GC: 기본적인 알고리즘은 Serial GC와 같지만 여러 쓰레들르 이용하여 GC를 처리한다.
- Paralle Old GC(Parallel Compacting GC): Serial GC의 Sweep 알고리즘 대신 Summary를 사용한다. Summary 단계는 앞서 GC를 수행한 영역에 대해서 별도로 살아있는 객체를 식별하며, Sweep보다 조금 더 복잡하다.
- Concurrent Mark & Sweep GC(CMS): Initial Mark 단계에서는 살아 있는 객체를 찾는 것으로 끝낸다.(Stop-the-World 시간이 짧음) 그리고 찾은 객체에서 참조하는 객체를 Concurrent하게(여러 쓰레드가 동시에) 따라가는 Concurrent Mark 단계가 수행된다. 그 이후에 Stop-the-world가 실행되고 Concurrent하게 Remark가 동작한다. 애플리케이션의 응답속도가 매우 중요할 때 사용한다.
- G1(Garbage First) GC: 바둑판의 각 영역에 객체를 할당하고 GC를 실행한다. 위에서 설명한 Young 영역과 Old 영역에 대한 개념을 사용하지 않고 객체를 할당한다.  

![](https://velog.velcdn.com/images/jimeaning/post/24d99d0f-1171-463f-a531-7c7897597f60/image.png)  ![](https://velog.velcdn.com/images/jimeaning/post/e01b242b-14b3-4eee-b49e-7f3787f39cec/image.png)  
<br/>

### 가비지 컬렉터 작동 문제를 진단하는 방법과 해결 방법
가비지 컬렉션을 수행하려면 Survivor 영역 중 하나는 반드시 비어 있는 상태로 남아 있어야 한다. 만약 두 Survivor 영역에 모두 데이터가 존재하거나, 두 영역 모두 사용량이 0이면 시스템이 정상적인 상황이 아닌 것이다.  
<br/>

### 가비지 컬렉션에 의한 시스템 중단 시간을 줄이는 방법
- 옵션을 변경하여 GC 성능 높이기
  - young 영역과 old 영역의 힙 크기를 높여 GC의 빈도를 줄인다
  - 객체의 할당과 promotion을 줄인다
- 설정을 변경하여 GC 성능 높이기
  - 애플리케이션을 중단시킨 후 GC를 병렬로 동시에 진행시킨다
  - 애플리케이션과 GC 작업을 동시에 진행시킨다(concurrent)
- 개발자 코드를 변경하여 GC 성능 높이기
  - Collection 등을 활용할 때 사용할 객체의 크기를 명시한다
  - 스트림을 바로 사용한다
    - 변경 전: byte[] fileData = readFileToByteArray(new File("myfile.txt"));
    - 변경 후: FileInputStream fis = new FileInputStream(fileName);
  - 불변(Immutable) 객체 사용하기
  ```
    public class MutableHolder {  
        private Object value;  
        public Object getValue() { return value; }  
        public void setValue(Object o) {  value = o; }  
    }  

    public class ImmutableHolder {  
        private final Object value;  
        public ImmutableHolder(Object o) { value = o; }  
        public Object getValue() { return value; }  
    }
    ```
    MutableHolder는 계속 다른 값을 참조하여 생존해 Old 영역으로 이동한다. 하지만 Old 영역으로 가서도 참조하는 객체가 바뀌기 때문에 Minor GC를 수행할 때 Old 영역으로 와서 MutableHolder까지 검사하여 Young 영역을 정리해야 한다. 즉 검사해야 하는 범위가 늘어나는 것이다.  
    하지만 불변의 객체 ImmutableHolder를 사용하면 스캔 범위가 줄어든다. ImmutableHolder가 참조하는 값이 먼저 존재해야 ImmutableHolder가 존재할 수 있다. 따라서 ImmutableHolder가 Old 영역으로 이동하게 되면 MutableHolder Minor GC에 대한 검사를 하지 않아도 된다. 스캔 범위가 줄어 성능을 높일 수 있다.  

<br/>

#### 참조 링크
[기술질문-Java](https://mangkyu.tistory.com/94)  
[가비지컬렉션 총정리](https://coding-factory.tistory.com/829)