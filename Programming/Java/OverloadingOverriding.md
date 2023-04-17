# 오버로딩 오버라이딩
자바에서 다형성을 지원하는 방법으로 메서드 오버로딩과 오버라이딩이 있다.

<br>

### 오버로딩 (Overloading)
C언어에서 하나의 함수는 하나의 기능만을 구현해야 한다. 한편 자바에서는 하나의 메소드 이름으로 여러 기능을 구현할 수 있다.  
오버로딩은 자바의 한 클래스 내에 이미 사용하려는 이름과 같은 이름을 가진 메소드가 있더라도 매개변수의 개수 또는 타입이 다르면 같은 이름을 사용해서 메소드를 정의할 수 있다.  
- 반환 타입 관계 없음
- 메소드명 같음
- 매개변수 다름 (자료형 or 순서)

<br>

### 오버로딩 조건
**메소드의 이름이 같고 매개변수의 개수나 타입이 달라야 한다.** 주의할 점은 **리턴 값만** 다른 것은 오버로딩을 할 수 없다.  

코드 예시  
```
class OverloadingTest {

	public static void main(String[] args) {
		OverloadingMethods om = new OverloadingMethods();

		om.print();
		System.out.println(om.print(3));
		om.print("Hello!");
		System.out.println(om.print(4, 5));
	}
}

class OverloadingMethods {
	public void print() {
		System.out.println("오버로딩1");
	}

	String print(Integer a) {
		System.out.println("오버로딩2");
		return a.toString();
	}

	void print(String a) {
		System.out.println("오버로딩3");
		System.out.println(a);
	}

	String print(Integer a, Integer b) {
		System.out.println("오버로딩4");
		return a.toString() + b.toString();
	}

}
```

**결과**
```
오버로딩1
오버로딩2
3
오버로딩3
Hello!
오버로딩4
45
```
<br>
코드는 아무 문제 없이 잘 실행된다. 즉 print라는 같은 이름을 가진 네개의 메소드가 매개변수의 개수와 타입를 다르게 지정하여 지정하는 것이 가능하다는 것을 보여주고 있다.

단, '리턴 값'만 다르게 지정하는 것은 오버로딩을 할 수 없다.

접근 제어자도 자유롭게 지정해 줄 수 있다. 각 메소드의 접근 제어자를 public, default, protected, private으로 다르게 지정해줘도 상관없다는 것이다.  
=> 접근 제어자만 다르게 한다고 오버로딩이 가능하지 않다!

결국 오버로딩은 **매개변수의 차이**로만 구현할 수 있다는 것이다. 매개변수가 다르다면 리턴 값은 다르게 지정할 수 있다.

<br>

### 오버로딩을 사용하는 이유
1. 같은 기능을 하는 메소드를 하나의 이름으로 사용할 수 있다.  
println 메소드 역시 오버로딩이다. println의 인자값으로 int, double, boolean, String 등 다양한 타입의 매개변수를 집어 넣었을 때, 우리는 그 함수들이 어떻게 실행되는지 모르지만 콘솔창에 잘 출력된다. 이처럼 '출력하다'라는 같은 기능을 가진 메소드들을 println이라는 하나의 이름으로 정의가 가능하다.

2. 메소드 이름을 절약할 수 있다.  
println 메소드를 매개변수의 종류에 따라서 다르게 지정해야 한다고 하면, printInt, printDouble, printBoolean 등 수많은 메소드들의 이름을 정해줘야 한다. 이는 프로그래머에게 메소드 네이밍 고민을 가중시키는 것이다. 또한 다른 곳에 이름이 사용돼 헷갈릴 가능성도 있다.

<br>

### 오버라이딩 (Overriding)

오버라이딩은 부모 클래스로부터 상속받은 메소드를 자식 클래스에서 재정의하는 것이다. 상속받은 메소드를 그대로 사용할 수도 있지만, 자식 클래스에서 상황에 맞게 변경해야 하는 경우 오버라이딩을 할 필요가 생긴다.  
- 반환타입, 메소드명, 매개변수 모두 같음
- 부모 클래스로부터 상속받은 메소드를 재정의하는 것

<br>

### 오버라이딩의 조건
오버라이딩은 부모 클래스의 메소드를 재정의하는 것이므로, 자식 클래스에서는 오버라이딩하고자 하는 메소드의 이름, 매개변수, 리턴 값이 모두 같아야 한다.

