> # LinkedList

### `Class LinkedList<E>`



**`형태 Parameter`**

- E - 컬렉션 내에 존재하는 요소의 형태

**`구현된 구현 인터페이스`**

- Serializable, Cloneable, Iterable <E>, Collection <E>, List <E>, Queue <E>



List 및 Deque 인터페이스의 양방향 LinkedList 구현입니다. 리스트의 임의의 오퍼레이션을 모두 구현하고 모든 요소(null 포함)를 허용합니다. List 인터페이스를 구현하는 것 외에 LinkedList 클래스는 리스트의 시작점 및 끝점에 있는 요소를 검색 및 삭제하거나 시작점 및 끝점에 요소를 삽입하는 메서드(get, remove, insert)를 제공합니다. 이러한 오퍼레이션을 사용하면 LinkedList를 스택, 큐, 또는 양방향 큐(Deque)로써 사용할 수 있게 됩니다.

이 클래스는 offer, poll 등에 의해 선입선출법(FIFO)을 제공하는 Queue 인터페이스를 구현합니다. 다른 스택 및 Deque 오퍼레이션은 리스트의 표준 오퍼레이션에 의해 간단하게 다시 작성할 수 있습니다. 이러한 오퍼레이션은 대응하는 List 오퍼레이션보다 다소 빠른 경우도 있지만, 주로 편의상의 이유로 포함되어 있습니다.

모든 오퍼레이션은 양방향 LinkedList에서 예상되는 대로 동작합니다. 리스트를 인덱스로 처리하는 오퍼레이션은 리스트의 시작점 또는 끝점 중 더 가까운 곳에서부터 리스트를 순회합니다.

이 구현은 동기화되지 않습니다. 여러 스레드가 동시에 LinkedList에 접근하고, 스레드 중 하나 이상이 리스트를 구조적으로 변경하는 경우 외부에서 동기화되어야 합니다(구조적 변경은 하나 이상의 요소를 추가하거나 삭제하는 작업입니다. 단순히 요소의 값을 설정하는 것은 구조적 변경이 아닙니다.). 이것은 일반적으로 리스트를 자연스럽게 캡슐화하는 일부 객체에서 동기화하여 수행됩니다. 그러한 객체가 없으면 `Collections.synchronizedList` 메서드를 사용하여 리스트를 "Wrap" 해야 합니다. 이것은 리스트에 대한 우발적인 비동기 접근을 방지하기 위해 작성 시 수행하는 것이 가장 좋습니다. 

​				List list = Collections.synchronizedList(new LinkedList(...));

이 클래스의 iterator 및 listIterator 메서드에 의해 리턴된 반복자는 `Fail-fast`입니다. 만약 반복자가 생성된 후에 반복자 자체의 remove 메서드 이외의 방법으로 리스트를 구조적으로 변경하면, 반복자는 `ConcurrentModificationException`을 Throw 합니다. 따라서 동시 변경을 하면, 반복자는 장래의 예측할 수 없는 시점에 있어 예측할 수 없는 동작이 발생하는 위험을 회피하기 위해서 즉시 예외를 Throw합니다.

보통, 비동기의 동시 변경이 있는 경우, 확실한 보증을 실시하는 것은 불가능해서 반복자의 'Fail-fast' 동작을 보장할 수 없습니다. 'Fail-fast' 반복자는 최선 노력 원칙에 기반해 `ConcurrentModificationException`을 Throw 합니다. 따라서, 정확성을 위해 이 예외에 의존하는 프로그램을 작성하는 것은 잘못된 것입니다. 반복자의 'Fail-fast' 동작은 버그를 감지하는 데에만 사용되어야 합니다.

이 클래스는 `Java Collections Framework` 멤버입니다.



**`도입된 버전`** : 1.2

**`관련 항목`**

- List, ArrayList, Vector, Collections.synchronizedList(List), 직렬화 된 형식



> # LinkedList의 생성자



