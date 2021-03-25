> # Collection

### `Interface Collection<E>`



**`상위 인터페이스`**

- Iterable <E>

**`알려진 직계 서브 인터페이스`**

- BeanContext, BeanContextServices, BlockingQueue <E>, List <E>, Queue <E>, Set<E>, SortedSet <E>

**`알려진 구현 클래스 목록`**

- AbstractCollection, AbstractList, AbstractQueue, AbstractSequentialList, AbstractSet, ArrayBlockingQueue, ArrayList, AttributeList, BeanContextServicesSupport, BeanContextSupport, ConcurrentLinkdedQueue, CopyOnWriteArrayList, CopyOnWriteArraySet, DelayQueue, EnumSet, HashSet, JobStateReasons, LinkedBlockingQueue, LinkedHashSet, LinkedList, PriorityBlockingQueue, PriorityQueue, RoleList, RoleUnresolvedList, Stack, SynchronousQueue, TreeSet, Vector



`컬렉션 계층`의 루트 인터페이스입니다. 컬렉션은 요소라고 하는 개체의 그룹을 말합니다. 컬렉션에 따라서 요소의 중복을 허용하지만, 허용하지 않는 컬렉션도 있습니다. 또, 순서를 붙일 수 있는 컬렉션과 그렇지 않은 컬렉션이 있습니다. JDK는 이 인터페이스의 어떠한 직접적인 구현도 제공하지 않습니다. Set과 List와 같은 보다 구체적인 하위 인어페이스의 구현을 제공합니다. **이 인터페이스는 일반적으로 최대한의 보편성이 요구되는 곳에서 컬렉션을 건네주거나 그 컬렉션을 조작하기 위해서 사용됩니다.**

"Bag" 또는 "multiset"(중복 요소를 포함할 수 있는 정렬되지 않은 컬렉션)은 이 인터페이스를 직접 구현해야 합니다.

범용 Collection 구현 클래스(보통, 서브 인터페이스를 개입시켜 간접적으로 Collection을 구현한다.)는 2개의 표준 생성자를 제공하지 않으면 안됩니다. 비어있는 컬렉션을 작성하는 void(인수 없음) 생성자와 Collection 형의 인수를 1개 가져, 그 인수와 같은 요소로 새로운 컬렉션을 작성하는 생성자입니다. 실제로 후자의 생성자는 사용자가 원하는 구현 유형의 동등한 컬렉션을 생성하여 모든 컬렉션을 복제할 수 있도록 합니다. 인터페이스는 생성자를 포함할 수 없으므로 이 규칙을 적용할 수 있는 방법은 없지만, Java 플랫폼 라이브러리의 모든 범용 컬렉션의 구현은 이 규약에 준거하고 있습니다.

이 인터페이스에 포함된 "파괴적인" 메서드, 즉, 작동하는 컬렉션을 수정하는 메서드는 이 컬렉션이 작업을 지원하지 않는 경우 `UnsupportedOperationException`을 Throw 하도록 지정됩니다. 이때, 호출이 컬렉션에 영향을 미치지 않는 경우, 이러한 메서드는 `UnsupportedOperationException`를 Throw할 수 있습니만, 필수는 아닙니다. 예를 들어, 수정할 수 없는 컬렉션에서 addAll(Collection) 메서드를 호출하면 추가할 컬렉션이 비어있는 경우 예외를 발생시킬 수 있지만 필수는 아닙니다.

일부 컬렉션 구현에는 포함할 수 있는 요소에 제한이 있습니다. 예를 들어, null 요소를 금지하는 구현이나, null 요소의 형태에 제한이 있는 구현도 있습니다. 적합하지 않은 요소를 추가하려고 하면, 보통 NullPointerException 또는 ClassCastException과 같은 확인되지 않은 예외를 Throw합니다. 부적합한 요소가 있는지 쿼리하려고 하면 예외가 발생하거나 단순히 false를 리턴하는 경우도 있습니다. 일부 구현은 전자의 동작을 나타내고 일부는 후자의 동작을 나타냅니다. 많은 경우는 컬렉션에 삽입되지 않는 부적합한 요소를 처리하려고 하면, 구현 옵션에 따라 예외가 발생하거나 처리가 유효하게 됩니다. 이 인터페이스에 관한 그러한 예외는 선택 사항으로 표현됩니다.

