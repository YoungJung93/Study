> # List

### `Interface List<E>`



**`모든 상위 인터페이스`**

- Collection <E>, Iterable <E>

**`알려진 구현 클래스`**

- AbstractList, AbstractSequentialList, ArrayList, AttributeList, CopyOnWriteArrayList, LinkedList, RoleList, RoleUnresolvedList, Stack, Vector



순서를 갖는 컬렉션입니다(시퀀스라고도 함). 이 인터페이스의 사용자는 리스트에서 각 요소가 삽입되는 위치를 정확하게 제어할 수 있습니다. 사용자는 정수 값의 인덱스(리스트 내의 위치)로 요소에 접근하거나 리스트에서 요소를 검색할 수 있습니다.

Set과 다르게 리스트는 일반적으로 중복 요소를 허용합니다. 즉, 리스트는 일반적으로 e1.equals(e2)과 같은 e1 및 e2 요소 쌍을 허용합니다. 또, null 요소를 허가하는 경우에는 일반적으로 복수의 null 요소를 허용합니다. 사용자가 중복된 값을 삽입하려고 했을 때, Runtime Exception을 Throw 함으로써 중복 요소를 금지하는 리스트를 구현하는 경우도 있지만, 이와 같이 사용되는 경우는 거의 없습니다.

List 인터페이스는 iterator, add, remove, equals 및 hashCode 메서드의 규약에 Collection 인터페이스에 지정된 것 외에 추가 규정을 적용합니다. 편의를 위해 다른 상속 메서드의 선언도 여기에 포함됩니다.

List 인터페이스는 리스트의 요소에 대한 위치(인덱스)에 접근하기 위한 4가지 메서드를 제공합니다. Java 배열과 같이 List의 인덱스는 0으로부터 시작됩니다. 일부 구현(LinkedList 클래스 등)에서는 이러한 오퍼레이션 실행에 인덱스 값에 비례하는 시간이 걸리는 경우가 있습니다. 따라서 호출자가 이러한 구현에 대해 모르는 경우, 리스트의 요소를 통해 인덱싱하는 것보다 일반적으로 리스트 내의 요소를 반복하는 것이 바람직합니다.

List 인터페이스는 `ListIterator`라는 특수 반복자를 제공하여 Iterator 인터페이스가 제공하는 일반 작업에 더해 요소의 삽입, 교체 및 양방향 접근을 제공합니다. 리스트의 지정된 위치에서 시작되는 리스트 반복자를 가져오는 메서드가 제공됩니다.

List 인터페이스는 지정된 객체를 검색하기 위한 2가지 메서드를 제공합니다. 성능 관점에서 이러한 메서드는 주의해서 사용해야 합니다. 많은 구현에서 이러한 메서드는 시간이 많이 걸리는 선형 검색을 수행합니다.

List 인터페이스는 리스트의 임의의 지점에 복수의 요소를 효율적으로 삽입 및 제거하는 2가지 메서드를 제공합니다. 

참고 : 리스트 자체가 요소로 포함되는 것은 허용되지만 매우 주의해야 합니다. 그러한 리스트에서 equals 및 hashCode 메서드의 동작은 보장되지 않습니다.

일부 리스트의 구현에는 포함할 수 있는 요소에 제한이 있는 경우도 있습니다. 예를 들어, 일부 구현에서는 null 요소를 금지하고, 일부 구현에는 요소의 형태에 제한이 있기도 합니다. 적합하지 않은 요소의 삽입을 시도하면 일반적으로 NullPointerException 또는 ClassCastException과 같은 `Unchecked Exception`이 Throw됩니다. 적합하지 않은 요소를 검색하려고 하면 예외가 발생하거나 단순히 false가 리턴될 수도 있습니다. 일부 구현은 전자의 동작을, 일부는 후자의 동작을 나타냅니다. 즉, 리스트에 삽입되지 않는 적합하지 않은 요소를 처리하려고 하면, 구현 옵션에 따라 예외가 발생하는 경우도 있지만 처리가 유효하게 되는 경우도 있습니다. 이 인터페이스에 관한 그러한 예외는 "선택 사항"으로 표시됩니다.

