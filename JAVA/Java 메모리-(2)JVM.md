# JVM(Java Virtual Machine)



`JVM을 이해하기 위해서는 JVM, JRE, JDK, Java를 구분해서 알아야 할 필요가 있습니다.`



![Java 메모리_5](C:\Users\tnfl4\OneDrive\Desktop\취업 스터디\CS정리\res\JAVA\Java 메모리_5.PNG)



> JVM (Java Virtual Machine)

- Java Byte Code를 OS에 맞게 해석해주는 역할을 합니다. Java Compiler는 `.java` 파일을 `.class` 라는 Java Byte Code로 변환시켜 줍니다.
- Byte Code는 기계어가 아니기 때문에 OS에서 바로 실행되지 않습니다. 이때, JVM은 OS가 Byte Code를 이해할 수 있도록 해석해줍니다.
- 이러한 JVM의 해석을 거치기 때문에 C언어 같은 네이티브 언어에 비해 속도가 느렸지만, JIT(Just In Time) 컴파일러를 구현해 이점을 극복했습니다.
- 따라서, Byte Code는 JVM 위에서 OS에 상관없이 실행된다는 점이 Java의 가장 큰 장점이 됩니다. OS에 종속적이지 않고 Java 파일 하나만 만들면 어느 디바이스든 JVM 위에서 실행할 수 있습니다.



> JRE (Java Runtime Environment)

- JVM + 핵심 라이브러리
- 개발과는 관련이 없으나, 실행과는 관련이 있음
- Java는 보통 JRE 단위로 배포됨



> JDK (Java Development Kit)

- JRE + 개발 툴
- 자바11 부터는 JDK 단위로 배포됨



> Java

- 소스 코드 자체는 플랫폼에 독립적
- javac에 의해 `.class`로 만들어짐
- JVM 자체 연관이 타이트하지 않음. (JVM은`.class`만 다루기 때문)
  - ex) Kotlin과 kotlinc로 `.class` 파일을 만들 수 있음

```
* .java 가 프로세스가 되기까지의 과정
.java -> (javac) -> .class -> (JVM) -> Process

* Byte 코드와 Binary 코드의 차이
- Byte 코드는 JVM 같은 가상 머신이 이해할 수 있는 코드(=.class)
- Binary 코드는 CPU가 이해할 수 있는 코드
```





### JVM 구조



![Java 메모리_6](C:\Users\tnfl4\OneDrive\Desktop\취업 스터디\CS정리\res\JAVA\Java 메모리_6.PNG)



> 클래스 로더(Class Loader) 시스템

- Byte Code를 읽어오며 메모리에 적절히 배치하는 역할
- RunTime 시점에 클래스를 로딩하게 해주며 클래스의 인스턴스를 생성하면 클래스 로더를 통해 메모리에 로드하게 됩니다.
  - 로딩(Loading) : `.class`를 읽어옴
  - 링크(Linking) : 코드 내부의 레퍼런스를 연결함
  - 초기화(Initialization) : 클래스에 있는 static 값들을 초기화함



> 메모리 영역(Runtime Data Areas)

- JVM이 프로그램을 수행하기 위해 OS로부터 별도로 할당받은 메모리 공간을 말하며, 크게 5가지 영역으로 나눌 수 있습니다.

- Heap, Method Area는 전체 공유 자원으로 분류되고, JVM Stack, Native Method Stack, PC Register는 스레드 단위의 자원으로 분류됩니다.

- Heap

  - 객체(인스턴스) 수준의 정보를 저장

- Method Area

  - 클래스 수준의 정보를 저장
    - 클래스 이름, 부모 클래스 이름, 메서드, 변수 등
    - static 변수, 일반 변수 등

- JVM Stack

  - 인스턴스 및 지역 변수의 참조 주소들을 저장
  - 스레드마다 런타임 스택을 만들고, 스택 프레임(메서드 call)을 쌓음
    - 에러가 났을 때, 에러 메시지를 보면 런타임 스택에 메시지가 쌓여있는 것을 확인할 수 있습니다.

