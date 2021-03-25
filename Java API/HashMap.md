> # HashMap

### `Class HashMap<K,V>`



**`구현된 인터페이스`**

- Serializable, Cloneable, Map<K,V>

**`알려진 서브 클래스`**

- LinkedHashMap, PrinterStateReasons



Map 인터페이스의 해시 테이블에 기반한 구현입니다. 이 구현은 Map과 관련된 선택적 오퍼레이션을 모두 제공하고, null 값과 null 키를 허용합니다. HashMap 클래스는 동기화되지 않고 null을 허용한다는 점을 제외하면 Hashtable과 거의 동일합니다. 이 클래스는 Map의 순서에 대해서는 보장하지 않습니다. 특히, 어느 기간에 걸쳐 일정한 순서를 유지하는 것을 보장하지 않습니다.

이 구현은 해시 함수가 복수의 버킷으로 요소를 적절히 분산시킨다고 가정하여 기본 작업(Get and Put)에 대해 일정한 시간 성능을 제공합니다. 컬렉션 뷰를 반복하려면 HashMap 인스턴스의 '용량(버킷 수)'와 그 ''사이즈''(키-값 매핑 수)에 비례하는 시간이 필요합니다. 따라서 반복 성능이 중요한 경우, 초기 용량을 너무 높게(또는 부하 계수를 너무 낮게) 설정하지 않는 것이 중요합니다.

HashMap의 인스턴스에는 성능에 영향을 미치는 두 개의 매개 변수가 있습니다. 초기 용량 및 부하 계수입니다. 용량은 해시 테이블의 버킷 수이고, 초기 용량은 단순히 해시 테이블이 생성된 시점의 용량입니다. 부하 계수는 해시 테이블이 어느 정도 가득 차게되면, 해시 테이블의 용량이 자동으로 증가될까의 기준입니다. 해시 테이블의 엔트리 수가 부하 계수와 현재 용량의 곱을 초과하면, 용량은 `rehash` 메서드를 호출하는 것으로 약 2배가 됩니다.

일반적으로 기본 부하 계수(.75)는 시간과 공간 코스트의 균형을 제공합니다.  값이 높을수록 공간 오버 헤드가 감소하지만 조회 비용이 증가합니다(참조 코스트가 증가해, get 및 put을 포함한 HashMap 클래스의 대부분 오퍼레이션이 영향을 받습니다.). 초기 용량을 설정할 때에는 rehash 오퍼레이션의 수를 최소화하기 위해 Map에서 예상되는 엔트리 수와 부하 계수를 고려해야 합니다. 초기 용량이 엔트리의 최대 수를 부하 계수로 나눈 값보다 큰 경우, rehash 오퍼레이션은 일어나지 않습니다.

HashMap 인스턴스에 많은 매핑이 포함되는 경우, 충분히 큰 용량으로 인스턴스를 생성하면 테이블을 확장하기 위해 자동 rehash 오퍼레이션을 수행하는 것보다 더 효율적으로 매핑을 저장할 수 있습니다. 동일한 hashCode()로 많은 키를 사용하는 것은 모든 해시 테이블의 성능을 저하시키는 확실한 방법입니다. 영향을 개선하기 위해 키가 Comparable인 경우, 이 클래스는 키 간의 순서 비교를 사용하여 연결을 끊을 수 있습니다.

이 구현은 동기화되지 않습니다. 여러 스레드가 동시에 해시 맵에 접근하고 스레드 중 하나 이상이 Map을 구조적으로 변경하는 경우, 외부적으로 동기화되어야 합니다(구조적 변경은 하나 이상의 매핑을 추가하거나 삭제하는 모든 작업입니다. 단순히 인스턴스에 이미 포함된 키와 관련된 값을 변경하는 것은 구조적 변경이 아닙니다.). 이는 일반적으로 Map을 자연스럽게 캡슐화하는 일부 객체에서 동기화하여 수행됩니다. 그러한 객체가 없으면, `'Collections.synchronizedMap' `메서드를 사용하여 맵을 "Wrap" 해야 합니다. 이것은 Map에 대한 우발적인 비동기 접근을 방지하기 위해 작성 시 수행하는 것이 가장 좋습니다.