이 인터페이스는 Java Collections Framework 멤버입니다.

Collections Framework 인터페이스 내 다수의 메서드는 equals 메서드로 정의됩니다. 예를 들어, contains(Object o) 메서드의 사양은 "이 컬렉션에 (o==null ? e==null : o.equals(e))와 같은 요소 e가 하나 이상 포함된 경우에만 true를 반환합니다."라는 것입니다. 이 사양은 Collection.contains를 null이 아닌 인수로 호출하면, 모든 요소에 대해 o.equals(e)가 호출된다는 의미로 해석되어서는 안됩니다. 구현은 두 요소의 해시 코드를 먼저 비교하여 같은 호출을 피하는 최적화를 자유롭게 구현할 수 있습니다.(Object.hashCode()의 사양은 해시 코드가 같지 않은 두 개체가 같을 수 없음을 보장합니다.) 보통, 다양한 Collections Framework 인터페이스의 구현은 구현자가 적절하다고 판단하는 경우 기본 개체 메서드의 지정된 동작을 자유롭게 활용할 수 있습니다.



> ## Collection의 Method



##### **`size`**

```java
int size()
    // 컬렉션의 요소 수를 리턴합니다. 이 컬렉션에 Integer.MAX_VALUE 보다 많은 요소가 있는 경우, Integer.MAX_VALUE를 리턴합니다.
    Returns
    	컬렉션의 요소 수
```



##### **`isEmpty`**

```java
boolean isEmpty()
    // 컬렉션에 요소가 없는 경우에 true를 리턴합니다.
    Returns
    	컬렉션에 요소가 없는 경우 true
```



##### **`contains`**

```java
boolean contains(Object o)
    // 컬렉션에 지정된 요소 o가 있는 경우 true를 리턴합니다. 즉, 이 컬렉션에 (o==null ? e==null : o.equals(e))인 요소 e가 1개 이상 있는 경우에만 true를 리턴합니다.
    Parameters
    	o - 컬렉션에 있는지를 조사할 요소
    Returns
    	컬렉션에 지정된 요소가 있는 경우 true
    Exceptions
    	ClassCastException - 지정한 요소의 형태가 이 컬렉션과 호환되지 않는 경우(선택 사항)
    	NullPointerException - 지정된 요소가 null이고 이 컬렉션에서 null 요소를 허용하지 않는 경우
    							(선택 사항)
```



##### **`iterator`**

```java
Iterator <E> iterator()
    // 컬렉션 요소의 반복자를 리턴합니다. 요소가 리턴되는 순서에 대한 보장은 없습니다. 다만, 이 컬렉션이 보장을 제공하는 클래스의 인스턴스인 경우는 예외입니다.
    Specified by
    	인터페이스 Iterable <E> 내의 iterator
    Returns
    	이 컬렉션 요소의 Iterator
```



##### **`toArray`**