코드
```
public class OverridingTest {

	public static void main(String[] args) {
		Person person = new Person();
		Child child = new Child();
		Senior senior = new Senior();
		
		person.cry();
		child.cry();
		senior.cry();
	}
}

class Person {
	void cry() {
		System.out.println("흑흑");
	}
}

class Child extends Person {
	@Override
	protected void cry() {
		System.out.println("잉잉");
	}
}

class Senior extends Person {
	@Override
	public void cry() {
		System.out.println("훌쩍훌쩍");
	}
}
```

결과
```
흑흑
잉잉
훌쩍훌쩍
```

<br>

**@Override의 쓰임**  

어노테이션(Annotation)은 직역하면 주석이다. 이는 일반적인 주석과 다르게, 검증하는 기능을 한다. 여기서 사용된 @Override라는 **어노테이션은 오버라이딩을 검증하는 기능**을 한다. 코드상으로 검사했을 때 오버라이딩이 실제로 시행되지 않았다면 컴파일시 오류를 출력한다.

<br>

위 코드는 정상적으로 실행되는 것을 볼 수 있다. 부모 클래스의 메소드를 오버라이딩하는 것은 내용만을 새로 정의하는 것이므로 ***선언부는 부모의 것과 완벽히 동일***해야 하는 것을 볼 수 있다.

프로그래머가 Person클래스의 cry메소드를 '흑흑'이라고 정의했다. 그런데 Child클래스와 Senior클래스를 만들면서 울음소리를 다르게 출력하고 싶은 것이다. 그래서 Child클래스와 Senior클래스에서 부모의 메소드의 이름만 빌려와서 자기의 방식대로 '재정의'하였다. 이것이 **오버라이딩**이다.

<br>


### 오버라이딩에서의 접근 제어자 규칙

1. 자식 클래스에서 오버라이딩하는 메소드의 접근 제어자는 부모 클래스보다 더 좁게 설정할 수 없다.  
위에서 볼 수 있듯이 부모 클래스의 접근제어자는 default로 설정되어 있다. 여기서 자식 클래스들은 default보다 같거나 더 넓은 범위의 접근제어자만 설정할 수 있으므로 default, protected, public 이 세 개의 접근 제어자 사용이 가능하다.

2. 예외(Exception)는 부모 클래스의 메소드 보다 많이 선언할 수 없다.  
   부모 클래스에서 어떤 예외를 throws 한다고 하면, 자식 클래스에서는 그 예외보다 더 큰 범위의 예외를 throws 할 수 없다는 것이다.



3. static 메소드를 인스턴스의 메소드 또는 그 반대로 바꿀 수 없다.  
   부모 클래스의 static 메소드를 자식에서 같은 이름으로 정의할 수 있지만 이것은 다시 정의하는 것이 아니라 같은 이름의 static 메소드를 새로 정의하는 것이다.

<br>

### 오버로딩과 오버라이딩 한 줄 정리
오버로딩(Overloading) : 같은 이름의 메서드 여러개를 가지면서 매개변수의 유형과 개수가 다르도록 하는 기술

오버라이딩(Overriding) : 상위 클래스가 가지고 있는 메서드를 하위 클래스가 재정의하는 것


구분 | 오버로딩 | 오버라이딩
--- | ---| ---|
메서드 이름 | 동일 | 동일
매개변수, 타입 | 다름 | 동일
리턴 타입 | 상관 없음 | 동일
적용 범위 | 같은 클래스 내 | 상속 관계
접근 제어자 | 모든 접근 제어자 사용 가능 | 부모 클래스의 메소드 접근 제어자보다 더 넓은 범위의 접근 제어자
<br>

#### 참고
[오버로딩&오버라이딩-티스토리](https://hyoje420.tistory.com/14)  
[오버로딩과 오버라이딩 차이는?](https://gyoogle.dev/blog/interview/%EC%96%B8%EC%96%B4.html#%E1%84%8B%E1%85%A9%E1%84%87%E1%85%A5%E1%84%85%E1%85%A9%E1%84%83%E1%85%B5%E1%86%BC%E1%84%80%E1%85%AA-%E1%84%8B%E1%85%A9%E1%84%87%E1%85%A5%E1%84%85%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%83%E1%85%B5%E1%86%BC-%E1%84%8E%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%82%E1%85%B3%E1%86%AB)  
[오버로딩과 오버라이딩 차이와 예제-티스토리](https://private.tistory.com/25)
 