​				Map m = Collections.synchronizedMap(new HashMap(...));

이 클래스의 모든 '컬렉션 뷰 메서드'에 의해 리턴되는 반복자는 'Fail-fast' 입니다. 만약 반복자가 생성된 후에 반복자 자체의 remove 메서드 또는 add 메서드 이외의 방법으로 Map을 구조적으로 변경하면, 반복자는 `ConcurrentModificationException`을 Throw 합니다. 따라서 동시 변경을 하면, 반복자는 장래의 예측할 수 없는 시점에 있어 예측할 수 없는 동작이 발생하는 위험을 회피하기 위해서 즉시 예외를 Throw합니다.

보통, 비동기의 동시 변경이 있는 경우, 확실한 보증을 실시하는 것은 불가능해서 반복자의 'Fail-fast' 동작을 보장할 수 없습니다. 'Fail-fast' 반복자는 최선 노력 원칙에 기반해 `ConcurrentModificationException`을 Throw 합니다. 따라서, 정확성을 위해 이 예외에 의존하는 프로그램을 작성하는 것은 잘못된 것입니다. 반복자의 'Fail-fast' 동작은 버그를 감지하는 데에만 사용되어야 합니다.

이 클래스는 `Java Collections Framework` 멤버입니다.



**`도입된 버전`** : 1.2

**`관련 항목`**

- Object.hashCode(), Collection, Map, TreeMap, Hashtable, 직렬화된 형식



> # HashMap의 생성자



##### **`HashMap`**

```java
public HashMap(int initialCapacity, float loatFactor)
    // 지정된 초기 용량과 부하 계수로 비어 있는 HashMap을 생성합니다.
    Parameters
    	initialCapacity - 초기 용량
    	loadFactor - 부하 계수
    Exceptions
    	IllegalArgumentException - 초기 용량이 음수이거나, 부하 계수가 양수가 아닌 경우
```



##### **`HashMap`**

```java
public HashMap(int initialCapacity)
    // 지정된 초기 용량과 디폴트의 부하 계수(0.75)로 비어 있는 HashMap을 생성합니다.
    Parameters
    	initialCapacity - 초기 용량
    Exceptions
    	IllegalArgumentException - 초기 용량이 음수인 경우
```



##### **`HashMap`**

```java
public HashMap()
    // 디폴트 초기 용량(16)과 디폴트의 부하 계수(0.75)로 비어 있는 HashMap을 생성합니다.
```



##### **`HashMap`**

```java
public HashMap(Map <? extends K, ? extends V> m)
    // 지정된 Map과 같은 매핑으로 새로운 HashMap을 생성합니다. 디폴트의 부하 계수(0.75) 및 지정된 Map 매핑을 보관, 유지하는 데 충분한 초기 용량으로 HashMap이 생성됩니다.
    Parameters
    	m - 매핑이 이 Map으로 배치될 Map
    Exceptions
    	NullPointerException - 지정된 Map이 null인 경우
```





> # HashMap의 Method



##### **`size`**

```java
public int size()
    // Map 내 키와 값 매핑의 수를 리턴합니다.
    Specified by
    	인터페이스 Map <K,V> 내의 size
    Overrides
    	클래스 AbstractMap <K,V> 내의 size
    Returns
    	Map 내 키와 값 매핑의 수
```



##### **`isEmpty`**

```java
public boolean isEmpty()
    // 이 Map에 키와 값의 매핑이 없는 경우, true를 리턴합니다.
    Specified by
    	인터페이스 Map <K,V> 내의 isEmpty
    Overrides
    	클래스 AbstractMap <K,V> 내의 isEmpty
    Returns
    	Map에 키와 값의 매핑이 없는 경우, true
```



##### **`get`**

