# Java 메모리 구조



***Java 애플리케이션을 개발할 때, 메모리를 잘 아는 것은 중요합니다. 메모리에 어떻게 코드가 적재되는지 이해해야 코드를 최적화할 수 있고 코드 에러를 피할 수 있습니다.***



***메모리 관리가 잘 되지 않는 프로그램은 서비스 속도 저하에서부터 심하게는 서버 불능 상태에 이르기도 합니다.***



***한정된 자원에서 효율적으로 메모리를 사용하여 성능 향상도 가능합니다.***





> ### Method Area(Static Area)



- **JVM이 구동될 때 생성되며 모든 스레드가 공유하는 영역**
- **JVM 구동 중 사용될 클래스 파일을 읽고 클래스 별로 runtime constant pool(런타임 상수 풀), field data(필드 데이터), method data(메서드 데이터), constructor(생성자) 등을 저장**



1. 필드 정보 : 멤버 변수 이름, 데디터 타입, 접근 제어자 등의 정보
2. 메서드 정보 : 메서드 이름, 리턴 타입, 매개변수, 접근 제어자 등의 정보
3. 상수 풀(String Constant Pool)
   - Type에서 사용된 상수를 저장하는 곳(중복이 있을 시 기존의 상수 사용)
   - 문자 상수, 타입, 필드, Method reference도 상수 풀에 저장
   - final class 변수의 경우에도 상수 풀에 값 복사
4. Static 변수
   - 모든 객체가 공유할 수 있고, 객체 생성없이 접근 가능
5. 프로그램 종료까지 메모리에 상주
6. Static 영역 데이터는 프로그램 시작 ~ 종료시까지 메모리에 남아있습니다.
   - 장점 : 프로그램이 종료될 때까지 어디서든 사용이 가능
   - 단점 : 무분별하게 많이 사용하다보면 메모리가 부족





> ### Stack



- **JVM Stack 영역은 스레드가 실행될 때 할당됩니다. (스레드마다 하나씩 존재)**
- **JVM Stack은 메서드를 호출 시, 프레임(Frame)을 추가(Push)하고, 메서드가 종료되면 해당 프레임을 제거(pop)합니다.**
- **실행 순서에 따라 생성되고 소멸됩니다. (Last In First Out(LIFO) 구조)**



애플리케이션이 동작할 때, 프로그램은 메모리에 올라가게 됩니다. JVM에서는 스레드 1개당 독립적인 Stack 공간이 할당됩니다. 아래와 같은 코드가 있을 때, Stack에 코드가 어떻게 적재되어 있는지 알아봅시다.

```java
public class Main {
    public static void main(String[] args) {
        int val = 1;
        val = calculate(value);
        System.out.println(val);
    }
    public static int calculate(int data) {
        int tmp = data + 2;
        int newData = tmp * 2;
        return newData;
    }
}

// 결과 : 6
```

이 코드에서 Stack 상태는 아래와 같습니다.

![Java 메모리_1](https://user-images.githubusercontent.com/31823098/112457656-4f055c80-8d9f-11eb-85d4-3b6a8c1fcaa0.PNG)

이 상태는 calculate() 메서드가 호출되었을 때이며, calculate() 메서드가 결과 값을 return 하게 되면 이 메서드에서 사용한 tmp와 newData 값은 Stack에서 pop됩니다.

따라서 결국엔 calculate() 메서드에서 return된 newData의 값 20이 val에 새롭게 저장되어 아래와 같은 Stack 상태가 됩니다.

![Java 메모리_2](https://user-images.githubusercontent.com/31823098/112457708-5cbae200-8d9f-11eb-8bb6-f2210647cdda.PNG)

또한, val과 args는 main() 메서드 안에 존재하는 값이므로, main() 메서드가 종료되는 시점에 모든 값이 Stack에서 pop되어 Stack은 완전히 비게 됩니다.





> ### Heap



- **객체 배열이 생성되는 영역**
- **해당 영역에 생성된 객체와 배열은 JVM Stack 영역의 변수나 다른 객체의 필드에서 참조합니다.**
- **만약, 참조하는 변수나 필드가 없으면 JVM이 Garbage Collector를 실행하여 해당 객체를 제거합니다.**



1. 객체(인스턴스 - new 연산자로 생성된 객체)가 저장되는 영역

2. 프로그램 실행 중 생성되는 모든 객체는 Heap 영역에 동적으로 할당

   - Garbage Collector를 통해 메모리 반환

3. 참조형(Reference Type) 데이터 타입을 갖는 객체(인스턴스), 배열 등은 Heap 영역에 데이터가 저장됩니다.

   (실제 데이터가 저장된 Heap 영역의 참조값(reference value, 해시코드 / 메모리에 저장된 주소를 연결해주는 값)을 저장)



Heap은 Stack과 다르게 프로세스 전역에서 공유하는 공간입니다. Java의 모든 객체들은 Heap 영역에 저장됩니다.(기본 자료형은 Stack에 저장됩니다.)

```java
int num = 1;
String str = "java";
```

이 코드에서 Stack과 Heap의 상태를 보면 다음과 같습니다.



![Java 메모리_3](https://user-images.githubusercontent.com/31823098/112457713-5f1d3c00-8d9f-11eb-9b10-269f4bc8618d.PNG)

```java
public class Main {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        list.add("one");
        list.add("two");
        list.add("three");
    }
}
```

좀 더 복잡한 위의 코드로 Java 메모리 할당 과정을 알아보겠습니다.

![Java 메모리_4](https://user-images.githubusercontent.com/31823098/112457724-617f9600-8d9f-11eb-8a6c-4563012d5772.PNG)





**결과적으로,**

1. **`객체는 Heap 영역에 저장되고, 객체를 참조하는 변수는 Stack 영역에 저장됩니다.`**
2. **`또한, 지역 변수는 Stack에 저장됩니다.`**