##### **`LinkedList`**

```java
public LinkedList()
    // 비어 있는 리스트를 생성합니다.
```



##### **`LinkedList`**

```java
public LinkedList(Collection <? extends E> c)
    // 지정된 컬렉션의 요소가 포함되어 있는 리스트를, 요소가 컬렉션의 반복자에 의해 리턴된 순서대로 생성합니다.
    Parameters
    	c - 리스트에 저장될 요소가 담겨있는 컬렉션
    Exceptions
    	NullPointerException - 지정된 컬렉션이 null인 경우
```





> # LinkedList의 Method



##### **`getFirst`**

```java
public E getFirst()
    // 리스트 내의 최초의 요소를 리턴합니다.
    Returns
    	리스트 내의 최초의 요소
    Exceptions
    	NoSuchElementException - 리스트가 비어 있는 경우
```



##### **`getLast`**

```java
public E getLast()
    // 리스트 내의 마지막 요소를 리턴합니다.
    Returns
    	리스트 내의 마지막 요소
    Exceptions
    	NoSuchElementException - 리스트가 비어 있는 경우
```



##### **`removeFirst`**

```java
public E removeFirst()
    // 리스트 내의 최초의 요소를 삭제해 리턴합니다.
    Returns
    	리스트 내의 최초의 요소
    Exceptions
    	NoSuchElementException - 리스트가 비어 있는 경우
```



##### **`removeLast`**

```java
public E getLast()
    // 리스트 내의 마지막 요소를 삭제해 리턴합니다.
    Returns
    	리스트 내의 마지막 요소
    Exceptions
    	NoSuchElementException - 리스트가 비어 있는 경우
```



##### **`addFirst`**

```java
public void addFirst(E o)
    // 리스트의 시작 점에 지정된 요소를 삽입합니다.
    Parameters
    	o - 리스트의 시작 점에 삽입될 요소
```



##### **`addLast`**

```java
public void addLast(E o)
    // 리스트의 끝 점에 지정된 요소를 삽입합니다. add 메서드와 같은 기능이지만, 일관성을 위해서 제공되고 있습니다.
    Parameters
    	o - 리스트의 끝 점에 삽입될 요소
```



##### **`contains`**

```java
public boolean contains(Object o)
    // 지정된 요소가 리스트에 포함되어 있는 경우, true를 리턴합니다. 즉, 리스트에 (o==null ? e==null : o.equals(e))가 되는 요소 e가 1개 이상 포함되어 있는 경우에만 true를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 contains
    	인터페이스 List <E> 내의 contains
    Overrides
    	클래스 AbstractCollection <E> 내의 contains
    Parameters
    	o - 리스트에 있을지를 조사할 요소
    Returns
    	리스트가 지정된 요소를 포함하고 있는 경우, true
```



##### **`size`**

```java
public int size()
    // 리스트에 있는 요소의 수를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 size
    	인터페이스 List <E> 내의 size
    	클래스 AbstractCollection <E> 내의 size
    Returns
    	리스트 내의 요소 수
```



##### **`add`**

```java
public boolean add(E o)
    // 리스트의 끝 점에 지정된 요소를 삽입합니다.
    Specified by
    	인터페이스 Collection <E> 내의 add
    	인터페이스 List <E> 내의 add
    Overrides
    	클래스 AbstractCollection <E> 내의 add
    Parameters
    	o - 리스트에 삽입될 요소
    Returns
    	true (Collection.add 일반 규약에 따릅니다.)
```



##### **`remove`**

```java
public boolean remove(Object o)
    // 리스트 내에서 최초로 검출된 지정 요소를 삭제합니다. 그 요소가 리스트에 없는 경우, 리스트의 변경은 없습니다. 즉, (o==null ? get(i)==null : o.equals(get(i)))가 되는 최소의 인덱스 i를 가지는 요소를 삭제합니다.(그러한 요소가 존재하는 경우)
    Specified by
    	인터페이스 Collection <E> 내의 remove
    	인터페이스 List <E> 내의 remove
    Overrides
    	클래스 AbstractCollection <E> 내의 remove
    Parameters
    	o - 리스트로부터 삭제될 요소(그 요소가 있는 경우)
    Returns
    	리스트에 지정된 요소가 포함되어 있는 경우, true
```