```java
public V get(Object key)
    // 지정된 키가 매핑되는 값을 리턴하거나, 이 Map에 키에 대한 매핑이 포함되지 않는 경우 null을 리턴합니다. 즉, 이 맵에 키 k에서 값 v로의 매핑이 포함되어 있는 경우(key==null ? k==null : key.equals(k)), 이 메서드는 v를 리턴합니다. 그렇지 않으면 null을 리턴합니다.(이러한 매핑은 최대 하나만 있을 수 있습니다.)
    // 리턴 값이 null이라고 해서 반드시 Map에 키에 대한 매핑이 포함되어 있지 않음을 나타내는 것은 아닙니다. Map이 명시적으로 키를 null로 매핑할 수도 있습니다. containsKey() 메서드를 사용하여 이 두 경우를 구분할 수 있습니다.
    Specified by
    	인터페이스 Map <K,V> 내의 get
    Overrides
    	클래스 AbstractMap <K,V> 내의 get
    Parameters
    	key - Map에서 매핑될 값을 검색할 키
    Returns
    	Map에서 지정된 키에 매핑되고 있는 값. 이 키에 대한 매핑이 없는 경우 null
    References
    	put(Object,Object)
```



##### **`containsKey`**

```java
public boolean containsKey(Object key)
    // Map이 지정된 키의 매핑을 보관, 유지하고 있는 경우, true를 리턴합니다.
    Specified by
    	인터페이스 Map <K,V> 내의 containsKey
    Overrides
    	클래스 AbstractMap <K,V> 내의 containsKey
    Parameters
    	key - Map에 있을지를 판단할 키
    Returns
    	Map이 지정된 키의 매핑을 보관, 유지하는 경우, true
```



##### **`put`**

```java
public V put(K key, V value)
    // 지정된 키와 지정된 값을 매핑하여 이 매핑을 Map에 추가합니다. Map이 이전에 이 키의 매핑을 보관, 유지하고 있었을 경우, 새로운 매핑으로 대체됩니다.
    Specified by
    	인터페이스 Map <K,V> 내의 put
    Overrides
    	클래스 AbsractMap <K,V> 내의 put
    Parameters
    	key - 지정된 값을 연결할 키
    	value - 지정된 키와 연결할 값
    Returns
    	키에 매핑되어 있던 이전 값. 키에 대한 매핑이 없었던 경우 null. (null 리턴은 Map이 이전에
		null과 키를 연결했음을 나타낼 수도 있습니다.)
```



##### **`putAll`**

```java
public void putAll(Map <? extends K, ? extends V> m)
    // 지정된 Map으로부터 모든 매핑을 Map에 복제합니다. 이러한 매핑은 현재 지정된 Map에 있는 모든 키에 대해 이 Map이 가진 모든 매핑을 대체합니다.
    Specified by
    	인터페이스 Map <K,V> 내의 putAll
    Overrides
    	클래스 AbstractMap <K,V> 내의 putAll
    Parameters
    	m - 복제할 Map
    Exceptions
    	NullPointerException - 지정된 Map이 null인 경우
```



##### **`remove`**

```java
public V remove(Object key)
    // 지정된 키에 대한 매핑이 있으면, 그 키의 매핑을 Map으로부터 삭제합니다.
    Specified by
    	인터페이스 Map <K,V> 내의 remove
    Overrides
    	클래스 AbstractMap <K,V> 내의 remove
    Parameters
    	key - Map으로부터 삭제될 키
    Returns
    	지정된 키에 매핑되어 있던 값. 또는 키의 매핑이 없었던 경우는 null. 리턴값 null은 Map이 이전에
    	null과 지정된 키를 매핑하고 있던 것을 나타내는 경우도 있습니다.
```



##### **`clear`**

```java
public void clear()
    // 모든 매핑을 Map으로부터 삭제합니다.
    Specified by
    	인터페이스 Map <K,V> 내의 clear
    Overrides
    	클래스 AbstractMap <K,V> 내의 clear
```



##### **`containsValue`**

