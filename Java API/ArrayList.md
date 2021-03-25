> # **ArrayList**

#### `Class ArrayList<E>`



**`구현된 모든 인터페이스` : Serializable, Cloneable, Iterable<E>, Collection<E>, List<E>, RandomAccess**

**`알려진 직계 서브 클래스` : AttributeList, RoleList, RoleUnresolvedList**



`List 인터페이스`의 사이즈 변경 가능한 배열의 구현입니다. 리스트의 임의의 오퍼레이션을 모두 구현해, null을 포함한 모든 요소를 허용합니다. 이 클래스는 `List 인터페이스`를 구현하는 것 외에 리스트를 포함하기 위해서 내부적으로 사용되는 배열의 사이즈를 조작하는 메서드를 제공합니다. (이 클래스는 동기화되지 않는 것을 제외하고 `Vector`와 거의 동일)

`size()`, `isEmpty()`, `get()`, `set()`, `iterator` 및 `listIterator` 처리는 일정한 시간에 실행됩니다. `add()` 처리도 일정한 상각 시간에 실행됩니다. 즉, n개의 요소를 추가하려면 O(n) 시간이 필요합니다. 대부분의 경우, 다른 모든 처리도 비례적인 시간에 실행됩니다. 정수의 계수는 `LinkedList` 구현의 경우보다 작아집니다.

각 `ArrayList 인스턴스`에는 `사이즈`가 있습니다. 그것은 리스트의 요소를 포함하기 위해서 사용하는 배열의 사이즈로 항상 리스트의 사이즈 이상의 크기가 됩니다. `ArrayList`에 요소를 추가하면, 그 사이즈는 자동적으로 확대합니다. 확대의 정책에 대해서는 요소를 추가하면 `일정한 상각 시간 코스트`가 수반되는 것 이외에는 자세하게 지정되지 않습니다.

Application에서는 `ensureCapacity`를 사용해 `ArrayList 인스턴스`의 사이즈를 확대하고 나서 많은 요소를 추가할 수 있습니다. 이것은 재할당의 수를 줄일 수 있습니다.

**`이 구현은 동기화되지 않는다는 점에 주의해주세요.`** 다수의 Thread가 동시에 `ArrayList 인스턴스`에 접속해 1개 이상의 Thread가 구조적으로 리스트를 변경하는 경우에는 리스트를 외부적으로 동기화할 필요가 있습니다. 구조적인 변경이란 1개 이상의 요소를 추가 또는 삭제하거나 기본으로 정해진 배열의 사이즈를 명시적으로 변경하는 등의 처리입니다. 요소의 값만을 설정하는 처리는 구조적인 변경이 아닙니다. 보통, 리스트를 동기화하려면 리스트를 자연스럽게 캡슐화하는 객체로 동기를 취합니다. 그러한 객체가 없는 경우에는 `Collections.synchronizedList` 메서드를 사용해 리스트를  "wrapped" 합니다. 이것은 실수로 동기화되지 않은 리스트에 접근하는 것을 막기 위해서 작성 시에 실시하는 것이 최적입니다.

```java
List list = Collections.synchronizedList(new ArrayList(...));
```

이 클래스의 `iterator` 및 `listIterator` 메서드에 의해 리턴된 반복자는 `Fail-fast`입니다. 반복자의 작성 후에 반복자 자체의 `remove()` 또는 `add()` 메서드 이외의 방법으로 리스트를 구조적으로 변경하면, 반복자는 `ConcurrentModificationException`을 Throw 합니다. 따라서, 동시 변경을 하면 반복자는 장래의 예측할 수 없는 시점에 있어, 예측할 수 없는 동작이 발생하는 위험을 회피하기 위해서 신속하게, 깨끗하게 실패합니다.

보통, 비동기의 동시 변경이 있는 경우, 확실한 보증을 실시하는 것은 불가능해서 반복자의 `Fail-fast`의 동작을 보증할 수 없습니다. `Fail-fast` 반복자는 최선 노력 원칙에 기반해 `ConcurrentModificationException`을 Throw 합니다. 따라서, 정확을 기하기 위해서 이 예에외 의존된 프로그램을 쓰는 것은 잘못입니다. 반복자의 `Fail-fast` 동작은 버그를 감지하는 데에만 사용되어야 합니다.

이 클래스는 `Java Collections Framework` 멤버입니다.



#### `Fail-fast`

- 자바2 이전 버전에서 사용되던 `Vector`, `HashTable`의 뷰 객체인 Enumeration은 Fail-fast 방식이 아니었으나, 자바2의 `Collection 프레임워크`에서 컬렉션 뷰인 `Iterator`, `listIterator` 객체는 `Fail-fast` 방식입니다.

