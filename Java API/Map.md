> # Map

### `Interface Map<K,V>`



**`알려진 서브 인터페이스`**

- ConcurrentMap <K,V>, SortedMap <K, V>

**`알려진 구현 클래스`**

- AbstractMap, Attributes, AuthProvider, ConcurrentHashMap, EnumMap, HashMap, Hashtable, IdentityHashMap, LinkedHashMap, PrinterStateReasons, Properties, Provider, RenderingHints, TabularDataSupport, TreeMap, UIDefaults, WeakHashMap



`public interface Map<K,V>`

키를 값에 매핑하는 객체입니다. Map은 중복 키를 포함할 수 없으며 각 키는 최대 하나의 값에 매핑할 수 있습니다.

이 인터페이스는 인터페이스라기 보다는 완전한 추상 클래스였던 `Dictionary` 클래스를 대신합니다.

Map 인터페이스는 Map의 내용을 키 집합 / 값 집합 / 키-값 매핑 집합의 3가지 방법으로 표시할 수 있습니다. Map의 순서는 Map 컬렉션 뷰의 반복자가 요소를 반환하는 순서로 정의됩니다. TreeMap 클래스 등 일부 Map의 구현에서는 순서에 대해 보증합니다. 하지만, HashMap 클래스 등의 구현에서는 순서에 대해 보증하지 않습니다.

**참고** : 변경 가능한 객체가 Map의 키로 사용되는 경우에는 세심한 주의가 필요합니다. 객체가 Map 내의 키일 때, equals() 비교에 영향을 주는 방식으로 객체의 값이 변경되었을 경우에는 맵의 동작이 보증되지 않습니다. 이 금지 사항의 특별한 경우는 Map은 자신을 키로 지정하는 것이 불가능하다는 것입니다. Map이 자신을 값으로 지정하는 것은 허용되지만, 극도의 주의가 필요합니다. 이러한 Map의 경우, equals 및 hashCode 메소드의 결과는 보증되지 않습니다.

모든 범용 Map의 구현 클래스는 다음 2개의 표준 생성자를 제공해야합니다. 하나는 void(인수 없음) 생성자와 Map 형태의 인수 1개를 취하는 생성자입니다. 전자는 비어있는 Map을 생성하고, 후자는 같은 키와 값의 매핑을 인수로서 가지는 새로운 Map을 생성합니다. 그 결과, 사용자는 후자의 생성자를 사용해 임의의 Map을 복제함으로써 필요한 클래스와 등가인 Map을 생성할 수 있습니다. 이것은 강제적인 것은 아니지만(인터페이스는 생성자를 가질 수 없기 때문에), JDK에서의 모든 범용 Map의 구현은 이를 따르고 있습니다.

이 Map이 오퍼레이션을 지원하지 않는 경우, 이 인터페이스에 포함된 파괴적인(destructive) 메소드, 즉, 처리되는 Map을 변경하는 메소드는 UnsupportedOperationException을 Throw 하도록 지정됩니다. 이 때, 호출이 Map에 영향을 미치지 않으면 이러한 메소드는 UnsupportedOperationException을 Throw 할 수 있지만, 필수는 아닙니다. 예를 들어, 변경 불가능한 Map에서 putAll(Map) 메소드를 호출하면, 매핑이 중첩되는 Map이 비어있는 경우에 예외가 발생할 수 있지만 필수는 아닙니다.

일부 Map의 구현에는 포함할 수 있는 키와 값에 대한 제한이 있습니다. 예를 들어, 일부 구현에서는 null 키 및 값을 제한하거나 또다른 구현에서는 키 Type에 대한 제한이 있을 수 있습니다. 부적합한 키 또는 값을 삽입하려고 시도하면 일반적으로 NullPointerException 또는 ClassCastException과 같은 `Unchecked Exception`이 발생합니다. 부적합한 키나 값이 존재하는지를 조회하려고 하면 예외를 Throw하거나 단순히 false를 리턴하는 경우도 있습니다. 일부 구현은 전자의 동작을 나타내고 일부는 후자를 나타냅니다. 많은 경우에 부적합한 요소가 삽입되지 않는 Map에 부적합한 키나 값을 포함하려고 시도하면 구현 옵션에 따라 예외가 발생하거나 혹은 처리가 유효하게 되는 경우가 있습니다. 이러한 예외는 이 인터페이스에 관한 '선택 사항'으로서 표시됩니다.

