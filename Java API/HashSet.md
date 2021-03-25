> # HashSet

### `Class HashSet<E>`



**`구현된 인터페이스`**

- Serializable, Cloneable, Iterable <E>, Collection <E>, Set <E>

**`알려진 서브 클래스`**

- JobStateReasons, LinkedHashSet



이 클래스는 해시 테이블(실제로는 HashMap 인스턴스)을 기본으로 하여 Set 인터페이스를 구현합니다. 이 클래스에서는 Set의 반복 순서를 보장하지 않습니다. 특히, 어느 기간에 걸쳐 일정한 순서를 유지하는 것을 보장하지 않습니다. 이 클래스는 null 요소를 허용합니다.

이 클래스는 해시 함수가 버킷 간의 요소를 적절하게 분산한다고 가정하여 기본 작업(add, remove, contains 및 size)에 대해 일정한 시간 성능을 제공합니다. 이 Set을 반복하려면 HashSet 인스턴스의 "사이즈(요소 수)"와 백업 HashMap 인스턴스의 "용량(버킷 수)"의 합계에 비례하는 시간이 필요합니다. 따라서 반복 성능이 중요한 경우, 초기 용량을 너무 높게(또는 부하 계수를 너무 낮게) 설정하지 않는 것이 매우 중요합니다.

이 구현은 동기화되지 않습니다. 여러 스레드가 동시에 HashSet에 접근하고 스레드 중 하나 이상이 Set을 변경하는 경우, 외부적으로 동기화되어야 합니다. 이는 일반적으로 Set을 자연스럽게 캡슐화하는 일부 객체에서 동기화하여 수행됩니다. 그러한 객체가 없으면, `'Collections.synchronizedSet' `메서드를 사용하여 맵을 "Wrap" 해야 합니다. 이것은 Set에 대한 우발적인 비동기 접근을 방지하기 위해 작성 시 수행하는 것이 가장 좋습니다.

​				Set s = Collections.synchronizedSet(new HashSet(...));

이 클래스의 반복자 메서드에 의해 리턴되는 반복자는 'Fail-fast' 입니다. 만약 반복자가 생성된 후에 반복자 자체의 remove 메서드 이외의 방법으로 Set을 구조적으로 변경하면, 반복자는 `ConcurrentModificationException`을 Throw 합니다. 따라서 동시 변경을 하면, 반복자는 장래의 예측할 수 없는 시점에 있어 예측할 수 없는 동작이 발생하는 위험을 회피하기 위해서 즉시 예외를 Throw합니다.

보통, 비동기의 동시 변경이 있는 경우, 확실한 보증을 실시하는 것은 불가능해서 반복자의 'Fail-fast' 동작을 보장할 수 없습니다. 'Fail-fast' 반복자는 최선 노력 원칙에 기반해 `ConcurrentModificationException`을 Throw 합니다. 따라서, 정확성을 위해 이 예외에 의존하는 프로그램을 작성하는 것은 잘못된 것입니다. 반복자의 'Fail-fast' 동작은 버그를 감지하는 데에만 사용되어야 합니다.

이 클래스는 `Java Collections Framework` 멤버입니다.



**`도입된 버전`** : 1.2

**`관련 항목`**

- Collection, Set, TreeSet, Collections.synchronizedSet(Set), HashMap, 직렬화된 형식



> # HashSet의 생성자



##### **`HashSet`**

```java
public HashSet()
    // 새로운 빈 Set을 생성합니다. 백업 HashMap 인스턴스는 디폴트 초기 용량(16)과 디폴트 부하 계수(0.75)를 가집니다.
```



##### **`HashSet`**

```java
public HashSet(Collection <? extends E> c)
    // 지정된 컬렉션의 요소를 포함하는 새로운 Set을 생성합니다. 백업 HashMap은 디폴트 부하 계수(0.75)와 지정된 컬렉션의 요소를 포함하기에 충분한 초기 용량으로 생성됩니다.
    Parameters
    	c - 요소가 Set에 배치될 컬렉션
    Exceptions
    	NullPointerException - 지정된 컬렉션이 null인 경우
```



##### **`HashSet`**