- 컬렉션 뷰는 컬렉션 객체에 저장된 객체들에 대한 순차적 접근을 제공합니다. 그러나 뷰 객체인 `Enumeration` 또는 `Iterator 객체`를 얻고 나서 순차적 접근이 끝나기 전에 뷰 객체를 얻은 하부 컬렉션 객체에 변경이 일어날 경우, 순차적 접근에 실패하게 된다. 여기서 변경이라는 것은 컬렉션에 객체가 추가되거나 제거되는 것과 같이 컬렉션 구조의 변경이 일어나는 경우를 말합니다.

  이런 상황은 멀티스레드 구조와 이벤트 구동 모델에서 일어날 수 있으며, 개발자가 혼자 테스트할 경우 발견하기 어려운 문제입니다. 따라서 정확한 이해와 예상이 필요하며 이에 대한 대처 방안을 마련해야 합니다.

- 하부 컬렉션 객체에 변경이 일어나 순차적 접근에 실패하면 `Enumeration 객체`는 실패를 무시하고 순차적 접근을 끝까지 제공합니다. `Iterator 객체`는 하부 컬렉션 객체에 변경이 일어나 순차적 접근에 실패하면 `ConcurrentModificationException` 예외를 발생합니다. **이처럼 순차적 접근에 실패하면 예외를 발생하도록 되어 있는 방식을 `Fail-fast`라고 합니다.**

- `Iterator`는 `Fail-fast` 방식으로 하부 컬렉션에 변경이 발생했을 경우, 신속하고 결함이 없는 상태를 만들기 위해 Iterator의 탐색을 실패한 것으로 하여 예외를 발생하며, 이렇게 함으로써 안전하지 않을지도 모르는 행위를 수행하는 위험을 막습니다. 왜냐하면 이러한 위험은 실행 중 불특정한 시간에 멋대로 결정되지 않은 행위를 할 가능성이 있기 때문에 안전하지 않다고 할 수 있기 때문입니다.





> ## ArrayList의 Method



### **`ArrayList`**

```java
public ArrayList(int initialCapacity)
    // 지정된 초기 사이즈로 비어있는 리스트를 작성합니다.
    Parameters
    	initialCapacity - 리스트의 초기 사이즈
    Exceptions
    	IllegalArgumentException - 지정된 초기 사이즈가 음수인 경우

public ArrayList()
    초기 사이즈 10으로 비어있는 리스트를 작성합니다.
    
public ArrayList(Collection <? extends E> c)
    // 지정된 컬렉션의 요소를 포함한 리스트를 작성합니다. 이러한 요소는 컬렉션의 반복자가 돌려주는 순서로 포함됩니다. ArrayList 인스턴스의 초기 사이즈는 지정된 컬렉션 사이즈의 110%입니다.
    parameters
    	c - 요소가 리스트에 배치되는 컬렉션
    Exceptions
    	NullPointerException - 지정된 컬렉션이 null인 경우
```



### **`trimToSize`**

```java
public void trimToSize()
    // 이 ArrayList 인스턴스의 사이즈를 리스트의 현재 사이즈로 축소합니다. 어플리케이션에서는 이 오퍼레이션으로 ArrayList 인스턴스의 포함 사이즈를 최소로 할 수 있습니다.
```



### **`ensureCapacity`**

```java
public void ensureCapacity(int minCapacity)
    // 필요에 따라서, 이 ArrayList 인스턴스의 사이즈를 확대해, 적어도 최소 사이즈 인수로 지정된 수의 요소를 포함할 수 있도록 합니다.
    Parameters
    	minCapacity - 보증하고 싶은 최소 사이즈
```



### **`size`**

```java
public int size()
    // 리스트 내에 있는 요소의 수를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 size
    	인터페이스 List <E> 내의 size
    	클래스 AbstractCollection <E> 내의 size
    Returns
    	리스트 내의 요소 수
```



### **`isEmpty`**

```java
public boolean isEmpty()
    // 리스트에 요소가 있는지 없는지를 판정합니다.
    Specified by
    	인터페이스 Collection <E> 내의 isEmpty
    	인터페이스 List <E> 내의 isEmpty
    Overrides
    	클래스 AbstractCollection <E> 내의 isEmpty
    Returns
    	리스트에 요소가 없는 경우 true, 그렇지 않은 경우 false
```



### **`contains`**

```java
public boolean contains(Object elem)
    // 리스트로 지정된 요소가 있는 경우에 true를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 contains
    	인터페이스 List <E> 내의 contains
    Overrides
    	클래스 AbstractCollection <E> 내의 contains
    Parameters
    	elem - 리스트에 있을지 없을지를 조사하는 요소
    Returns
    	지정된 요소가 있는 경우 true, 그렇지 않은 경우 false
```