```java
Object[] toArray()
    // 컬렉션의 모든 요소를 포함하는 배열을 리턴합니다. 반복자에 의해 리턴된 요소의 순서를 보장하는 컬렉션의 경우, 이 메서드는 같은 순서로 요소를 리턴하지 않으면 안됩니다.
    // 리턴된 배열은 이 컬렉션에서 해당 배열에 대한 참조가 유지되지 않으므로 안전합니다. 즉, 이 메서드는 컬렉션이 배열에 의해 지원되더라도 새로운 배열을 할당해야 합니다. 따라서 호출자는 리턴된 배열을 자유롭게 변경할 수 있습니다.
    // 이 메서드는 배열 베이스 API와 컬렉션 베이스 API 사이의 중개자로서의 역할을 합니다.
    Returns
    	컬렉션의 모든 요소를 포함하는 배열
    
<T> T[] toArray(T[] a)
    // 컬렉션의 모든 요소를 포함하는 배열을 리턴합니다. 리턴된 배열의 실행 시의 형태는 지정된 배열의 형태입니다. 컬렉션이 지정된 배열에 적합하면 그 안에 리턴됩니다. 그렇지 않으면, 지정된 배열의 실행 시의 유형과 이 컬렉션의 크기로 새 배열이 할당됩니다.
    // 이 컬렉션이 여유 공간이 있는 지정된 배열에 맞으면(즉, 배열에 이 컬렉션보다 많은 요소가 있으면), 컬렉션의 끝 바로 다음에 오는 배열의 요소들은 null로 설정됩니다.(호출자가 이 컬렉션에 null 요소가 포함되어 있지 않다는 것을 알고 있는 경우에만 이 컬렉션의 길이를 결정하는 데 유용합니다.)
    // 이 컬렉션이 반복자에 의해 리턴되는 요소의 순서를 보장하는 경우, 이 메서드는 동일한 순서로 요소를 리턴해야 합니다. 
    // toArray() 메서드와 마찬가지로 이 메서드는 배열 기반 API와 컬렉션 기반 API 사이의 중개자 역할을 합니다. 또한, 이 메서드를 사용하면 출력 배열의 실행 시의 형태(런타임 유형)을 정확하게 제어할 수 있기 때문에 특정 상황에서는 할당 비용을 절약하는 데 사용될 수 있습니다.
    // x가 문자열만 포함하는 것으로 알려진 컬렉션이라고 가정합니다. 다음 코드를 사용하여 컬렉션을 새로 할당된 String 배열로 덤프할 수 있습니다.
    // String[] y = x.toArray(new String[0]);
    // toArray(Object[0])은 toArray()와 기능적으로 동일합니다.
    Type Parameters
    	T - 컬렉션을 포함할 배열의 런타임 유형
    Parameters
    	a - 이 컬렉션의 요소가 충분히 큰 경우, 저장될 배열. 그렇지 않은 경우, 동일한 런타임 유형의 새 배열이 이 목적으로 할당됩니다.
    Returns
    	컬렉션의 요소를 포함한 배열
    Exceptions
    	ArrayStoreException - 지정된 배열의 런타임 유형이 이 컬렉션에 있는 모든 요소 런타임 유형의 상위 유형이 아닌 경우
    	NullPointerException - 지정된 배열이 null인 경우
```



##### **`add`**

```java
boolean add(E o)
    // 이 컬렉션에 지정된 요소가 포함되어 있는지 확인합니다(선택 작업). 호출의 결과로 이 컬렉션이 변경된 경우, true를 리턴합니다. 이 컬렉션이 중복을 허용하지 않고, 이미 지정된 요소를 포함하고 있는 경우, false를 리턴합니다.
    // 이 작업을 지원하는 컬렉션은 이 컬렉션이 추가할 수 있는 요소에 제한을 둘 수 있습니다. 특히, 컬렉션에 따라서는 null 요소 추가가 거부되는 경우나 추가할 수 있는 요소 유형에 제한을 두는 경우가 있습니다. 컬렉션 클래스는 추가할 수 있는 요소에 대한 제한 사항을 문서에 명시해야 합니다.
    // 컬렉션에 이미 요소가 포함되어 있는 것 이외의 이유로 특정 요소 추가를 거부하는 경우, false를 리턴하는 대신 예외를 Throw 해야 합니다. 이렇게 하면, 이 호출이 리턴된 후 컬렉션에 항상 지정된 요소가 포함된다는 불변성이 유지됩니다.
    Parameters
    	o - 컬렉션에 있을지를 조사하는 요소
    Returns
    	이 호출의 결과, 이 컬렉션이 변경되었을 경우, true
    Exceptions
    	UnsupportedOperationException - 이 컬렉션이 add를 지원하지 않는 경우
    	ClassCastException - 지정된 요소의 클래스가 이 컬렉션에 추가되는 것을 방지하는 경우
    	NullPointerException - 지정된 요소가 null 이고, 이 컬렉션이 null 요소를 허용하지 않는 경우
    	IllegalArgumentException - 요소의 일부 특성 탓에 이 컬렉션에 추가할 수 없는 경우
    	IllegalStateException - 삽입 제한으로 인해 현재 요소를 추가할 수 없는 경우
```



##### **`remove`**