```java
public boolean containsValue(Object value)
    // Map이 1개 이상의 키와 지정된 값을 매핑하고 있는 경우, true를 리턴합니다.
    Specified by
    	인터페이스 Map <K,V> 내의 containsValue
    Overrides
    	클래스 AbstractMap <K,V> 내의 containsValue
    Parameters
    	value - Map에 있을지를 판단할 값
    Returns
    	Map이 1개 이상의 키와 지정된 값을 매핑하고 있는 경우, true
```



##### **`clone`**

```java
public Object clone()
    // HashMap 인스턴스의 얕은 복사본을 리턴합니다. 키와 값 그 자체는 복제되지 않습니다.
    Overrides
    	클래스 AbstractMap <K,V> 내의 clone
    Returns
    	이 Map 인스턴스의 얕은 복사본
    References
    	Cloneable
```



##### **`keySet`**

```java
public Set <K> keySet()
    // 이 Map에 포함된 키의 Set 뷰를 리턴합니다. Set은 Map에 의해 지원되므로 Map의 변경 사항은 Set에 반영되며, 그 반대의 경우도 마찬가지입니다. Set에 대한 반복이 진행되는 동안 Map이 변경되면(반복자 자체 제거 작업을 통한 경우는 제외), 반복 결과가 정의되지 않습니다. 이 Set은 Iterator.remove, Set.remove, removeAll, perserveAll 및 clear 작업을 통해 Map에서 해당 매핑을 제거하는 요소 제거를 지원합니다. 하지만, add 또는 addAll 작업은 지원하지 않습니다.
    Specified by
    	인터페이스 Map <K,V> 내의 keySet
    Overrides
    	클래스 AbstractMap <K,V> 내의 keySet
    Returns
    	Map에 포함되어 있는 키의 Set 뷰
```



##### **`values`**

```java
public Collection <V> values()
    // 이 Map에 포함된 값의 컬렉션 뷰를 리턴합니다. 컬렉션은 Map에 의해 지원되므로 Map의 변경 사항은 컬렉션에 반영되며, 그 반대의 경우도 마찬가지입니다. 컬렉션에 대한 반복이 진행되는 동안 Map이 변경되면(반복자 자체 제거 작업을 통한 경우는 제외), 반복 결과가 정의되지 않습니다. 이 컬렉션은 Iterator.remove, Collection.remove, removeAll, preserveAll 및 clear 작업을 통해 Map에서 해당 매핑을 제거하는 요소 제거를 지원합니다. 하지만, add 또는 addAll 작업은 지원하지 않습니다.
    Specified by
    	인터페이스 Map <K,V> 내의 values
    Overrides
    	클래스 AbstractMap <K,V> 내의 values
    Returns
    	Map에 포함되어 있는 값의 컬렉션 뷰
```



##### **`entrySet`**

```java
public Set <Map.Entry <K,V>> entrySet()
    // 이 Map에 포함된 매핑의 Set 뷰를 리턴합니다. Set은 Map에 의해 지원되므로 Map의 변경 사항은 Set에 반영되며, 그 반대의 경우도 마찬가지입니다. Set에 대한 반복이 진행되는 동안 Map이 변경되면(반복자 자체 제거 작업을 통한 경우나 반복자에 의해 리턴되는 Map 항목의 setValue 작업을 통한 경우는 제외), 반복 결과가 정의되지 않습니다. 이 Set은 Iterator.remove, Set.remove, removeAll, preserveAll 및 clear 작업을 통해 Map에서 해당 매핑을 제거하는 요소 제거를 지원합니다. 하지만, add 또는 addAll 작업은 지원하지 않습니다.
    Specified by
    	인터페이스 Map <K,V> 내의 entrySet
    	클래스 AbstractMap <K,V> 내의 entrySet
    Returns
    	Map에 포함되어 있는 매핑의 Set 뷰
```





> 출처

- http://cris.joongbu.ac.kr/course/java/api/java/util/HashMap.html
- https://docs.oracle.com/javase/8/docs/api/index.html