```java
public HashSet(int initialCapacity, float loadFactor)
    // 새로운 빈 Set을 생성합니다. 백업 HashMap 인스턴스는 지정된 초기 용량 및 지정된 부하 계수를 가집니다.
    Parameters
    	initialCapacity - 백업 해시 맵의 초기 용량
    	loadFactor - 백업 해시 맵의 부하 계수
    Exceptions
    	IllegalArgumentException - 초기 용량이 0보다 작거나, 부하 계수가 양수가 아닌 경우
```



##### **`HashSet`**

```java
public HashSet(int initialCapacity)
    // 새로운 빈 Set을 생성합니다. 백업 HashMap 인스턴스는 지정된 초기 용량과 디폴트 부하 계수(0.75)를 가집니다.
    Parameters
    	initialCapacity - 해시 테이블의 초기 용량
    Exceptions
    	IllegalArgumentException - 초기 용량이 0보다 작은 경우
```





> # HashSet의 Method

##### **`iterator`**

```java
public Iterator <E> iterator()
    // 새로운 요소의 반복자를 리턴합니다. 요소는 특별한 순서없이 리턴됩니다.
    Specified by
    	인터페이스 Iterable <E> 내의 iterator
    	인터페이스 Collection <E> 내의 iterator
    	인터페이스 Set <E> 내의 iterator
    	클래스 AbstractCollection <E> 내의 iterator
    Returns
    	Set 요소의 Iterator
    References
    	ConcurrentModificationException
```



##### **`size`**

```java
public int size()
    // Set 내의 요소 수(그 cardinality)를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 size
    	인터페이스 Set <E> 내의 size
    	클래스 AbstractCollection <E> 내의 size
    Returns
    	Set 내의 요소 수(그 cardinality)
```



##### **`isEmpty`**

```java
public boolean isEmpty()
    // Set가 요소를 1개 이상 보관, 유지하고 있지 않은 경우, true를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 isEmpty
    	인터페이스 Set <E> 내의 isEmpty
    Overrides
    	클래스 AbstractCollection <E> 내의 isEmpty
    Returns
    	Set가 요소를 1개 이상 보관, 유지하고 있지 않은 경우, true
```



##### **`contains`**

```java
public boolean contains(Object o)
    // Set가 지정된 요소를 보관, 유지하고 있는 경우, true를 리턴합니다.
    Specified by
    	인터페이스 Collection <E> 내의 contains
    	인터페이스 Set <E> 내의 contains
    Overrides
    	클래스 AbstractCollection <E> 내의 contains
    Parameters
    	o - Set에 있을지를 조사할 요소
    Returns
    	Set가 지정된 요소를 보관, 유지하고 있는 경우, true
```



##### **`add`**

```java
public boolean add(E o)
    // 지정된 요소가 Set의 요소로서 존재하지 않는 경우, 그 요소를 Set에 추가합니다.
    Specified by
    	인터페이스 Collection <E> 내의 add
    	인터페이스 Set <E> 내의 add
    Overrides
    	클래스 AbstractCollection <E> 내의 add
    Parameters
    	o - Set에 추가될 요소
    Returns
    	Set가 지정된 요소를 보관, 유지하고 있지 않았던 경우, true
```



##### **`remove`**

```java
public boolean remove(Object o)
    // 지정된 요소가 있으면 Set로부터 삭제됩니다.
    Specified by
    	인터페이스 Collection <E> 내의 remove
    	인터페이스 Set <E> 내의 remove
    Overrides
    	클래스 AbstractCollection <E> 내의 remove
    Parameters
    	o - Set에 있으면 삭제될 객체
    Returns
    	지정된 요소가 Set 내에 있을 경우, true
```



##### **`clear`**

```java
public void clear()
    // 모든 요소를 Set로부터 삭제합니다.
    Specified by
    	인터페이스 Collection <E> 내의 clear
    	인터페이스 Set <E> 내의 clear
    Overrides
    	클래스 AbstractCollection <E> 내의 clear
```



##### **`clone`**

```java
public Object clone()
    // HashSet 인스턴스의 얕은 복사본을 리턴합니다. 요소 자체는 복제되지 않습니다.
    Overrides
    	클래스 Object 내의 clone
    Returns
    	이 Set의 얕은 복사본
    References
    	Cloneable
```







> 출처

- http://cris.joongbu.ac.kr/course/java/api/java/util/HashSet.html
- https://docs.oracle.com/javase/8/docs/api/index.html