이 인터페이스는 Java Collections Framework 멤버입니다.

Collections Framework 인터페이스의 많은 메소드는 equals 메소드와 관련되어 정의됩니다. 예를 들어, containsKey(Object key) 메소드에 대한 기본 내용은 다음과 같습니다. 

> 이 Map에 키 k에 대한 매핑이 포함되어 있는 경우에만 true를 리턴합니다. 
>
> key == null ? k == null : key.equals(k)

이 설명은 `null이 아닌 key로 Map.containsKey를 호출하면, 모든 키 k에 대해 key.equals(k)가 호출된다`고 해석되어서는 안됩니다. 예를 들어, 두 key의 해시 코드를 먼저 비교하여 equals 호출을 피하는 방식으로 최적화하여 구현할 수 있습니다(Object.hashCode() 메소드는 해시 코드가 같지 않은 두 객체가 같을 수 없음을 보증합니다.). 일반적으로 다양한 Collection Framework 인터페이스의 구현은 구현자가 적절하다고 판단하는 경우, 기본 객체 메소드의 지정된 동작을 자유롭게 활용할 수 있습니다.



**`도입된 버전`** : 1.2

**`관련 항목`**

- HashMap, TreeMap, Hashtable, SortedMap, Collection, Set





> # Map의 Method



##### **`size`**

```java
int size()
    // Map 내의 키-값 매핑의 수를 리턴합니다. Map에 Integer.MAX_VALUE 보다 많은 요소가 있는 경우는 Integer.MAX_VALUE를 리턴합니다.
    Returns
    	Map 내의 키-값 매핑의 수
```



##### **`isEmpty`**

```java
boolean isEmpty()
    // Map에 키-값 매핑이 보관 유지되어 있지 않을 경우에 true를 리턴합니다.
    Returns
    	Map에 키-값 매핑이 보관 유지되어 있지 않을 경우 true
```



##### **`containsKey`**

```java
boolean containsKey(Object key)
    // 지정된 키의 매핑이 Map에 포함되어 있는 경우에 true를 리턴합니다. 즉, Map에 (key==null ? k==null : key.equals(k))을 만족하는 키 k의 매핑이 포함되어 있는 경우에만 true를 리턴합니다. Map은 이러한 매핑을 1개만 포함합니다.
    Parameters
    	key - Map에 있는지 판단할 키
    Returns
    	Map이 지정된 키의 매핑을 보관하고 있는 경우 true
    Exceptions
    	ClassCastException - 키가 Map에 적합하지 않는 형태인 경우
    	NullPointerException - 키가 null이고 Map이 null 키를 허용하지 않는 경우
```



##### **`containsValue`**

```java
boolean containsValue(Object value)
    // 지정된 값의 매핑이 Map에 1개 이상 포함되어 있는 경우 true를 리턴합니다. 즉, Map에 (value==null ? v==null : value.equals(v))을 만족하는 값 v의 매핑이 1개 이상인 경우에만 true를 리턴합니다. Map 인터페이스 대부분의 구현에서 이 오퍼레이션에 걸리는 시간은 Map의 크기에 정비례합니다.
    Parameters
    	value - Map에 있는지 판단할 값
    Returns
    	Map이 지정된 값의 매핑을 1개 이상 보관하고 있는 경우 true
    Exceptions
    	ClassCastException - 값이 Map에 적합하지 않는 형태인 경우
    	NullPointerException - 값이 null이고 Map이 null 값을 허용하지 않는 경우
```



##### **`get`**

```java
V get(Object key)
    // Map 내 지정된 키에 매핑되어 있는 값을 리턴합니다. Map이 이 키의 매핑을 포함하고 있지 않은 경우 null을 리턴합니다. 하지만, 리턴값 null이 Map이 키의 매핑을 포함하지 않는 것을 나타낸다고 할 수는 없습니다. Map이 명시적으로 null 값을 매핑하는 경우도 있기 때문입니다. containsKey() 메소드를 사용하면 이러한 2개의 경우를 분별할 수 있습니다.
    // Map에 (key==null ? k==null : key.equals(k))의 조건으로부터 키 k에 값 v가 매핑되는 경우, 이 메소드는 v를 리턴합니다. 포함되지 않는 경우 null을 리턴합니다. 이러한 매핑은 1개만 존재합니다.
    Parameters
    	key - 관련된 값을 찾을 키
    Returns
    	Map 내 지정된 키에 매핑되어 있는 값. 이 키에 대한 매핑이 없는 경우 null
    Exceptions
    	ClassCastException - 키가 Map에 적합하지 않는 형태인 경우
    	NullPointerException - 키가 null이고 Map이 null 키를 허용하지 않는 경우
    References
    	containsKey(Object)
```