### **`indexOf`**

```java
public int indexOf(Object elem)
    // equals() 메서드를 사용해 동일한지를 판정하면서 지정된 인수와 같은 내용의 요소를 선두로부터 검색합니다.
    Specified by
    	인터페이스 List <E> 내의 indexOf
    Overrides
    	클래스 AbstractList <E> 내의 indexOf
    Parameters
    	elem - 검색할 요소
    Returns
    	리스트 내에서 인수가 최초로 나타나는 인덱스. 객체가 발견되지 않는 경우 -1
    References
    	Object.equals(Object)
```



### **`lastIndexOf`**

```java
public int lastIndexOf(Object elem)
    // 지정된 객체가 리스트 내에서 마지막에 나타나는 인덱스를 리턴합니다.
    Specified by
    	인터페이스 List <E> 내의 lastIndexOf
    Overrides
    	클래스 AbstractList <E> 내의 lastIndexOf
    Parameters
    	elem - 검색할 요소
    Returns
    	리스트로 지정된 객체와 일치하는 마지막 객체의 인덱스, 객체가 발견되지 않는 경우 -1
```



### **`clone`**

```java
public Object clone()
    // ArrayList 인스턴스의 복사본을 리턴합니다. 요소 자체는 카피되지 않습니다.
    Overrides
    	클래스 Object 내의 clone
    Returns
    	이 ArrayList 인스턴스의 복제
    References
    	Cloneable
```



### **`toArray`**

```java
public Object[] toArray()
    // 리스트의 모든 요소를 포함하는 배열을 적절한 순서로(첫번째 요소부터 마지막 요소까지) 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 toArray
    	인터페이스 List <E> 내의 toArray
    Overrides
    	클래스 AbstractCollection <E> 내의 toArray
    Returns
    	리스트 내의 모든 요소를 포함하는 배열
    References
    	Arrays.asList(Object[])
    
public <T> T[] toArray(T[] a)
    // 리스트의 모든 요소를 포함하는 배열을 적절한 순서로 리턴합니다. 리턴된 배열의 런타임 유형은 지정된 배열의 런타임 유형입니다. 지정된 배열에 리스트가 들어가 있는 경우는 그 배열이 리턴됩니다. 그 외의 경우는 지정된 배열의 런타임 유형과 리스트의 사이즈를 이용해 새로운 배열을 할당합니다.
    // 배열에 리스트보다 많은 요소가 있는 경우, 컬렉션의 끝에 있는 배열의 요소는 null로 설정됩니다.
    Specified by
    	인터페이스 Collection <E> 내의 toArray
    	인터페이스 List <E> 내의 toArray
    Overrides
    	클래스 AbstractCollection <E> 내의 toArray
    Parameters
    	a - 배열이 충분한 크기를 가지는 경우는 리스트의 요소가 포함되는 배열. 그렇지 않은 경우는 
    		요소를 포함하기 위해서 같은 런타임 유형의 새로운 배열을 할당할 수 있습니다.
    Returns
    	리스트의 요소가 포함되어 있는 배열
    Exceptions
    	ArrayStoreException - 지정된 배열의 런타임 유형이 이 리스트에 있는 모든 요소의 런타임 유형의
    							상위 유형이 아닌 경우
    	NullPointerException - 지정한 배열이 null인 경우
```



### **`get`**

```java
public E get(int index)
    // 리스트 내에 지정된 위치에 있는 요소를 리턴합니다.
    Specified by
    	인터페이스 List <E> 내의 get
    	클래스 AbstractList <E> 내의 get
    Parameters
    	index - 리턴될 요소의 인덱스
    Returns
    	리스트 내에 지정된 위치에 있는 요소
    Exceptions
    	IndexOutOfBoundsException - 인덱스가 범위 외의 경우일 때
```



### **`set`**

```java
public E set(int index, E element)
    // 리스트에 지정된 위치에 있는 요소를 지정된 요소로 교체합니다.
    Specified by
    	인터페이스 List <E> 내의 set
    Overrides
    	클래스 AbstractList <E> 내의 set
    Parameters
    	index - 치환되는 요소의 인덱스
    	element - 지정된 위치에 저장될 요소
    Returns
    	이전에 지정된 위치에 있던 요소
    Exceptions
    	IndexOutOfBoundsException - 인덱스가 범위 외의 경우일 때
```



### **`add`**