이 인터페이스는 `Java Collections Framework` 멤버입니다.



**`도입된 버전`** : 1.2

**`관련 항목`**

- Collection, Set, ArrayList, LinkedList, Vector, Arrays.asList(Object[]), Collections.nCopies(int, Object), Collections.EMPTY_LIST, AbstractList, AbstractSequentialList





> # List의 Method



##### **`size`**

```java
int size()
    // 리스트 내의 요소 수를 리턴합니다. 이 리스트에 Integer.MAX_VALUE 보다 많은 수의 요소가 있는 경우, Integer.MAX_VALUE를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 size
    Returns
    	리스트 내의 요소 수
```



##### **`isEmpty`**

```java
boolean isEmpty()
    // 리스트 내에 요소가 없는 경우, true를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 isEmpty
    Returns
    	리스트가 요소를 포함하고 있지 않은 경우, true
```



##### **`contains`**

```java
boolean contains(Object o)
    // 리스트 내에 지정된 요소가 포함되어 있는 경우, true를 리턴합니다. 즉, 리스트에 (o==null ? e==null : o.equals(e))가 되는 요소 e가 1개 이상 포함되어 있는 경우에만 true를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 contains
    Parameters
    	o - 리스트 내에 있을지를 조사할 요소
    Returns
    	리스트가 지정된 요소를 포함하고 있는 경우, true
    Exceptions
    	ClassCastException - 지정된 요소의 형태가 이 리스트와 호환되지 않는 경우(선택 사항)
    	NullPointerException - 지정된 요소가 null이고, 이 리스트가 null 요소를 지원하지 않는 경우
    							(선택 사항)
```



##### **`iterator`**

```java
Iterator <E> iterator()
    // 이 리스트 내의 요소를 적절한 순서로 반복 처리하는 반복자를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 iterator
    	인터페이스 Iterable <E> 내의 iterator
    Returns
		리스트 내의 요소를 적절한 순서로 반복 처리하는 반복자
```



##### **`toArray`**

```java
Object[] toArray()
    // 리스트 내의 모든 요소를 적절한 순서로 포함하고 있는 배열을 리턴합니다. Collection.toArray 메서드의 일반 규약에 따릅니다.
    Specified by
    	인터페이스 Collection <E> 내의 toArray
    Returns
    	리스트 내의 모든 요소를 적절한 순서로 포함하고 있는 배열
    References
    	Arrays.asList(Object[])
    
<T> T[] toArray(T[] a)
    // 리스트 내의 모든 요소를 적절한 순서로 포함하고 있는 배열을 리턴합니다. 리턴된 배열의 런타임 유형은 지정된 배열의 런타임 유형이 됩니다. Collection.toArray(Object[]) 메서드의 일반 규약에 따릅니다.
    Specified by
    	인터페이스 Collection <E> 내의 toArray
    Parameters
    	a - 이 리스트의 요소가 충분히 큰 경우, 저장할 배열. 그렇지 않은 경우, 동일한 런타임 유형의
    		새 배열이 이 목적으로 할당됩니다.
    Returns
    	리스트의 내의 모든 요소를 적절한 순서로 포함하고 있는 배열
    Exceptions
    	ArrayStoreException - 지정된 배열의 런타임 유형이 리스트 내 각 요소의 런타임 유형의 슈퍼
    							타입이 아닌 경우
    	NullPointerException - 지정된 배열이 null인 경우
```



##### **`add`**