- Native Method Stack

  - Native 메서드를 호출할 때 사용하는 별도의 스택

  - Native 메서드는 Java가 아닌 C와 같은 언어(low-level)로 구현된 메서드임

    - 대표적인 예시로, `Thread.currentThread() `가 있습니다.

      `public static native Thread currentThread()` 로 선언되어 있습니다.

- PC Register

  - 스레드마다 가지고 있는 Program Counter
  - 현재 실행할 부분을 가리키고 있습니다.



> 실행 엔진 (Execution Engine)

- Load된 Class의 Byte Code를 실행하는 Runtime Module 입니다.
- Class Loader를 통해 JVM 내의 Runtime Data Areas에 배치된 Byte Code는 Execution Engine에 의해 실행되며, 실행 엔진은 자바 Byte Code를 명령어 단위로 읽어서 실행합니다.
- 인터프리터(Interpreter)
  - Byte Code를 한 줄씩 읽어서 Native Code로 변환

- JIT (Just In Time) 컴파일러
  - Byte Code에서 반복되는 코드 부분은 JIT 컴파일러가 미리 Native Code로 변환 시켜놓음
  - 반복되는 코드가 읽힐 순서가 왔을 때, 인터프리터로 읽지 않고 바로 Native Code를 바로 사용합니다.
  - 인터프리터로 읽을 때의 속도 효율성을 JIT 컴파일러가 보완하는 형태
  - 최초 JVM이 나왔을 당시에는 Interpreter 방식(한 줄씩 해석하고 실행)이었기 때문에 속도가 느리다는 단점이 있었지만, JIT Compiler 방식을 통해 이 점을 보완했습니다.
  - JIT는 Byte Code를 어셈블러 같은 Native Code로 바꿔서 실행이 빠르지만, 변환하는데 비용이 발생합니다.
  - 따라서, JVM은 모든 코드를 JIT Compiler 방식으로 실행하지 않고, Interpreter 방식을 사용하다가 일정한 기준이 넘어가면 JIT Compiler 방식으로 실행합니다.
- 가비지 컬렉터(Garbage Collector)
  - 더 이상 참조되지 않는 객체를 모아서 메모리 정리를 합니다.
  - 경우에 따라 성능 효율을 위해 커스터마이징을 해야함





### Class Loader



- JVM 내부 구조의 클래스 로더 시스템 부분을 좀 더 자세히 살펴봅시다.



![Java 메모리_7](C:\Users\tnfl4\OneDrive\Desktop\취업 스터디\CS정리\res\JAVA\Java 메모리_7.PNG)



- 로딩 -> 링크 -> 초기화 순으로 진행됩니다.

- 로딩 (Loading)

  - `.class` 파일을 읽어서 Byte Code를 Binary Code로 만들고 이를 '메서드' 영역에 저장합니다.

  - 저장하는 데이터는 다음과 같습니다.

    - Fully-Qualified Class Name
      - 클래스 로더, 클래스 패키지 경로, 패키지 이름, 클래스 이름을 모두 포함한 값
    - 클래스 / 인터페이스 / enum(열거형 변수)을 구분하여 저장
    - 메서드와 변수

  - 로딩이 끝나면 해당 클래스 타입의 객체를 생성하여 'Heap' 영역에 저장

  - `BootStrap` -> `Extension` -> `Application` Loader 순으로, 앞의 Loader가 로딩할 수 없으면 그다음 Loader가 읽어내는 방식

    사실상 Application Loader가 읽어낸다고 함

- 링킹(Linking)

  - Verify
    - `.class` 파일 형식이 유효한지 검사합니다.
  - Prepare
    - `static` 변수와 기본 값에 필요한 메모리를 준비합니다.
  - Resolve(Optional)
    - 심볼릭 메모리 레퍼런스를 실제 메모리 레퍼런스로 교체합니다.
    - Optional인 이유는, 이때 교체(binding)될 수도 있고, 이후 사용이 일어날 때 동적으로 교체될 수도 있기 때문

- 초기화(Initialization)

  - `static` 변수를 초기화합니다.

