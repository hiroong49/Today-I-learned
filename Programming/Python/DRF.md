# DRF (Django REST Framework)

Django 안에서 Restful API 서버를 쉽게 구축할 수 있도록 도와주는 오픈소스 라이브러리

*REST*  
HTTP의 URL과 HTTP method(GET, POST, PUT, DELETE)를 사용하여 가독성을 높인 구조화된 시스템 아키텍처(프레임워크)  

자세한 정리는 [이 곳](https://github.com/jimeaning/Today-I-learned/blob/main/Network/RestfulAPI.md) 참고..

어플리케이션 등장 이후 웹으로만 서비스를 제공할 수 없어졌다. 즉, HTML로 렌더링하는 웹 서버가 아니라 **JSON이나 XML과 같은 형식을 통해 데이터를 다루는 별도의 API 서버가 필요**해졌다.

따라서 RESTful한 아키텍처를 HTTP method와 함께 사용하여 웹, 앱, 데스크탑, 스마트폰 어플들까지 범용 가능한 하나의 API를 선호하게 되었다.  
자체 View 클래스 자체가 RESTful한 서버를 만들기에 최적의 프레임워크인 장고 역시 그 기능을 제공하게 된 것이 DRF이다.

<br>

### DRF의 장점 / DRF를 사용하면 좋은 경우

- 범용성이 좋은 웹 브라우저 API를 사용한 쉬운 개발 (RESTful한 서버를 보다 쉽고 빠르게 만들자)
- OAuth1, OAuth2를 위한 추가적인 패키지가 인증 정책에 추가되어 있는 경우
- DB 데이터를 json으로 직렬화하는 기능
- 국제적인 기업들을 포함해서 다수의 기업이 사용 (커뮤니티가 잘 되어 있음)

<br>

### Serializer

DRF에서 메인이 되는 기능으로, DB 데이터를 JSON 데이터로 변환해준다. (ORM, non-ORM 모두)  
API 통신에서 주고 받는 데이터 타입은 JSON이다. 한편, 파이썬 모델 객체 데이터 타입은 QuerySet으로 구조가 복잡하다.  
QuerySet을 JSON으로 바꾸는 것이 어렵다. 이때 QuerySet을 JSON으로 바꾸는 기능을 제공하는 것이 직렬화이다.  
DRF를 가장 매력적, 강력하게 만들어주는 요소이다.

<br>

#### 참고
[What is Django REST Framework?](https://velog.io/@ifyouseeksoomi/DRF-Django-REST-Framework-%EA%B0%84%EB%8B%A8%ED%95%9C-%EC%98%88%EC%8A%B5-Serializer)