```java
boolean add(E o)
    // 지정된 요소를 리스트의 마지막에 삽입합니다.(선택 작업)
    // 이 오퍼레이션을 지원하는 리스트는 이 리스트에 추가할 수 있는 요소에 제한을 둘 수 있습니다. 특히, 일부 리스트는 null 요소의 삽입을 거부하고, 어떤 리스트는 삽입할 수 있는 요소 유형에 제한을 부과합니다. List 클래스는 리스트에 추가할 수 있는 요소에 대해 제약이 있으면, 문서로 그것을 명시해야할 필요가 있습니다.
    Specified by
    	인터페이스 Collection <E> 내의 add
    Parameters
    	o - 리스트에 삽입할 요소
    Returns
    	true (Collection.add 메서드의 일반 규약에 따릅니다.)
    Exceptions
    	UnsupportedOperationException - 리스트가 add 메서드를 지원하고 있지 않은 경우
    	ClassCastException - 지정된 요소의 클래스를 이 리스트에 삽입할 수 없는 경우
    	NullPointerException - 지정된 요소가 null이고 이 리스트가 null 요소를 지원하지 않는 경우
    	IllegalArgumentException - 이 요소의 특성 상, 이 리스트에 삽입할 수 없는 경우
```



##### **`remove`**

```java
boolean remove(Object o)
    // 리스트 내에서 지정된 요소가 최초로 검출되었을 때, 그 요소를 삭제합니다(선택 작업). 리스트에 그 요소가 없는 경우, 변경되지 않습니다. 즉, (o==null ? get(i)==null : o.equals(get(i)))가 되는 최소의 인덱스 값 i를 가지는 요소를 삭제합니다(그러한 요소가 존재하는 경우).
    Specified by
    	인터페이스 Collection <E> 내의 remove
    Parameters
    	o - 리스트로부터 삭제할 요소(그 요소가 있는 경우)
    Returns
    	리스트가 지정된 요소를 포함하고 있는 경우, true
    Exceptions
    	ClassCastException - 지정된 요소의 형태가 이 리스트와 호환되지 않는 경우(선택 사항)
    	NullPointerException - 지정된 요소가 null이고 이 리스트가 null 요소를 지원하지 않는 경우
    							(선택 사항)
    	UnsupportedOperationException - 리스트가 remove 메서드를 지원하고 있지 않은 경우
```



##### **`containsAll`**

```java
boolean containsAll(Collection <?> c)
    // 지정된 컬렉션의 모든 요소가 리스트에 포함되어 있는 경우, true를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 containsAll
    Parameters
    	c - 이 리스트에 있을지를 조사할 컬렉션
    Returns
    	지정된 컬렉션의 모든 요소가 리스트에 포함되어 있는 경우, true
    Exceptions
    	ClassCastException - 지정된 컬렉션의 일부 요소의 형태가 이 리스트화 호환되지 않는 경우
    							(선택 사항)
    	NullPointerException - 지정된 컬렉션이 1개 이상의 null 요소를 포함하고, 이 리스트가 null
    							요소를 지원하지 않는 경우(선택 사항)
    	NullPointerException - 지정된 컬렉션이 null인 경우
    References
    	contains(Object)
```



##### **`addAll`**