##### **`addAll`**

```java
public boolean addAll(Collection <? extends E> c)
    // 지정된 컬렉션 내의 모든 요소를 지정된 컬렉션의 반복자에 의해 리턴된 순서로 리스트의 마지막에 삽입합니다. 작업이 진행되는 동안 지정된 컬렉션이 변경되면 이 작업의 동작은 정의되지 않습니다.(지정된 컬렉션이 이 리스트 자신이고, 리스트가 비어있지 않은 경우 이 호출의 동작은 보장되지 않습니다.)
    Specified by
    	인터페이스 Collection <E> 내의 addAll
    	인터페이스 List <E> 내의 addAll
    Overrides
    	클래스 AbstractCollection <E> 내의 addAll
    Parameters
    	c - 리스트에 삽입할 요소(컬렉션)
    Returns
    	이 호출의 결과, 이 리스트가 변경되었을 경우, true
    Exceptions
    	NullPointerException - 지정된 컬렉션이 null인 경우
    References
    	AbstractCollection.add(Object)
    
public boolean addAll(int index, Collection <? extends E> c)
    // 지정된 컬렉션 내의 모든 요소를 리스트의 지정된 위치부터 삽입합니다. 현재 그 위치에 있는 요소와 후속의 요소는 오른쪽으로 이동됩니다(인덱스 값이 증가). 새로운 요소는 지정된 컬렉션의 반복자에 의해 리턴된 순서로 리스트에 삽입됩니다.
    Specified by
    	인터페이스 List <E> 내의 addAll
    Overrides
    	클래스 AbstractSequentialList 내의 addAll
    Parameters
    	index - 지정된 컬렉션으로부터 최초의 요소를 삽입하는 위치의 인덱스
    	c - 리스트에 삽입할 요소(컬렉션)
    Returns
    	이 호출의 결과, 이 리스트가 변경되었을 경우, true
    Exceptions
    	IndexOutOfBoundsException - 지정된 인덱스가 범위 외일 경우(index<0 || index>size())
    	NullPointerException - 지정된 컬렉션이 null인 경우
```



##### **`clear`**

```java
public void clear()
    // 리스트로부터 모든 요소를 삭제합니다.
    Specified by
    	인터페이스 Collection <E> 내의 clear
    	인터페이스 List <E> 내의 clear
    Overrides
    	클래스 AbstractList <E> 내의 clear
```



##### **`get`**

```java
public E get(int index)
    // 리스트 내에 지정된 위치에 있는 요소를 리턴합니다.
    Specified by
    	인터페이스 List <E> 내의 get
    Overrides
    	클래스 AbstractSequentialList <E> 내의 get
    Parameters
    	index - 리턴될 요소의 인덱스
    Returns
    	리스트 내에 지정된 위치에 있는 요소
    Exceptions
    	IndexOutOfBoundsException - 지정된 인덱스가 범위 외일 경우(index<0 || index>size())
```



##### **`set`**

```java
public E set(int index, E element)
    // 리스트의 지정된 위치에 있는 요소를 지정된 요소로 대체합니다.
    Specified by
    	인터페이스 List <E> 내의 set
    Overrides
    	클래스 AbstractSequentialList <E> 내의 set
    Parameters
    	index - 대체될 요소의 인덱스
    	element - 지정된 위치에 대체될 요소
    Returns
    	지정된 위치에 이전에 있던 요소
    Exceptions
    	IndexOutOfBoundsException - 지정된 인덱스가 범위 외일 경우(index<0 || index>size())
```



##### **`add`**

