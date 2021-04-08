# Call By Value vs Call By Reference



- 메소드의 인자 호출 방식에는 `Call By Value(값에 의한 호출)`와 `Casll By Reference(참조에 의한 호출)` 두 가지 방식이 있습니다.



> ### Call By Value

- 메소드 호출 시에 사용되는 인자의 메모리에 저장되어 있는 `값`을 복사하여 보내는 방식입니다.
- 메소드 인자로 byte, char, short, int, long, float, double, boolean 등 자바 기본 타입(Primitive Type)이 전달되는 경우에는 인자의 값(상수 값)이 복사되어 전달됩니다.
- 메소드 인자로 객체에 대한 레퍼런스(Reference Type)가 전달되는 경우에는 객체 자체가 복사되어 전달되는 것이 아니라, 그 객체를 가리키는 레퍼런스 값이 복사되어 전달됩니다.



> ### Call By Reference

- 메소드 호출 시에 사용되는 인자 값의 메모리에 저장되어 있는 `주소`를 복사하여 보내는 방식입니다.
- 메서드 호출 시 전달하려는 인자로 참조(객체) 자료형을 사용한 경우를 의미
- 하나의 객체를 참조하는 변수가 2개가 되어 어느 한 곳에서 수정을 하게 되면 같은 객체를 참조하는 다른 쪽에서도 영향을 받게 됨



> ### Java는 Call By Value 인가? Call By Reference 인가?

결론부터 말하면 Java는 Call By Value 입니다. Call By Reference의 경우, 인자가 전달될 때 인자 값의 메모리에 저장되어 있는`주소`값을 복사하여 보내는 방식인데, Java에서 인자 전달 시 주소 값을 보내는 경우는 없습니다. Primitive Type의 인자를 보낼 때에는 인자의 값(상수 값)을 복사해 보내고, Reference Type의 인자를 보낼 때에는 인자의 레퍼런스 값을 복사해 보내기 때문에 Java의 인자 전달 방식은 Call By Value로 보는 것이 맞습니다.

예를 들어 살펴보겠습니다.

```java
public class CallByValue {
    static class A {
        int num;
        public A(int num) {
            this.num = num;
        }
    }
    public static void main(String[] args) {
        A a = new A(1);
        System.out.println("num : " + a.num);
        callByValue(a);
        System.out.println("num : " + a.num);
    }
    public static callByValue(A a) {
        a = new A(2);
    }
}
```

위의 코드를 실행했을 때, 만약 Java의 인자 전달 방식이 Call By Reference라면

```text
num : 1
num : 2
```

위의 결과가 나와야 합니다. 

하지만 위 코드를 실행했을 때 아래와 같은 결과가 나옵니다.

```text
num : 1
num : 1
```

Java는 인자 전달 시, 주소 값을 복사해서 보내는 방식이 아니라 레퍼런스 값을 복사해서 보내는 방식이기 때문에 Java의 인자 전달 방식은 Call By Value로 보는 것이 맞습니다.







> ## References
>
> - https://sejun-s.tistory.com/18
> - https://neos518.tistory.com/27
> - https://lbmmbl.tistory.com/22
> - http://wonwoo.ml/index.php/post/1679