```java
boolean addAll(Collection <? extends E> c)
    // 지정된 컬렉션 내의 모든 요소를 지정된 컬렉션의 반복자에 의해 리턴된 순서대로 리스트의 마지막에 추가합니다(선택 작업). 지정된 컬렉션이 이 작업 진행 중에 변경될 경우, 이 오퍼레이션의 동작은 보장되지 않습니다. 즉, 지정된 컬렉션이 이 리스트이고, 비어 있지 않은 경우 이 문제가 발생합니다.
    Specified by
    	인터페이스 Collection <E> 내의 addAll
    Parameters
    	c - 리스트에 삽입될 요소가 담긴 컬렉션
    Returns
    	이 호출의 결과, 리스트가 변경되었을 경우, true
    Exceptions
    	UnsupportedOperationException - 리스트가 addAll 메서드를 지원하고 있지 않은 경우
    	ClassCastException - 지정된 컬렉션 내 요소의 클래스를 이 리스트에 삽입할 수 없는 경우
    	NullPointerException - 지정된 컬렉션에 하나 이상의 null 요소가 포함되어 있고 이 리스트가
    							null 요소를 지원하지 않는 경우 또는 지정된 컬렉션이 null인 경우
    	IllegalArgumentException - 지정된 컬렉션 내 요소의 특성 상, 이 리스트에 삽입할 수 없는 경우
    References
    	add(Object)
    
boolean addAll(int index, Collection <? extends E> c)
    // 지정된 컬렉션 내의 모든 요소를 리스트의 지정된 위치에 삽입합니다(선택 작업). 현재 그 위치에 있는 요소와 후속의 요소는 오른쪽으로 이동합니다(인덱스 값이 증가). 새로운 요소는 지정된 컬렉션의 반복자에 의해 리턴된 순서대로 리스트에 삽입됩니다. 지정된 컬렉션이 이 작업 진행 중에 변경될 경우, 이 오퍼레이션의 동작은 보장되지 않습니다. 즉, 지정된 컬렉션이 이 리스트이고, 비어 있지 않은 경우 이 문제가 발생합니다.
    Parameters
    	index - 지정된 컬렉션으로부터 최초의 요소를 삽입할 위치의 인덱스
    	c - 리스트에 삽입될 요소가 담긴 컬렉션
    Returns
    	이 호출의 결과, 리스트가 변경되었을 경우, true
    Exceptions
    	UnsupportedOperationException - 리스트가 addAll 메서드를 지원하고 있지 않은 경우
    	ClassCastException - 지정된 컬렉션 내 요소의 클래스를 이 리스트에 삽입할 수 없는 경우
    	NullPointerException - 지정된 컬렉션에 하나 이상의 null 요소가 포함되어 있고 이 리스트가
    							null 요소를 지원하지 않는 경우 또는 지정된 컬렉션이 null인 경우
    	IllegalArgumentException - 지정된 컬렉션 내 요소의 특성 상, 이 리스트에 삽입할 수 없는 경우
    	IndexOutOfBoundsException - 인덱스가 범위 외에 있을 경우(index<0 || index>size))
```



##### **`size`**

```java
int size()
    // 리스트 내의 요소 수를 리턴합니다. 이 리스트에 Integer.MAX_VALUE 보다 많은 수의 요소가 있는 경우, Integer.MAX_VALUE를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 size
    Returns
    	리스트 내의 요소 수
```



##### **`size`**

```java
int size()
    // 리스트 내의 요소 수를 리턴합니다. 이 리스트에 Integer.MAX_VALUE 보다 많은 수의 요소가 있는 경우, Integer.MAX_VALUE를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 size
    Returns
    	리스트 내의 요소 수
```



##### **`size`**

```java
int size()
    // 리스트 내의 요소 수를 리턴합니다. 이 리스트에 Integer.MAX_VALUE 보다 많은 수의 요소가 있는 경우, Integer.MAX_VALUE를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 size
    Returns
    	리스트 내의 요소 수
```



##### **`size`**

```java
int size()
    // 리스트 내의 요소 수를 리턴합니다. 이 리스트에 Integer.MAX_VALUE 보다 많은 수의 요소가 있는 경우, Integer.MAX_VALUE를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 size
    Returns
    	리스트 내의 요소 수
```



##### **`size`**

```java
int size()
    // 리스트 내의 요소 수를 리턴합니다. 이 리스트에 Integer.MAX_VALUE 보다 많은 수의 요소가 있는 경우, Integer.MAX_VALUE를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 size
    Returns
    	리스트 내의 요소 수
```



##### **`size`**

```java
int size()
    // 리스트 내의 요소 수를 리턴합니다. 이 리스트에 Integer.MAX_VALUE 보다 많은 수의 요소가 있는 경우, Integer.MAX_VALUE를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 size
    Returns
    	리스트 내의 요소 수
```



##### **`size`**

```java
int size()
    // 리스트 내의 요소 수를 리턴합니다. 이 리스트에 Integer.MAX_VALUE 보다 많은 수의 요소가 있는 경우, Integer.MAX_VALUE를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 size
    Returns
    	리스트 내의 요소 수
```