```java
public void add(int index, E element)
    // 리스트의 지정된 위치에 지정된 요소를 삽입합니다. 현재 그 위치에 있는 요소와 후속의 요소는 오른쪽으로 이동됩니다(인덱스 값이 증가).
    Specified by
    	인터페이스 List <E> 내의 add
    Overrides
    	클래스 AbstractSequentialList <E> 내의 add
    Parameters
    	index - 지정된 요소가 삽입될 인덱스
    	element - 삽입될 요소
    Exceptions
    	IndexOutOfBoundsException - 지정된 인덱스가 범위 외일 경우(index<0 || index>size())
```



##### **`remove`**

```java
public E remove(int index)
    // 리스트의 지정된 위치에 있는 요소를 삭제합니다. 후속의 요소는 왼쪽으로 이동됩니다(인덱스 값이 감소). 리스트로부터 삭제된 요소가 리턴됩니다.
    Specified by
    	인터페이스 List <E> 내의 remove
    Overrides
    	클래스 AbstractSequentialList <E> 내의 remove
    Parameters
    	index - 삭제될 요소의 인덱스
    Returns
    	지정된 위치에 이전에 있던 요소
    Exceptions
    	IndexOutOfBoundsException - 지정된 인덱스가 범위 외일 경우(index<0 || index>size())
```



##### **`indexOf`**

```java
public int indexOf(Object o)
    // 리스트 내에서 지정된 요소가 최초로 검출된 위치의 인덱스를 리턴합니다. 리스트에 이 요소가 없는 경우, -1을 리턴합니다. 즉, (o==null ? get(i)==null : o.equals(get(i)))가 되는 최소의 인덱스 i를 리턴합니다. 그러한 인덱스가 없는 경우, -1을 리턴합니다.
    Specified by
    	인터페이스 List <E> 내의 indexOf
    Overrides
    	클래스 AbstractList <E> 내의 indexOf
    Parameters
    	o - 검색할 요소
    Returns
    	리스트 내에서 지정된 요소가 최초로 검출된 위치의 인덱스. 리스트에 이 요소가 없는 경우, -1
```



##### **`lastIndexOf`**

```java
public int lastIndexOf(Object o)
    // 리스트 내에서 지정된 요소가 마지막에 검출된 위치의 인덱스를 리턴합니다. 리스트에 이 요소가 없는 경우, -1을 리턴합니다. 즉, (o==null ? get(i)==null : o.equals(get(i)))가 되는 최대의 인덱스 i를 리턴합니다. 그러한 인덱스가 없는 경우, -1을 리턴합니다.
    Specified by
    	인터페이스 List <E> 내의 lastIndexOf
    Overrides
    	클래스 AbstractList <E> 내의 lastIndexOf
    Parameters
    	o - 검색할 요소
    Returns
    	리스트 내에서 지정된 요소가 마지막에 검출된 위치의 인덱스. 리스트에 이 요소가 없는 경우, -1
```



##### **`peek`**

```java
public E peek()
    // 이 리스트의 최초의 요소를 검색하지만, 삭제하지는 않습니다.
    Specified by
    	인터페이스 Queue <E> 내의 peek
    Returns
    	큐의 최초의 요소. 큐가 비어있는 경우, null
    Since Version
    	1.5
```



##### **`element`**

```java
public E element()
    // 이 리스트의 최초의 요소를 검색하지만, 삭제는 하지 않습니다.
    Specified by
    	인터페이스 Queue <E> 내의 element
    Returns
    	큐의 최초의 요소.
    Exceptions
    	NoSuchElementException - 큐가 비어있는 경우
    Since Version
    	1.5
```



##### **`poll`**

```java
public E poll()
    // 이 리스트의 최초의 요소를 검색하고 삭제합니다.
    Specified by
    	인터페이스 Queue <E> 내의 poll
    Returns
    	큐의 최초의 요소. 큐가 비어있는 경우, null
    Since Version
    	1.5
```



