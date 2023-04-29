# 제네릭

자바에서 제네릭(Generics)은 데이터의 타입을 일반화한다는 것이다. 즉, **클래스 내부에서 사용할 데이터 타입을 외부에서 지정하는 기법**이다. 객체별로 다른 타입의 자료가 저장될 수 있도록 한다.

이렇게 컴파일 시에 미리 타입 검사를 수행하면 다음과 같은 장점이 있다.
- 클래스나 메소드 내부에서 사용되는 객체의 안정성을 높일 수 있다.
- 반환값에 대한 타입 변환 및 타입 검사에 들어가는 노력을 줄일 수 있다.

자바에서 배열과 함께 자주 쓰이는 자료형이 리스트(List)이다.
```
ArrayList<String> list = new ArrayList<>();
```
여기서 꺾쇠 괄호가 제네릭이다. 괄호 안에는 타입명을 적는다. 이 리스트 클래스의 자료형은 String으로 지정되어 문자열 데이터만 리스트에 적재할 수 있게 된다.

![](https://velog.velcdn.com/images/jimeaning/post/f0bff6f8-f17a-48fc-a30f-be47929c7820/image.png)

이렇게 제네릭은 **타입을 변수화** 한 기능이라고 생각하면 된다.

즉, 변수를 선언할 때 타입을 지정해주듯이 **제네릭은 객체(Object)에 타입을 지정해주는 것**이라고 보면 된다.

<br>

### 제네릭의 장점
1. 제네릭을 사용하면 잘못된 타입이 들어올 수 있는 것을 컴파일 단계에서 방지할 수 있다.
2. 클래스 외부에서 타입을 지정해주기 때문에 따로 타입을 체크하고 변환할 필요가 없다. 즉, 관리하기가 편안하다.
3. 비슷한 기능을 지원하는 경우 코드의 재사용성이 높아진다.

<br>

### 제네릭 사용방법
| 타입 | 설명|
|---|---|
\<T> | Type
\<E> | Element
\<K> | Key
\<V> | Value
\<N> | Number

<br>

제네릭 클래스를 사용하는 방법은 아래와 같다.

```
public class ClassName <T, K> { ... }
 
public class Main {
	public static void main(String[] args) {
		ClassName<String, Integer> a = new ClassName<String, Integer>();
	}
}
```

이렇게 객체를 생성할 때 구체적인 타입을 명시해야 한다. 예시는 T가 String, K는 Integer가 된다.

이때 주의할 점은 타입 파라미터로 명시할 수 있는 것은 참조 타입(Reference Type)이다. 즉, int, double, char과 같은 primitive type은 올 수 없다. 그래서 int형 double형 등 primitive Type의 경우 Integer, Double 같은 Wrapper Type으로 쓰는 이유가 바로 위와같은 이유다.

<br>

### 제네릭의 제거 시기
자바 코드에서 선언되고 사용된 제네릭 타입은 컴파일 시 컴파일러에 의해 자동으로 검사되어 타입 변환된다. 그리곤 코드 내의 모든 제네릭 타입은 제거되고 컴파일된 class 파일에는 어떠한 제네릭 타입도 포함되지 않게 된다.

이런 식으로 동작하는 이유는 제네릭을 사용하지 않는 코드와의 호환성을 유지하기 위해서이다.

<br>

#### 참고
[자바 제네릭 개념&문법 정복하기 -티스토리](https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EC%A0%9C%EB%84%A4%EB%A6%ADGenerics-%EA%B0%9C%EB%85%90-%EB%AC%B8%EB%B2%95-%EC%A0%95%EB%B3%B5%ED%95%98%EA%B8%B0)  
[제네릭이란? -TCP School](http://www.tcpschool.com/java/java_generic_concept)  
[제네릭의 이해 -티스토리](https://st-lab.tistory.com/153)