##### **`put`**

```java
V put(K key, V value)
    // 지정된 키와 지정된 값의 매핑을 이 Map에 저장합니다. Map에 이미 이 키에 대한 매핑이 있는 경우, 이전 매핑은 지정된 매핑으로 대체됩니다. Map.containsKey(k)가 true를 리턴하는 경우, Map은 키 k의 매핑을 포함한다고 할 수 있습니다.
    Parameters
    	key - Map에 저장할 매핑의 키
    	value - Map에 저장할 매핑의 값
    Returns
    	지정된 키에 관련된 이전 매핑의 값. 키에 매핑이 없었던 경우는 null. 또한, null 반환값은 Map이 null 값을 허용하고 있는 경우는 이전 키에 null 값이 매핑되어 있었다는 것을 나타낼 수도 있습니다.
    Exceptions
    	UnsupportedOperationException - Map이 put 메소드를 지원하고 있지 않은 경우
    	ClassCastException - 키 혹은 값이 Map에 적합하지 않는 형태인 경우
    	IllegalArgumentException - 지정된 키나 값의 특성 상, 이 Map에 삽입할 수 없는 경우
    	NullPointerException - 키 혹은 값이 null이고 Map이 null 키나 값을 허용하지 않는 경우
```



##### **`remove`**

```java
V remove(Object key)
    // 이 키에 매핑이 있는 경우, 그 매핑을 Map으로부터 삭제합니다. 즉, (key==null ? k==null : key.equals(k))를 만족하는 k의 매핑이 Map에 포함되어 있을 경우, 이 매핑은 삭제됩니다. Map은 이러한 매핑을 1개만 포함합니다.
    Parameters
    	key - Map에서 삭제할 매핑의 키
    Returns
    	지정된 키와 매핑되어 있던 이전의 값. 키의 매핑이 없을 경우 null
    Exceptions
    	ClassCastException - 키가 Map에 적합하지 않는 형태인 경우
    	NullPointerException - 키가 null이고 Map이 null 키를 허용하지 않는 경우
    	UnsupportedOperationException - Map이 remove 메소드를 지원하고 있지 않은 경우
```



##### **`putAll`**

```java
void putAll(Map <? extends K, ? extends V> t)
    // 지정된 Map의 모든 매핑을 이 Map에 복제합니다. 이 호출의 효과는 지정된 맵의 모든 매핑(k, v)에 관해서 이 Map으로 put(k, v)를 호출한 것과 같습니다. 지정된 Map이 이 오퍼레이션의 처리 중에 변경되었을 경우, 그 오퍼레이션의 동작은 정의되지 않습니다.
    Parameters
    	t - Map에 삽입할 매핑들이 들어있는 Map
    Exceptions
    	UnsupportedOperationException - Map이 put 메소드를 지원하고 있지 않은 경우
    	ClassCastException - 지정된 Map의 키 혹은 값이 Map에 적합하지 않는 형태인 경우
    	IllegalArgumentException - 지정된 키나 값의 특성 상, 이 Map에 삽입할 수 없는 경우
    	NullPointerException - 지정된 Map이 null인 경우. 또는 키 혹은 값이 null이고 Map이 null 키나 값을 허용하지 않는 경우
```



##### **`clear`**

```java
void clear()
    // Map으로부터 매핑을 모두 삭제합니다.
    Exceptions
    	UnsupportedOperationException - Map이 clear 메소드를 지원하고 있지 않은 경우
```



##### **`keySet`**

