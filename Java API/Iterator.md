> # Iterator

### `Interface Iterator<E>`



**`알려진 서브 인터페이스`**

- ListIterator <E>

**`알려진 구현 클래스`**

- BeanContextSupport.BCSIterator, Scanner



컬렉션에 대한 반복자입니다. 반복자는 Java Collections Framework 에서 Enumeration을 대신합니다. 반복자는 2가지 면에서 Enumeration과 다릅니다.

1. 반복자를 사용하면 호출자가 잘 정의된 의미 체계로 반복하는 동안, 기본 컬렉션에서 요소를 제거할 수 있습니다.
2. 메서드 이름이 개선되었습니다.

이 인터페이스는 Java Collections Framework의 멤버입니다.



**`도입된 버전`** : 1.2

**`관련 항목`**

- Collection, ListIterator, Enumeration



> # Iterator의 Method



##### **`hasNext`**

```java
boolean hasNext()
    // 반복할 요소가 더 있는 경우 true를 리턴합니다. 즉, next()가 예외를 던지는 대신 요소를 리턴할 경우 true를 리턴합니다.
    Returns
    	반복할 요소가 더 있는 경우, true
```



##### **`next`**

```java
E next()
    // 반복에서 다음 요소를 리턴합니다. hasNext() 메서드가 false를 리턴할 때까지 이 메서드를 반복해 호출하면, 기본으로 하는 컬렉션 내의 각 요소가 한 번만 리턴됩니다.
    Returns
    	반복에서 다음의 요소
    Exceptions
    	NoSuchElementException - 반복할 요소가 더 없는 경우
```



##### **`remove`**

```java
void remove()
    // 기본 컬렉션으로부터 반복자에 의해 마지막에 리턴된 요소를 삭제합니다(선택 작업). 이 메서드는 next() 호출 당 한 번만 호출할 수 있습니다. 이 메서드를 호출하는 것 이외의 방법으로 반복이 진행되는 동안 기본 컬렉션이 수정되면 반복자의 동작이 보장되지 않습니다.
    Exceptions
    	UnsupportedOperationException - Iterator가 remove 오퍼레이션을 지원하지 않는 경우
    	IllegalStateException - next 메서드가 아직 호출되지 않았거나 다음 메서드에 대한 마지막 호출
    							이후 remove 메서드가 이미 호출된 경우
```

