# Java

### Java의 장단점
- 장점
  - JVM 위에서 동작하기 때문에 운영체제로부터 독립적이다.
  - 가비지컬렉터가 메모리를 관리해주기 때문에 편리하다.
- 단점
  - JVM 위에서 동작하기 때문에 실행속도가 상대적으로 느리다.
  - 다중 상속이나 타입에 엄격하는 등 제약이 많다.  
<br/>

### Java가 다중 상속을 지원하지 않는 이유
다중 상속을 지원하면 다이아몬드 문제가 발생할 수 있다. 예를 들어, Human 클래스 안에 있는 walk() 메소드를 Female 클래스와 Male 클래스가 모두 구현하였다고 할 때, Female과 Male 클래스를 다중 상속 받은 Person 클래스 입장에서 코드 충돌이 생기기 때문이다.  

![](https://velog.velcdn.com/images/jimeaning/post/2a2351f0-26f4-4503-9c8d-12acb93ea86b/image.png)  

<br/>

### Java의 List, Set, Map 차이
Collection, 순서나 집합적인 저장 공간
- List
  - 데이터를 순차적으로 저장한다.
  - 데이터의 중복을 허용한다.
  - 데이터로 null을 허용한다.
- Set
  - 순서없이 Key로만 데이터를 저장한다.
  - Key의 중복을 허용하지 않는다.
  - Key로 null을 허용하지 않는다.  

키와 값으로 핸들
- Map
  - 순서없이 Key, Value로 데이터를 저장한다.
  - Value는 중복을 허용하지만 Key의 중복은 허용하지 않는다.
  - Key로 null을 허용하지 않는다.
  
![](https://velog.velcdn.com/images/jimeaning/post/0350c142-3d6d-4a5c-b074-4cdb81f6f8d8/image.png)

<br/>

### Java의 Vector, ArrayList 차이
크기가 동적인 배열을 사용할 때 주로 사용
- Vector
  - 동기화를 지원한다. (한번에 하나의 스레드만 접근 가능->스레드 안전)
  - 속도가 느리지만 병렬 상황에서 안전하다.
  - 크기가 증가하는 경우 2배 증가함
- ArrayList
  - 동기화를 지원하지 않는다. (동시에 여러 스레드가 작업할 수 있음)
  - 속도는 빠르지만 병렬 상황에서 안전하지 않다.
  - 크기가 증가하는 경우 1.5배 증가함  

<br/>

### Java의 StringBuffer, StringBuilder 차이
문자열을 연산(추가하거나 변경)할 때 주로 사용하는 자료형
- StringBuffer
  - 동기화를 지원한다.
  - 속도가 느리지만 병렬 상황에서 안전하다.
- StringBuilder
  - 동기화를 지원하지 않는다.
  - 속도는 빠르지만 병렬 상황에서 안전하지 않다.  
  
<br/>

### Java의 synchronized
Java에서 지원하는 synchronized는 여러 스레드가 하나의 자원을 이용하고자 할 때, 한 스레드가 해당 자원을 사용중인 경우, 데이터에 접근할 수 없도록 막는 것이다. synchronized를 이용하면 병렬 상황에서 자원의 접근을 안전하게 하지만, 자원을 이용하지 않는 스레드는 락에 의한 병목현상이 발생한다.
- 메소드 synchronized: 한 시점에 하나의 스레드만 해당 메소드를 실행할 수 있다.
- 변수 synchronized: 한 시점에 하나의 스레드만 해당 변수를 참조할 수 있다.  

<br/>

### Java8
Java8에서는 함수형 프로그래밍을 위해 함수형 인터페이스, 람다, stream API가 추가되었고, Null-safe한 작업을 위해 Optional API, Date, Time을 함께 처리하기 위한 LocalDateTime API가 추가되었다.