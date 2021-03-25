# Java란?



- 객체지향 프로그래밍 언어이다.
- 서버, 모바일, 임베디드, 애플리케이션 등 다양한 분야에서 쓰인다.
- 처음 나온 것은 1995년이다.





# Java의 특징



> 쉬운 언어이다.

- C와 C++언어의 문법을 기본으로 차용하여 개발된 언어
- C와 C++이 가진 어려운 문법인 포인터와 다중 상속 제거
- C와 C++에 비해 쉬운 언어이다.



> 이식성이 높은 언어이다.

- Java는 JVM(Java Virtual Machine) 위에서 돌아가기 때문에 운영체제 종류에 상관없이 돌아간다.

- Java 언어로 개발된 프로그램은 소스 파일을 다시 수정하지 않아도 자바 실행 환경(JRE : Java Runtime Environment)이 설치되어 있는 모든 운영체제에서 실행 가능하다. 따라서 Java 언어는 이식성이 높은 프로그래밍 언어라 할 수 있다.

  ![JAVA_1](C:\Users\tnfl4\OneDrive\Desktop\취업 스터디\CS정리\res\JAVA\JAVA_1.png)

  예를 들어, C언어의 경우 운영체제의 종류에 따라 int형의 크기가 달라지기도 하지만 Java의 경우는 이런 경우가 없다.(모두 동일한 JVM 환경에서 돌아가기 때문)

  즉, MS Windows, 리눅스, Mac OS 등 여러 운영체제에서 동일하게 실행가능하다.(=플랫폼에 독립적이다.)



> 객체지향언어(OOP) 이다.

- 객체 지향 프로그래밍(OOP) : 프로그램을 개발하는 기법으로 부품에 해당하는 객체들을 먼저 만들고 이것들을 하나씩 조립 및 연결해서 전체 프로그램을 완성하는 기법

- Java는 처음부터 객체 지향 개발용 언어로 설계된 언어이다.

  따라서 유지보수가 쉽고 직관적인 코드 분석이 가능하다.
  
- 객체를 만들기 위해 설계도인 클래스를 작성해야 하고 객체와 객체를 연결해 목적에 맞는 프로그램을 만들어낸다. Java는 아무리 작은 프로그램이라도 객체를 만들어 사용하게 된다.



> 메모리 자동 관리

- C언어의 경우 malloc 함수를 통해 메모리를 직접 관리하지만, Java는 Garbage Collector에 의해 사용하지 않는 객체는 자동으로 메모리에서 제거를 한다.



> 다양한 애플리케이션 개발 가능

- 콘솔 프로그램, UI 애플리케이션, 서버 애플리케이션, 모바일 애플리케이션 등 다양한 프로그램을 개발할 수 있다.



> 멀티 스레드(Multi-Thread)를 쉽게 구현 가능

`1. 동시에 여러가지 작업을 하는 경우`

`2. 대용량 작업을 빨리 처리할 경우`

위 두 가지를 하기 위해 병렬 처리(=멀티 스레드)가 필요하다.

![JAVA_2](C:\Users\tnfl4\OneDrive\Desktop\취업 스터디\CS정리\res\JAVA\JAVA_2.png)

운영체제마다 멀티 스레드를 이용하는 API가 다르지만, Java의 경우 Java API를 이용하기 때문에 일관된 생성 및 관리가 가능하다.



> 동적 로딩

- 미리 객체를 만들지 않고, 필요한 시점에 동적으로 로딩해서 객체를 생성할 수 있다.
- 유지보수 시, 특정 객체만 쉽게 수정 및 교체해서 사용할 수 있다.



> 풍부한 오픈소스 라이브러리

- 자바는 오픈소스 언어이고, 자바를 이용해서 만들어진 라이브러리가 굉장히 많다.
- 라이브러리를 이용하여 시간과 비용을 줄이고 좋은 애플리케이션을 만들기 편하다.



> 속도가 느리다.

- 자바는 한 번의 컴파일링으로 실행 가능한 기계어가 만들어지지 않고 JVM에 의해 기계어로 번역되고 실핸하는 과정을 거치기 때문에 C나 C++의 컴파일 단계에서 만들어지는 완전한 기계어보다는 속도가 느리다.
- 그러나 바이트 코드를 기계어로 변환해주는 JIT 컴파일러 같은 기술 적용으로 JVM의 기능이 향상되어 속도의 격차가 많이 줄어들었다.



> 예외 처리가 불편하다.

- 자바는 다른 언어들과 달리 프로그램 실행 시 발생할 수 있는 예외(Exception)들을 개발자가 직접 선언하여 처리해야 한다. 그렇지 않으면 아예 컴파일이 되지 않는다.