```java
boolean remove(Object o)
    // 지정된 요소의 단일 인스턴스가 있는 경우, 이 컬렉션에서 제거합니다(선택 작업). 좀 더 공식적으로, 이 컬렉션에 하나 이상의 요소가 포함되어 있는 경우, (o==null ? e==null : o.equals(e))인 요소 e를 삭제합니다. 이 컬렉션에 지정된 요소가 포함된 경우 true를 리턴합니다(또는, 호출의 결과로 이 컬렉션이 변경된 경우).
    Parameters
    	o - 컬렉션으로부터 삭제될 요소(그 요소가 있는 경우)
    Returns
    	이 호출의 결과, 이 컬렉션이 변경되었을 경우, true
    Exceptions
    	ClassCastException - 지정된 요소의 형태가 이 컬렉션과 호환이 아닌 경우(선택 사항)
    	NullPointerException - 지정된 요소가 null 이고, 이 컬렉션이 null 요소를 허용하지 않는 경우								(선택 사항)
    	UnsupportedOperationException - 이 컬렉션이 remove를 지원하지 않는 경우
```



##### **`containsAll`**

```java
boolean containsAll(Collection <? > c)
    // 이 컬렉션 내에 지정된 컬렉션의 모든 요소가 있는 경우, true를 리턴합니다.
    Parameters
    	c - 이 컬렉션에 있을지를 조사할 컬렉션
    Returns
    	지정된 컬렉션의 모든 요소가 이 컬렉션 내에 있는 경우, true
    Exceptions
    	ClassCastException - 지정된 컬렉션의 하나 이상의 요소 유형이 이 컬렉션과 호환이 아닌 경우
    						(선택 사항)
    	NullPointerException - 지정된 컬렉션이 하나 이상의 null 요소를 포함하고, 이 컬렉션이 null
    						요소를 허용하지 않는 경우(선택 사항) 또는 지정된 컬렉션이 null인 경우
    References
    	contains(Object)
```



##### **`addAll`**

```java
boolean addAll(Collection <? extends E> c)
    // 지정된 컬렉션의 모든 요소를 이 컬렉션에 추가합니다(선택 작업). 작업이 진행되는 동안 지정된 컬렉션이 변경되었을 경우, 이 작업의 동작은 정의되지 않습니다. 이것은 지정된 컬렉션이 이 컬렉션 자신이며, 이 컬렉션이 비어있지 않은 경우, 이 호출의 동작은 정의되지 않음을 의미합니다.
    Parameters
    	c - 컬렉션에 삽입될 요소
    Returns
    	이 호출의 결과, 이 컬렉션이 변경되었을 경우, true
    Exceptions
    	UnsupportedOperationException - 이 컬렉션이 addAll 메서드를 지원하지 않는 경우
    	ClassCastException - 지정된 요소의 클래스가 이 컬렉션에 추가되는 것을 방지하는 경우
    	NullPointerException - 지정된 컬렉션이 null 요소를 포함하고, 이 컬렉션이 null 요소를 
    						허용하지 않는 경우 또는 지정된 컬렉션이 null인 경우
    	IllegalArgumentException - 지정된 컬렉션 요소의 일부 특성 탓에 이 컬렉션에 추가할 수 
    							없는 경우
    	IllegalStateException - 삽입 제한으로 인해 현재 모든 요소를 추가할 수 없는 경우
    References
    	add(Object)
```



##### **`removeAll`**

```java
boolean removeAll(Collection <? > c)
    // 지정된 컬렉션에도 포함되어 있는 이 컬렉션의 모든 요소를 삭제합니다(선택 작업). 이 호출의 결과, 이 컬렉션에는 지정된 컬렉션과 공통의 요소는 사라집니다.
    Parameters
    	c - 컬렉션에 삭제될 요소
    Returns
    	이 호출의 결과, 이 컬렉션이 변경되었을 경우, true
    Exceptions
    	UnsupportedOperationException - 이 컬렉션이 removeAll 메서드를 지원하지 않는 경우
    	ClassCastException - 지정된 컬렉션의 하나 이상의 요소 유형이 이 컬렉션과 호환이 아닌 경우
    						(선택 사항)
    	NullPointerException - 지정된 컬렉션이 null 요소를 포함하고, 이 컬렉션이 null 요소를 
    						허용하지 않는 경우 또는 지정된 컬렉션이 null인 경우
    References
    	remove(Object), contains(Object)
```



