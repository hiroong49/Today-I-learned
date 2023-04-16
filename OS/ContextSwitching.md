# Context Switching

현재 진행하고 있는 Context(프로세스, 스레드)의 상태를 저장하고 다음 진행할 Context를 실행하는 것이다. 즉 CPU에 실행할 프로세스를 교체하는 기술이다.  

<br>

#### Context
프로그래밍에서 Context는 동작, 작업들의 집합을 정의, 관리, 실행하도록 하는 최소한의 상태, 재료, 속성을 포함하는 객체, 구조체, 정보이다.  

#### 스케줄링
**자원**에 **작업**을 할당하는 행위이다.  
**자원**은 프로세서, 네트워크 연결, 외부 장치 등을 의미하고, **작업**은 스레드, 프로세스, 혹은 데이터 플로우를 의미한다.

<br>

### Context Switching이 필요한 이유
컴퓨터가 매번 하나의 task만 처리할 수 있다면, 해당 테스크가 다 끝날 때까지 다음 테스크는 기다릴 수밖에 없다.   
-> 반응 속도가 매우 느리고 사용하기 불편하다.

컴퓨터 멀티태스킹을 통해 빠른 반응 속도로 응답할 수 있다.  
빠른 속도로 테스크를 바꿔가며 실행하기 때문에 사람의 눈으로는 실시간처럼 보인다.  
CPU가 테스크를 바꿔가며 실행하기 위해 Context Switching이 필요하게 되었다.

<br>

### Context Switching의 진행 과정
- Task의 대부분 정보는 레지스터에 저장되고 PCB(Process Control Block)로 관리된다.
- 현재 실행하고 있는 테스크의 PCB 정보를 저장하게 된다. (Process Stack, Ready Queue)
- 다음 실행할 테스크의 PCB 정보를 읽어 레지스터에 적재하고 CPU가 이전에 진행했던 과정을 연속적으로 수행한다.

<br>

### PCB(Process Control Block) 구조
컨텍스트 스위칭은 PCB라고 하는 메모리의 별도 공간에 프로세스 상태값들을 저장하고, 해당 값들을 찾는 방법으로 구현된다. PCB는 프로세스가 실행중인 상태를 스냅샷 찍어 저장하는 공간이라고 생각하면 된다.

![](https://velog.velcdn.com/images/jimeaning/post/8f5f7c47-726a-40dc-861d-9f4279c0eeb3/image.png) 

- Process ID (PID)
- Process State: 프로세스 상태(Create, Ready, Running, waiting, terminated)
- Process Counter: 다음 실행할 명령어의 주소값
- CPU Registers: accumulator, index register, stack pointers, general purpose registers
- Memory Info(Limit): 메모리 사이즈 limit, 전체 프로세스 사이즈 등

<br>


### Process Context Switching vs Thread Context Switching
프로세스는 하나 이상의 스레드를 포함한다. 이 스레드는 고유한 Stack 영역의 메모리와 고유한 레지스터를 할당받는다. Heap 영역의 메모리에서 선언된 데이터는 서로 공유한다.  
동일한 프로세스 속에서 thread context switching이 발생할 경우 프로세서는 스택 영역의 주소와 레지스터 주소를 포함한 스레드의 context 정보만을 변경하면 된다.  
하지만 process context switching이 발생할 경우 프로세서는 스레드의 context 뿐만 아니라 프로세스의 context까지 모두 변경해야 한다.  

<br>

### Context Switching Cost
Context Switching이 발생하면 많은 비용이 든다.
- Cache 초기화
- Memory Mapping 초기화
- Kernel은 항상 실행되어야 한다.(메모리의 접근을 위해서)
- 프로세스가 스레드보다 비용이 많이 든다.
- 스레드는 스택 영역을 제외한 모든 메모리를 공유하기 때문에 Context Switching 발생시 스택 영역만 변경을 진행하면 된다.

<br>


[Context Switching로 알아보는 프로세스와 스레드](https://velog.io/@curiosity806/Context-Switching%EC%9C%BC%EB%A1%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EB%8A%94-process%EC%99%80-thread)  
[Context Switching이란](https://nesoy.github.io/articles/2018-11/Context-Switching)  
[컨텍스트 스위칭 - 티스토리](https://hyunie-y.tistory.com/31)