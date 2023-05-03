# 입력 함수

### input()

- input() 함수가 호출되면 인자로 주어진 문자를 화면에 출력하고 사용자의 입력을 기다린다.
- 사용자가 키를 누르면 그에 대응하는 데이터가 버퍼에 하나씩 들어간다.
- 개행 문자는 입력의 종료로 간주한다.
- 무엇을 입력하든 문자열로 변환하고 줄바꿈을 제거한 뒤 값을 반환한다.
- input() 내장 함수는 parameter로 prompt message를 받을 수 있다.  
  따라서 입력받기 전 prompt message를 출력해야 한다.
- 입력받은 값의 개행 문자를 삭제시켜서 리턴한다. 즉 입력받은 문자열에 rstrip() 함수를 적용시켜서 리턴한다.

<br>

### sys.stdin.readline()

- input()과 달리 문자를 화면에 출력하는 기능이 없다.
- 한번에 읽을 수 있는 글자 수 크기에 대한 매개변수를 제공한다.
- 한번에 읽어와 버퍼에 저장한다. 즉 하나씩 버퍼에 저장하는 input()보다 빠르며, 입력이 많아질수록 차이가 더욱 커진다.
- sys.stdin.readline()는 prompt message를 인수로 받지 않는다.
- 개행 문자를 포함한 값을 리턴한다. 따로 rstrip() 함수를 적용시켜야 한다.
  
<br>

*prompt message*  
사용자가 프롬프트에서 명령어를 입력하는 과정에서 작업 처리에 필요한 정보가 누락된 경우, 명령어에서 필요로 하는 정보를 추가로 입력받기 위하여 사용자에게 출력하는 메시지.

<br>

#### 참고
[input()과 sys.stdin.readline() 차이 -티스토리](https://hs-archive.tistory.com/35)  
[Input vs. sys.stdin.readline 차이점? -티스토리](https://buyandpray.tistory.com/7)  
[프롬프트 메시지의 의미](https://wordrow.kr/%EC%9D%98%EB%AF%B8/%ED%94%84%EB%A1%AC%ED%94%84%ED%8A%B8%20%EB%A9%94%EC%8B%9C%EC%A7%80/)