##### **`remove`**

```java
public E remove()
    // 이 리스트의 최초의 요소를 검색하고 삭제합니다.
    Specified by
    	인터페이스 Queue <E> 내의 remove
    Returns
    	큐의 최초의 요소.
    Exceptions
    	NoSuchElementException - 큐가 비어있는 경우
    Since Version
    	1.5
```



##### **`offer`**

```java
public boolean offer(E o)
    // 지정된 요소를 이 리스트의 끝(마지막 요소)으로 삽입합니다.
    Specified by
    	인터페이스 Queue <E> 내의 offer
    Parameters
    	o - 삽입할 요소
    Returns
    	true(Queue.offer의 일반 규약에 따릅니다.)
    Since Version
    	1.5
```



##### **`listIterator`**

```java
public ListIterator <E> listIterator(int index)
    // 리스트 내의 지정된 위치에서 시작되는 리스트 내의 요소를 적절한 순서로 반복하는 리스트 반복자를 리턴합니다. List.listIterator(int)의 일반 규약에 따릅니다.
    // 리스트 반복자는 'Fail-fast'입니다. 반복자가 생성된 후 리스트가 리스트 반복자의 자체 remove 또는 add 메서드를 통하지 않고 어떤 방식으로든 구조적으로 변경되면, ConcurrentModificationException를 Throw합니다. 따라서 동시 변경을 하면, 반복자는 장래의 예측할 수 없는 시점에 있어 예측할 수 없는 동작이 발생하는 위험을 회피하기 위해서 즉시 예외를 Throw합니다.
    Specified by
    	인터페이스 List <E> 내의 listIterator
    	클래스 AbstractSequentialList <E> 내의 listIterator
    Parameters
    	index - next() 호출에 의해 리스트 반복자로부터 리턴될 첫 번째 요소의 인덱스
    Returns
    	리스트 내의 지정된 위치로부터 시작되는 리스트 내 요소의 리스트 반복자(적절한 순서로)
    Exceptions
    	IndexOutOfBoundsException - 지정된 인덱스가 범위 외일 경우(index<0 || index>size())
    References
    	List.listIterator(int)
```



##### **`clone`**

```java
public Object clone()
    // 지정된 LinkedList의 얕은 복사본을 리턴합니다. 요소 자신은 복제되지 않습니다.
    Overrides
    	클래스 Object 내의 clone
    Returns
    	이 LinkedList 인스턴스의 얕은 복사본
    References
    	Cloneable
```



##### **`toArray`**

```java
public Object[] toArray()
    // 리스트 내의 모든 요소가 올바른 순서로 포함되고 있는 배열을 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 toArray
    	인터페이스 List <E> 내의 toArray
    Overrides
    	클래스 AbstractCollection <E> 내의 toArray
    Returns
    	리스트 내의 모든 요소가 올바른 순서로 포함되고 있는 배열
    References
    	Arrays.asList(Object[])
    
public <T> T[] toArray(T[] a)
    // 리스트 내의 모든 요소가 올바른 순서로 포함되고 있는 배열을 리턴합니다. 리턴된 배열의 런타임 유형은 지정된 배열의 련타임 유형입니다. 지정된 배열에 리스트가 들어가 있는 경우는 그 배열이 리턴됩니다. 그 외의 경우는 지정된 배열의 런타임 유형과 리스트의 사이즈를 이용해 새로운 배열을 할당합니다.
    // 배열에 리스트보다 많은 요소가 있는 경우, 컬렉션의 끝에 있는 배열의 요소는 null로 설정됩니다.(이는 리스트에 null 요소가 포함되어 있지 않음을 호출자가 알고 있는 경우에만 리스트의 길이를 결정하는 데 유용합니다.)
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





> 출처

- https://docs.oracle.com/javase/8/docs/api/index.html
- http://cris.joongbu.ac.kr/course/java/api/java/util/LinkedList.html