```java
public boolean add(E o)
    // 리스트의 마지막에 지정된 요소를 추가합니다.
    Specified by
    	인터페이스 Collection <E> 내의 add
    	인터페이스 List <E> 내의 add
    Overrides
    	클래스 AbstractList <E> 내의 add
    Parameters
    	o - 리스트에 추가되는 요소
    Returns
    	true (Collection.add(E)에 정의된 대로)
    
public void add(int index, E element)
    // 리스트에 지정된 위치에 지정된 요소를 삽입합니다. 현재 그 위치에 있는 요소와 후속의 요소는 오른쪽으로 이동합니다.
    Specified by
    	인터페이스 List <E> 내의 add
    Overrides
    	클래스 AbstractList <E> 내의 add
    Parameters
    	index - 지정된 요소가 삽입되는 인덱스
    	element - 삽입되는 요소
    Exceptions
    	IndexOutOfBoundsException - 인덱스가 범위 외의 경우일 때
```



### **`remove`**

```java
public E remove(int index)
    // 리스트 내에 지정된 위치의 요소를 삭제합니다. 그리고 후속의 요소를 왼쪽으로 이동합니다.
    Specified by
    	인터페이스 List <E> 내의 remove
    Overrides
    	클래스 AbstractList <E> 내의 remove
    Parameters
    	index - 삭제되는 요소의 인덱스
    Returns
    	리스트로부터 삭제한 요소
    Exceptions
    	IndexOutOfBoundsException - 인덱스가 범위 외의 경우일 때
    
public boolean remove(Object o)
    // 지정된 요소의 인스턴스가 이 리스트에 있으면, 그 인스턴스를 리스트로부터 1개 삭제합니다. 지정된 요소를 가진 인스턴스가 여러 개라면, 가장 낮은 인덱스를 가진 요소를 삭제합니다. 호출의 결과로 리스트가 변경된 경우 true를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 remove
    	인터페이스 List <E> 내의 remove
    Overrides
    	클래스 AbstractCollection <E> 내의 remove
    Parameters
    	o - 리스트로부터 삭제되는 요소 (그 요소가 있는 경우)
    Returns
    	리스트가 지정된 요소를 포함하고 있는 경우 true
```



### **`clear`**

```java
public void clear()
    // 리스트로부터 모든 요소를 삭제합니다. 이 호출 후에 이 리스트는 비워집니다.
    Specified by
    	인터페이스 Collection <E> 내의 clear
    	인터페이스 List <E> 내의 clear
    Overrides
    	클래스 AbstractList <E> 내의 clear
```



### **`addAll`**

```java
public boolean addAll(Collection <? extends E> c)
    // 리스트의 끝에 지정된 컬렉션의 모든 요소를 추가합니다. 작업이 진행 중인 동안 지정된 컬렉션이 수정되면 이 작업의 동작은 정의되지 않습니다.
    Specified by
    	인터페이스 Collection <E> 내의 addAll
    	인터페이스 List <E> 내의 addAll
    Overrides
    	클래스 AbstractCollection <E> 내의 addAll
    Parameters
    	c - 리스트에 삽입할 요소
    Returns
    	이 호출의 결과, 이 리스트가 변경되었을 경우 true
    Exceptions
    	NullPointerException - 지정된 컬렉션이 null인 경우
    References
    	AbstractCollection.add(Object)
    
public boolean addAll(int index, Collection <? extends E> c)
    // 리스트 내의 지정된 위치로부터, 지정된 컬렉션의 모든 요소를 추가합니다. 지정된 위치에 요소가 있는 경우, 그 위치의 요소와 후속의 요소들을 오른쪽으로 이동합니다.
    Specified by
    	인터페이스 List <E> 내의 addAll
    Overrides
    	클래스 AbstractList <E> 내의 addAll
    Parameters
    	index - 지정된 컬렉션으로부터 최초의 요소를 삽입하는 위치의 인덱스
    	c - 리스트에 삽입되는 요소
    Returns
    	이 호출의 결과, 이 리스트가 변경되었을 경우 true
    Exceptions
    	IndexOutOfBoundsException - 인덱스가 범위 외의 경우일 때
    	NullPointerException - 지정된 컬렉션이 null인 경우
```



### **`removeRange`**

```java
protected void removeRange(int fromIndex, int toIndex)
    // 이 리스트의 fromIndex 부터 toIndex 직전까지의 인덱스를 가지는 모든 요소를 삭제합니다. 후속의 요소는 왼쪽으로 이동합니다. fromIndex와 toIndex의 값이 같은 경우, 실행되지 않습니다.
	Overrides
    	클래스 AbstractList <E> 내의 removeRange
    Parameters
    	fromIndex - 삭제하는 최초 요소의 인덱스
    	toIndex - 삭제하는 마지막 요소 직후의 인덱스
```





> 연관 내용

- List
- ArrayList와 Vector
- Fail-fast



> 출처

- https://docs.oracle.com/javase/8/docs/api/index.html
- http://cris.joongbu.ac.kr/course/java/api/java/util/ArrayList.html
- https://epicdevsold.tistory.com/32