```java
Set <K> keySet()
    // Map에 포함되어 있는 키의 Set 뷰를 리턴합니다. Set은 Map과 연동되어 있으므로 Map이 변경되면 Set에 반영되고, Set이 변경되면 Map에 반영됩니다. Set에 대한 반복 처리가 진행되는 동안 MAp이 변경되면(반복자 자체 remove 오퍼레이션 제외), 반복 결과가 보장되지 않습니다. Set는 요소의 삭제를 지원하고 있어, 대응하는 매핑을 Map에서 삭제할 수 있습니다. Set은 Iterator.remove, Set.remove, removeAll, retainAll 및 clear 오퍼레이션을 통해 Map에서 해당 매핑을 삭제하는 요소 삭제를 지원합니다. 그러나 add 또는 addAll 오퍼레이션은 지원하지 않습니다.
    Returns
    	Map에 포함되어 있는 키의 Set 뷰
```



##### **`values`**

```java
Collection <V> values()
    // Map에 포함되어 있는 값의 컬렉션 뷰를 리턴합니다. 컬렉션은 Map과 연동되어 있으므로 Map이 변경되면 컬렉션에 반영되고, Collection이 변경되면 Map에 반영됩니다. 컬렉션에 대한 반복 처리가 진행되는 동안 Map이 변경되면(반복자 자체 remove 오퍼레이션 제외), 반복 결과가 보장되지 않습니다. 컬렉션은 요소의 삭제를 지원하고 있어, 대응하는 매핑을 Map에서 삭제할 수 있습니다. 컬렉션은 Iterator.remove, Set.remove, removeAll, retainAll 및 clear 오퍼레이션을 통해 Map에서 해당 매핑을 삭제하는 요소 삭제를 지원합니다. 그러나 add 또는 addAll 오퍼레이션은 지원하지 않습니다.
    Returns
    	Map에 포함되어 있는 값의 컬렉션 뷰
```



##### **`entrySet`**

```java
Set <Map.Entry <K, V>> entrySet()
    // Map에 포함되어 있는 매핑의 Set 뷰를 리턴합니다. 리턴된 Set 내의 각 요소는 Map.Entry입니다. Set은 Map과 연동되어 있으므로 Map이 변경되면 Set에 반영되고, Set이 변경되면 Map에 반영됩니다. Set에 대한 반복 처리가 진행되는 동안 MAp이 변경되면(반복자 자체 remove 오퍼레이션, 반복자에 의해 리턴된 Map.Entry에 대한 SetValue 오퍼레이션 제외), 반복 결과가 보장되지 않습니다. Set는 요소의 삭제를 지원하고 있어, 대응하는 매핑을 Map에서 삭제할 수 있습니다. Set은 Iterator.remove, Set.remove, removeAll, retainAll 및 clear 오퍼레이션을 통해 Map에서 해당 매핑을 삭제하는 요소 삭제를 지원합니다. 그러나 add 또는 addAll 오퍼레이션은 지원하지 않습니다.
    Returns
    	Map에 포함되어 있는 매핑의 Set 뷰
```



##### **`equals`**

```java
boolean equals(Object o)
    // 지정된 객체가 이 Map과 동일한지를 비교합니다. 지정된 객체도 Map이고 2개의 Map이 같은 매핑을 포함하고 있는 경우 true를 리턴합니다. 즉, t1.entrySet().equals(t2.entrySet())인 경우, 2개의 Map t1과 t2는 같은 매핑을 나타냅니다. 이것에 의해 Map 인터페이스의 구현이 다른 경우에도 equals 메소드가 올바르게 동작하는 것이 보증됩니다.
    Overrides
    	클래스 Object 내의 equals
    Parameters
    	o - Map과 동일한지를 비교할 객체
    Returns
    	지정된 객체가 Map과 동일한 경우 true
    References
    	Object.hashCode(), Hashtable
```



##### **`hashCode`**

```java
int hashCode()
    // Map의 해시 코드 값을 리턴합니다. Map의 해시 코드는 Map의 entrySet뷰 내의 각 엔트리의 hashCode의 합이 되도록 정의됩니다. 이는 m1.equals(m2)가 Object.hashCode()의 일반 규약에서 요구하는대로 두 Map m1과 m2에 대해 (m1.hashCode()==m2.hashCode())를 의미함을 보장합니다.
    Overrides
    	클래스 Object 내의 hashCode
    Returns
    	Map의 해시 코드 값
    References
    	Map.Entry.hashCode(), Object.hashCode(), Object.equals(Object), equals(Object)
```





> 출처

- https://docs.oracle.com/javase/8/docs/api/index.html
- http://cris.joongbu.ac.kr/course/java/api/java/util/Map.html