##### **`retainAll`**

```java
boolean retainAll(Collection <? > c)
    // 지정된 컬렉션에 포함된 이 컬렉션의 요소만 유지합니다(선택 작업). 즉, 지정된 컬렉션에 포함되지 않은 모든 요소를 이 컬렉션에서 제거합니다.
    Parameters
    	c - 이 컬렉션에서 유지할 요소를 포함하는 컬렉션
    Returns
    	이 호출의 결과, 이 컬렉션이 변경되었을 경우, true
    Exceptions
    	UnsupportedOperationException - 이 컬렉션이 retainAll 메서드를 지원하지 않는 경우
    	ClassCastException - 지정된 컬렉션의 하나 이상의 요소 유형이 이 컬렉션과 호환이 아닌 경우
    						(선택 사항)
    	NullPointerException - 지정된 컬렉션이 null 요소를 포함하고, 이 컬렉션이 null 요소를 
    						허용하지 않는 경우 또는 지정된 컬렉션이 null인 경우
    References
    	remove(Object), contains(Object)
```



##### **`clear`**

```java
void clear()
    // 컬렉션으로부터 모든 요소를 삭제합니다(선택 작업). 이 호출의 결과, 예외를 Throw 하지 않는 한, 컬렉션은 비웁니다.
    Exceptions
    	UnsupportedOperationException - 이 컬렉션이 clear 메서드를 지원하지 않는 경우
```



##### **`equals`**

```java
boolean equals(Object o)
    // 지정된 객체와 이 컬렉션이 동일한지를 비교합니다.
    // Collection 인터페이스는 Object.equals에 대한 범용 규정을 추가하지는 않지만, Collection 인터페이스를 직접 구현하는 프로그래머(즉, Collection이지만 Set 또는 List가 아닌 클래스를 생성)는 Object.equals를 오버라이드하기로 선택한 경우에 주의를 기울여야 합니다. Object.equals를 오버라이드할 필요가 없는 경우, 가장 단순한 방법은 Object의 구현에 의존하는 것이지만, 구현자는 디폴트로 '참조 비교' 대신에 '값 비교'를 구현할 수 있습니다.(List 및 Set 인터페이스는 이러한 '값 비교'를 요구합니다.)
    // Object.equals 메서드의 일반 규약에 의하면, equals는 대칭이어야 합니다(즉, b.equals(a)인 경우에만 a.equals(b)). List.equals 및 Set.equals의 규약에 따르면, List는 다른 List와만 동일하고 Set은 다른 Set과만 동일합니다.따라서 List와 Set 인터페이스를 구현하지 않는 컬렉션 클래스에 대한 사용자 정의 equals 메서드는 이 컬렉션이 List 또는 Set과 비교할 때, false를 리턴해야 합니다. 같은 논리로 Set 및 List 인터페이스를 모두 올바르게 구현하는 클래스를 작성할 수 없습니다.
    Overrides
    	클래스 Object 내의 equals
    Parameters
    	o - 이 컬렉션과 동일한지를 비교할 Object
    Returns
    	지정된 객체가 이 컬렉션과 동일한 경우, true
    References
    	Object.equals(Object), Set.equals(Object), List.equals(Object)
```



##### **`hashCode`**

```java
int hashCode()
    // 컬렉션의 해시 코드 값을 리턴합니다. Collection 인터페이스는 Object.hashCode 메서드에 대한 일반 규정을 추가하지 않지만, 프로그래머는 Object.equals 메서드를 오버라이드하는 모든 클래스가 Object에 대한 일반 규정을 충족하기 위해 Object.hashCode 메서드도 오버라이드해야 한다는 점에 유의해야 합니다. 특히, c1.equals(c2)는 c1.hashCode()==c2.hashCode()를 의미합니다.
    Overrides
    	클래스 Object 내의 hashCode
    Returns
    	이 컬렉션의 해시 코드 값
    References
    	Object.hashCode(), Object.equals(Object)
```





> 출처

- https://docs.oracle.com/javase/8/docs/api/index.html
- http://cris.joongbu.ac.kr/course/java/api/java/util/Collection.html

