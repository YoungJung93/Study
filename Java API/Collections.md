> # Collections

### `Class Collections`

이 클래스는 컬렉션에서 작동하거나 리턴하는 static 메서드로만 구성됩니다. 여기에는 컬렉션에서 작동하는 다형성 알고리즘이 포함되어 있습니다.

이 클래스의 모든 메서드는 제공되는 컬렉션 또는 클래스 객체가 null인 경우, NullPointerException을 Throw 합니다. 

이 클래스에 있는 다형성 알고리즘의 문서에는 일반적으로 구현에 대한 간략한 설명이 포함되어 있습니다. 이러한 설명은 규격의 일부가 아닌, 구현 참고 사항으로 간주되어야 합니다. 구현자는 규격 자체를 준수하는 한 다른 알고리즘으로 자유롭게 대체하여 사용할 수 있습니다. 예를 들어, sort 가 사용하는 알고리즘이 꼭 합병정렬일 필요는 없지만 안정적이어야 합니다.

컬렉션이 set 메서드와 같이 적절한 변형 Primitive 메서드를 지원하지 않을 경우, 이 클래스에 포함된 파괴적 알고리즘 즉, 작동하는 컬렉션을 변경하는 알고리즘은 UnsupportedOperationException을 Throw 하도록 지정됩니다. 이러한 알고리즘은 호출이 컬렉션에 영향을 미치지 않는 경우 예외를 Throw 할 수 있지만, 반드시 필요한 것은 아닙니다. 예를 들어, 이미 정렬된 변경 불가능한 리스트에서 sort 메서드를 호출하면, UnsupportedOperationException이 발생할 수도, 발생하지 않을 수도 있습니다.



> # Collections의 Field



##### **`EMPTY_SET`**

```java
public static final Set EMPTY_SET
    // 비어있는 세트입니다(불변). 이 SET는 직렬화 가능합니다.
    References
    	emptySet()
```



##### **`EMPTY_LIST`**

```java
public static final Set EMPTY_SET
    // 비어있는 리스트입니다(불변). 이 LIST는 직렬화 가능합니다.
    References
    	emptyList()
```



##### **`EMPTY_MAP`**

```java
public static final Set EMPTY_SET
    // 비어있는 맵입니다(불변). 이 MAP는 직렬화 가능합니다.
    References
    	emptyMap()
```





> # Collections의 Method



##### **`sort`**

```java
public static <T extends Coparable <? super T>> void sort(List <T> list)
    // 요소의 자연 정렬에 따라, 지정된 리스트를 오름차순으로 정렬합니다. 리스트의 모든 요소는 Comparable 인터페이스를 구현해야 합니다. 게다가 리스트의 모든 요소는 서로 비교 가능해야 합니다. 즉, e1.compareTo(e2)는 리스트의 요소 e1와 e2에 대해 ClassCastException을 발생시키지 않아야 합니다.
    // 이 정렬은 안정성이 보장됩니다. 정렬 결과, 동일한 요소가 다시 정렬되지 않습니다.
    // 지정된 리스트는 변경 가능해야 하지만, 사이즈를 변경할 필요는 없습니다.
    // 정렬 알고리즘은 변경된 합병 정렬입니다. 이 알고리즘은 항상 n*log(n)의 시간복잡도를 제공합니다.
    Parameters
    	list - 정렬할 리스트
    Exceptions
    	ClassCastException - 리스트에 서로 비교할 수 없는 요소가 있는 경우(ex.문자열)
    	UnsupportedOperationException - 지정된 리스트의 리스트 반복자가 set 오퍼레이션을 지원하지
    									않는 경우
    References
    	Comparable
    
public static <T> void sort(List<T> list, Comparator <? super T> c)
    // 지정된 Comparator가 가리키는 순서에 따라 지정된 리스트를 정렬합니다. 게다가 리스트의 모든 요소는 서로 비교 가능해야 합니다. 즉, e1.compareTo(e2)는 리스트의 요소 e1와 e2에 대해 ClassCastException을 발생시키지 않아야 합니다.
    // 이 정렬은 안정성이 보장됩니다. 정렬 결과, 동일한 요소가 다시 정렬되지 않습니다.
    // 정렬 알고리즘은 변경된 합병 정렬입니다. 이 알고리즘은 항상 n*log(n)의 시간복잡도를 제공합니다.
    Parameters
    	list - 정렬할 리스트
    	c - 리스트의 정렬 순서를 결정하는 Comparator. null 값은 요소의 자연 정렬을 사용하는 것을 
    		나타낸다.
    Exceptions
    	ClassCastException - 리스트에 서로 비교할 수 없는 요소가 있는 경우(ex.문자열)
    	UnsupportedOperationException - 지정된 리스트의 리스트 반복자가 set 오퍼레이션을 지원하지
    									않는 경우
    References
    	Comparator
```



##### **`binarySearch`**

```java
public static <T> int binarySearch(List <? extends Comparable <? super T>> list, T key)
    // 이진 탐색 알고리즘을 사용해 지정된 리스트로부터 지정된 객체를 검색합니다. 리스트는 호출 전에 sort(List) 메서드를 사용해 요소의 자연 정렬에 따라 정렬될 필요가 있습니다. 정렬되어 있지 않은 경우, 결과는 정의되지 않습니다. 지정된 객체와 동일한 요소가 리스트에 다수 있는 경우, 어떤 것이 탐색될지 보장되지는 않습니다.
    // "Random Access" 리스트의 경우, 이 메서드는 log(n)의 시간복잡도를 갖습니다(위치를 지정한 액세스에 거의 일정한 시간이 필요). 지정된 리스트가 RandomAccess 인터페이스를 구현하지 않고 큰 리스트인 경우, 이 메서드는 O(n) 링크 순회 및 O(log n) 요소 비교를 실행하는 반복자 기반의 이진 탐색을 실시합니다.
    Parameters
    	list - 검색되는 리스트
    	key - 검색할 객체
    Returns
    	리스트에 key가 있는 경우, key의 인덱스. key가 리스트에 없는 경우는 (-(삽입 지점)-1). 삽입 지점이란 리스트로 key가 삽입되는 지점입니다. 즉, key 보다 큰 최초 요소의 인덱스이며 리스트의 모든 요소가 지정된 key 보다 작은 경우는 list.size() 입니다. 리스트에서 key가 발견되었을 경우 리턴 값이 0 이상이며, 그렇지 않을 경우 리턴 값은 음수가 됩니다.
    Exceptions
    	ClassCastException - 리스트에 서로 비교할 수 없는 요소가 있는 경우(ex.문자열) 또는 
    						key가 리스트의 요소와 서로 비교 불가능한 경우
    References
    	Comparable, sort(List)
    
public static <T> int binarySearch(List <? extends T> list, T key, 
                                   Comparator <? super T> c)
    // 이진 탐색 알고리즘을 사용해 지정된 리스트로부터 지정된 객체를 검색합니다. 리스트는 호출 전에 sort(List, Comparator) 메서드를 사용해, 지정된 컴퍼레이터에 따라 정렬될 필요가 있습니다. 리스트가 정렬되어 있지 않은 경우, 결과는 정의되지 않습니다. 지정된 객체와 동일한 요소가 리스트에 다수 있는 경우, 어떤 것이 탐색될지 보장되지는 않습니다.
    // "Random Access" 리스트의 경우, 이 메서드는 log(n)의 시간복잡도를 갖습니다(위치를 지정한 액세스에 거의 일정한 시간이 필요). 지정된 리스트가 RandomAccess 인터페이스를 구현하지 않고 큰 리스트인 경우, 이 메서드는 O(n) 링크 순회 및 O(log n) 요소 비교를 실행하는 반복자 기반의 이진 탐색을 실시합니다.
    Parameters
    	list - 검색되는 리스트
    	key - 검색할 객체
    	c - 리스트를 정렬하기 위한 Comparator. null 값은 요소의 자연 정렬을 사용하는 것을 나타냅니다.
    Returns
    	리스트에 key가 있는 경우, key의 인덱스. key가 리스트에 없는 경우는 (-(삽입 지점)-1). 삽입 지점이란 리스트로 key가 삽입되는 지점입니다. 즉, key 보다 큰 최초 요소의 인덱스이며 리스트의 모든 요소가 지정된 key 보다 작은 경우는 list.size() 입니다. 리스트에서 key가 발견되었을 경우 리턴 값이 0 이상이며, 그렇지 않을 경우 리턴 값은 음수가 됩니다.
    Exceptions
    	ClassCastException - 리스트에 서로 비교할 수 없는 요소가 있는 경우(ex.문자열) 또는 
    						key가 리스트의 요소와 서로 비교 불가능한 경우
    References
    	Comparable, sort(List)
```



##### **`reverse`**

```java
public static void reverse(List <? > list)
    // 지정된 리스트 내 요소의 순서를 반대로 합니다.
    // 이 메서드는 선형 시간에 실행됩니다.
    Parameters
    	list - 요소의 순서를 반대로 할 리스트
    Exceptions
    	UnsupportedOperationException - 지정된 리스트 또는 리스트 반복자가 set 메서드를 지원하지
    									않는 경우
```



##### **`shuffle`**

```java
public static void shuffle(List <? > list)
    // 기본 Random Number Generation(무작위 수 생성기)를 사용하여 지정된 리스트를 무작위로 순열합니다. 모든 순열은 거의 동일한 가능성으로 발생합니다.
    // 위의 설명에서 '거의'라는 말을 사용하는 것은, 기본 Random Number Generation(무작위 수 생성기)가 독립적으로 선택된 비트의 거의 편향되지 않은 소스이기 때문입니다. 만약, 그것이 무작위로 선택된 비트의 완벽한 소스라면, 알고리즘은 완벽한 균일성을 가진 순열을 선택할 것입니다.
    // 이 구현은 리스트의 마지막 요소에서 두 번째 요소까지 역방향으로 순회하며 무작위로 선택된 요소를 현재 위치로 반복적으로 교체합니다. 요소는 첫 번째 요소에서 현재 위치까지의 범위에서 무작위로 선택됩니다.
    // 이 메서드는 선형 시간에 실행됩니다. 지정된 리스트가 RamdomAccess 인터페이스를 구현하지 않고 큰 리스트인 경우, 이 구현은 지정된 리스트를 Shuffle 하기 전에 배열로 덤프하고 Shuffle된 배열을 다시 리스트로 덤프합니다. 이렇게 하면, 'Sequential Access' 리스트를 제자리에 섞어서 발생하는 2차 동작을 방지할 수 있습니다.
    Parameters
    	list - 순서를 바꾸는 작업을 할 리스트
    Exceptions
    	UnsupportedOperationException - 지정된 리스트 또는 리스트 반복자가 set 메서드를 지원하지
    									않는 경우
```



##### **`shuffle`**

```java
public static void shuffle(List <? > list, Random rnd)
    // 기본 Random Number Generation(무작위 수 생성기)를 사용하여 지정된 리스트를 무작위로 순열합니다. 모든 순열은 Random Number Generation(무작위 수 생성기)가 한결같다고 가정할 때, 동일한 가능성으로 발생합니다.
    // 이 구현은 리스트의 마지막 요소에서 두 번째 요소까지 역방향으로 순회하며 무작위로 선택된 요소를 현재 위치로 반복적으로 교체합니다. 요소는 첫 번째 요소에서 현재 위치까지의 범위에서 무작위로 선택됩니다.
    // 이 메서드는 선형 시간에 실행됩니다. 지정된 리스트가 RamdomAccess 인터페이스를 구현하지 않고 큰 리스트인 경우, 이 구현은 지정된 리스트를 Shuffle 하기 전에 배열로 덤프하고 Shuffle된 배열을 다시 리스트로 덤프합니다. 이렇게 하면, 'Sequential Access' 리스트를 제자리에 섞어서 발생하는 2차 동작을 방지할 수 있습니다.
    Parameters
    	list - 순서를 바꾸는 작업을 할 리스트
    	rnd - 리스트의 순서를 바꾸기 위해 사용할 Random Number Generation(무작위 수 생성기)
    Exceptions
    	UnsupportedOperationException - 지정된 리스트 또는 리스트 반복자가 set 메서드를 지원하지
    									않는 경우
```



##### **`swap`**

```java
public static void swap(List <? > list, int i, int j)
    // 지정된 리스트의 지정된 위치에 있는 요소를 스왑합니다. 지정된 위치가 같으면, 이 메서드의 호출 결과, 리스트가 변경되지 않습니다.
    Parameters
    	list - 요소를 스왑할 리스트
    	i - 스왑될 첫 번째 요소의 인덱스
    	j - 스왑될 두 번째 요소의 인덱스
    Exceptions
    	IndexOutOfBoundsException - i 또는 j, i와 j 모두가 리스트의 범위 외일 경우
    								(i<0 || i>=list.size() || j<0 || j>=list.size())
    Since Version
    	1.4
```



##### **`fill`**

```java
public static <T> void fill(List <? super T> list, T obj)
    // 지정된 리스트의 모든 요소를 지정된 요소로 바꿉니다.
    // 이 메서드는 선형 시간에 실행됩니다.
    Parameters
    	list - 지정된 요소가 삽입될 리스트
    	obj - 지정된 리스트에 삽입될 요소
    Exceptions
    	UnsupportedOperationException - 지정된 리스트 또는 리스트 반복자가 set 메서드를 지원하지
    									않는 경우
```



##### **`copy`**

```java
public static <T> void copy(List <? super T> dest, List <? extends T> src)
    // 한 리스트(src)로부터 다른 리스트(dest)에 모든 요소를 복제합니다. 작업 후 대상 리스트에 있는 복제된 요소의 인덱스는 원본 리스트의 해당 인덱스와 동일합니다. 대상 리스트의 길이는 적어도 원본 리스트보다 같거나 길어야 합니다. 카피처의 리스트가 더 긴 경우, 대상 리스트의 나머지 요소는 영향을 받지 않습니다.
    // 이 방법은 선형 시간에 실행됩니다.
    Parameters
    	dest - 카피처 리스트
    	src - 원본 리스트(카피원 리스트)
    Exceptions
    	IndexOutOfBoundsException - 카피처 리스트가 카피원 리스트 전체를 포함하기에 작을 경우
    	UnsupportedOperationException - 지정된 리스트 또는 리스트 반복자가 set 메서드를 지원하지
    									않는 경우
```



##### **`min`**

```java
public static <T extends Object & Comparable <? super T>> T min(Collection <? extends T> 
                                                                coll)
    // 요소의 자연 정렬에 따라 지정된 컬렉션의 최소 요소를 리턴합니다. 컬렉션의 모든 요소는 Comparable 인터페이스를 구현해야 합니다. 또한, 컬렉션의 모든 요소는 서로 비교할 수 있어야 합니다. 즉, e1.compareTo(e2)는 컬렉션의 요소 e1과 e2에 대해 ClassCastException을 발생시키지 않아야 합니다.
    // 이 메서드는 전체 컬렉션에 걸쳐 반복되므로 컬렉션 사이즈에 비례한 시간이 필요합니다.
    Parameters
    	coll - 최소의 요소를 검색할 컬렉션
    Returns
    	요소의 자연 정렬에 따라, 지정된 컬렉션의 최소의 요소
    Exceptions
    	ClassCastException - 컬렉션에 서로 비교 불가능한 요소(ex. 문자열)가 있는 경우
    	NoSuchElementException - 컬렉션이 비어있는 경우
    References
    	Comparable
    
public static <T> T min(Collection <? extends T> coll, Comparator <? super T> comp)
    // 지정된 Comparator가 가리키는 순서에 따라, 지정된 컬렉션의 최소 요소를 리턴합니다. 컬렉션의 모든 요소는 지정된 Comparator로 서로 비교할 수 있어야 합니다. 즉, comp.compare(e1,e2)는 컬렉션의 요소 e1과 e2에 대해 ClassCastException을 발생시키지 않아야 합니다.
    // 이 메서드는 전체 컬렉션에 걸쳐 반복되므로 컬렉션 사이즈에 비례한 시간이 필요합니다.
    Parameters
    	coll - 최소의 요소를 검색할 컬렉션
    	comp - 최소의 요소를 결정하는 데 사용할 Comparator. null 값은 요소의 자연 정렬을 사용하는 
    			것을 나타냅니다.
    Returns
    	지정된 Comparator에 따라, 지정된 컬렉션의 최소의 요소
    Exceptions
    	ClassCastException - 컬렉션에 지정된 Comparator로 서로 비교 불가능한 요소가 있는 경우
    	NoSuchElementException - 컬렉션이 비어있는 경우
    References
    	Comparable
```



##### **`max`**

```java
public static <T extends Object & Comparable <? super T>> T max(Collection <? extends T>
                                                               coll)
    // 요소의 자연 정렬에 따라 지정된 컬렉션의 최대 요소를 리턴합니다. 컬렉션의 모든 요소는 Comparable 인터페이스를 구현해야 합니다. 또한, 컬렉션의 모든 요소는 서로 비교할 수 있어야 합니다. 즉, e1.compareTo(e2)는 컬렉션의 요소 e1과 e2에 대해 ClassCastException을 발생시키지 않아야 합니다.
    // 이 메서드는 전체 컬렉션에 걸쳐 반복되므로 컬렉션 사이즈에 비례한 시간이 필요합니다.
    Parameters
    	coll - 최대의 요소를 검색할 컬렉션
    Returns
    	요소의 자연 정렬에 따라, 지정된 컬렉션의 최대의 요소
    Exceptions
    	ClassCastException - 컬렉션에 서로 비교 불가능한 요소(ex. 문자열)가 있는 경우
    	NoSuchElementException - 컬렉션이 비어있는 경우
    References
    	Comparable
    
public static <T> T max(Collection <? extends T> coll, Comparator <? super T> comp)
    // 지정된 Comparator가 가리키는 순서에 따라, 지정된 컬렉션의 최대 요소를 리턴합니다. 컬렉션의 모든 요소는 지정된 Comparator로 서로 비교할 수 있어야 합니다. 즉, comp.compare(e1,e2)는 컬렉션의 요소 e1과 e2에 대해 ClassCastException을 발생시키지 않아야 합니다.
    // 이 메서드는 전체 컬렉션에 걸쳐 반복되므로 컬렉션 사이즈에 비례한 시간이 필요합니다.
    Parameters
    	coll - 최대의 요소를 검색할 컬렉션
    	comp - 최대의 요소를 결정하는 데 사용할 Comparator. null 값은 요소의 자연 정렬을 사용하는 
    			것을 나타냅니다.
    Returns
    	지정된 Comparator에 따라, 지정된 컬렉션의 최대의 요소
    Exceptions
    	ClassCastException - 컬렉션에 지정된 Comparator로 서로 비교 불가능한 요소가 있는 경우
    	NoSuchElementException - 컬렉션이 비어있는 경우
    References
    	Comparable
```



##### **`rotate`**

```java
public static void rotate(List <? > list, int distance)
    // 지정된 거리만큼 지정된 리스트의 요소를 회전합니다. 이 메서드를 호출하면 인덱스 i의 요소는 0과 list.size()-1 사이의 모든 값에 대해 인덱스 ((i-distance) mod list.size())의 요소가 됩니다. (이 방법은 리스트 사이즈에 영향을 미치지 않습니다.) 예를 들어, 리스트가 [t,a,n,k,s]로 구성되어 있다고 가정했을 때, Collections.rotate(list, 1) 또는 Collections.rotate(list, -4)를 호출하면 리스트가 [s,t,a,n,k]로 변경됩니다.
    // 이 메서드는 나머지 요소의 순서를 유지하면서 리스트 내에서 하나 이상의 요소를 이동하는 서브 리스트에 유용하게 적용될 수 있습니다. 예를 들어, 다음의 관용구는 인덱스 j번째 요소부터 K+1번째 요소까지만 왼쪽으로 1만큼 회전시킵니다(k는 j보다 크거나 같아야 합니다.).
    			Collections.rotate(list.subList(j, k+1), -1);
    // 이를 구체적으로 설명하기 위해, [a,b,c,d,e]를 포함하는 리스트가 있다고 가정합니다. 인덱스 1(b)의 요소를 두 위치 앞으로 이동하려면 다음 호출을 수행합니다.
				Collections.rotate(list.subList(1, 4), -1);
	// 이 호출의 결과, 리스트는 [a,c,d,b,e]가 됩니다.
	// 둘 이상의 요소를 앞으로 이동시키려면 이동 거리의 절대값을 늘립니다. 요소를 뒤로 이동하려면 양의 이동 거리를 사용해야 합니다.
	// 지정된 리스트가 작거나 RandomAccess 인터페이스를 구현하고 있는 경우, 이 구현은 첫 번째 요소를 이동해야 하는 위치로 교체한 다음, 대체된 요소가 첫 번째 요소로 스왑될 때까지 대체된 요소를 이동해야 하는 위치로 반복적으로 교체합니다. 필요한 경우 회전이 완료될 때까지 두 번째 및 연속 요소에서 이 프로세스가 반복됩니다.
	// 지정된 리스트가 크거나 RandomAccess 인터페이스를 구현하지 않은 경우, 이 구현은 리스트를 (index-distance) mod size 인 2개의 서브 리스트로 분할합니다. 두 알고리즘에 대한 자세한 설명은 Jon Bentley의 Programming Pearls(Addison-Wesley, 1986)의 섹션 2.3을 참조하세요.
    Parameters
    	list - 회전시킬 리스트
        distance - 리스트를 회전시킬 거리값. 이 값에 제약은 없습니다. 값은 0, 음수 또는 
        			list.size() 보다 클 수도 있습니다.
    Exceptions
    	UnsupportedOperationException - 지정된 리스트 또는 리스트 반복자가 set 메서드를 지원하지
    									않는 경우
	Since Version
        1.4
```



##### **`replaceAll`**

```java
public static <T> boolean replaceAll(List <T> list, T oldVal, T newVal)
    // 리스트 내에 존재하는 지정된 값(oldVal)을 모두 다른 값(newVal)으로 대체합니다. 즉, 리스트 내에서 (oldVal==null ? e==null : oldVal.equals(e))가 되는 모든 요소 e를 새로운 값(newVal)로 교체합니다. 이 메서드는 리스트의 사이즈에 영향을 미치지 않습니다.
    Parameters
    	list - 값 대체가 생기는 리스트
    	oldVal - 대체 전의 값
    	newVal - 대체 후의 값
    Exceptions
    	UnsupportedOperationException - 지정된 리스트 또는 리스트 반복자가 set 메서드를 지원하지
    									않는 경우
    Since Version
    	1.4
```



##### **`indexOfSubList`**

```java
public static int indexOfSubList(List<? > source, List<? > target)
    // 지정된 소스 리스트 내에서 지정된 타겟 리스트가 최초로 출현한 개시 위치를 리턴하거나, 그러한 발생이 없는 경우 -1을 리턴합니다. 즉, source.subList(i, i+target.size()).equals(target) 가 되는 최소의 인덱스 i를 리턴하고, 이러한 인덱스 값이 없는 경우 -1을 리턴합니다.(target.size() > source.size())인 경우 -1을 리턴합니다.
    // 이 구현은 소스 리스트에서 스캔하는 "Brute force"기술을 사용하여 차례로 각 위치에서 대상과 일치하는 항목을 찾습니다.
    Parameters
    	source - 최초로 출현하는 target이 검색될 리스트
    	target - source의 subList로서 검색할 리스트
    Returns
    	지정된 소스 리스트 내에서 최초로 출현한 타겟 리스트의 위치. 이러한 출현이 없는 경우 -1
    Since Version
    	1.4
```



##### **`lastIndexOfSubList`**

```java
public static int lastIndexOfSubList(List<? > source, List<? > target)
    // 지정된 소스 리스트 내에서 마지막에 출현한 타겟 리스트의 개시 위치를 리턴하거나, 그러한 발생이 없는 경우 -1을 리턴합니다. 즉, source.subList(i, i+target.size()).equals(target) 가 되는 최소의 인덱스 i를 리턴하고, 이러한 인덱스 값이 없는 경우 -1을 리턴합니다.(target.size() > source.size())인 경우 -1을 리턴합니다.
    // 이 구현은 소스 리스트를 반복하는 "Brute force"기술을 사용하여 차례로 각 위치에서 대상과 일치하는 항목을 찾습니다.
    Parameters
    	source - 마지막에 출현하는 target이 검색될 리스트
    	target - source의 subList로서 검색할 리스트
    Returns
    	지정된 소스 리스트 내에서 마지막에 출현한 타겟 리스트의 개시 위치. 이러한 출현이 없는 경우 -1
    Since Version
    	1.4
```



##### **`unmodifiableCollection`**

```java
public static <T> Collection <T> unmodifiableCollection(Collection <? extends T> c)
    // 지정된 컬렉션의 변경 불가능한 View를 리턴합니다. 이 메서드를 사용하면 모듈이 사용자에게 내부 컬렉션에 대한 "read-only" 접근 권한을 제공할 수 있습니다. 리턴된 컬렉션에서의 쿼리 작업은 지정된 컬렉션을 직접 읽어들입니다. 직접 또는 반복자를 사용하는 것과 관계없이 리턴된 컬렉션을 변경하려고 하면 UnsupportedOperationException이 발생합니다.
    // 리턴된 컬렉션은 hashCode 및 equals 작업을 백업 컬렉션에 전달하지는 않지만, Object의 equals 및 hashCode 메서드에 의존합니다. 이는 백업 컬렉션이 Set 또는 List인 경우, 이러한 작업의 규약을 지키기 위해 필요합니다.
    // 리턴된 컬렉션은 지정된 컬렉션이 직렬화 가능할 경우 직렬화 가능합니다.
    Parameters
    	c - 변경 불가능한 뷰가 리턴되는 컬렉션
    Returns
    	지정된 컬렉션의 변경 불가능한 뷰
```



##### **`unmodifiableSet`**

```java
public static <T> Set <T> unmodifiableSet(Set <? extends T> s)
    // 지정된 Set의 변경 불가능한 View를 리턴합니다. 이 메서드를 사용하면 모듈이 사용자에게 내부 Set에 대한 "read-only" 접근 권한을 제공할 수 있습니다. 리턴된 Set에서의 쿼리 작업은 지정된 Set을 직접 읽어들입니다. 직접 또는 반복자를 사용하는 것과 관계없이 리턴된 Set을 변경하려고 하면 UnsupportedOperationException이 발생합니다.
    // 리턴된 Set은 지정된 Set이 직렬화 가능할 경우 직렬화 가능합니다.
    Parameters
    	s - 변경 불가능한 뷰가 리턴되는 Set
    Returns
    	지정된 Set의 변경 불가능한 뷰
```



##### **`unmodifiableSortedSet`**

```java
public static <T> SortedSet <T> unmodifiableSortedSet(SortedSet <T> s)
    // 지정된 SortedSet의 변경 불가능한 View를 리턴합니다. 이 메서드를 사용하면 모듈이 사용자에게 내부 SortedSet에 대한 "read-only" 접근 권한을 제공할 수 있습니다. 리턴된 SortedSet에서의 쿼리 작업은 지정된 SortedSet을 직접 읽어들입니다. 직접 또는 반복자를 사용하는 것 혹은 뷰의 subSet, headSet, tailSet을 사용하는 것과 관계없이 리턴된 SortedSet을 변경하려고 하면 UnsupportedOperationException이 발생합니다.
    // 리턴된 SortedSet은 지정된 SortedSet이 직렬화 가능할 경우 직렬화 가능합니다.
    Parameters
    	s - 변경 불가능한 뷰가 리턴되는 SortedSet
    Returns
    	지정된 SortedSet의 변경 불가능한 뷰
```



##### **`unmodifiableList`**

```java
public static <T> List <T> unmodifiableList(List <? extends T> list)
    // 지정된 리스트의 변경 불가능한 View를 리턴합니다. 이 메서드를 사용하면 모듈이 사용자에게 내부 리스트에 대한 "read-only" 접근 권한을 제공할 수 있습니다. 리턴된 리스트에서의 쿼리 작업은 지정된 리스트을 직접 읽어들입니다. 직접 또는 반복자를 사용하는 것과 관계없이 리턴된 리스트을 변경하려고 하면 UnsupportedOperationException이 발생합니다.
    // 리턴된 리스트는 지정된 리스트가 직렬화 가능할 경우 직렬화 가능합니다. 또, 지정된 리스트가 RandomAccess를 구현한 경우에만 리턴된 리스트가 RandomAccess를 구현합니다.
    Parameters
    	list - 변경 불가능한 뷰가 리턴되는 리스트
    Returns
    	지정된 리스트의 변경 불가능한 뷰
```



##### **`unmodifiableMap`**

```java
public static <K,V> Map <K,V> unmodifiableMap(Map <? extends K,? extends V> m)
    // 지정된 Map의 변경 불가능한 View를 리턴합니다. 이 메서드를 사용하면 모듈이 사용자에게 내부 Map에 대한 "read-only" 접근 권한을 제공할 수 있습니다. 리턴된 Map에서의 쿼리 작업은 지정된 Map을 직접 읽어들입니다. 직접 또는 반복자를 사용하는 것과 관계없이 리턴된 Map을 변경하려고 하면 UnsupportedOperationException이 발생합니다.
    // 리턴된 Map은 지정된 Map이 직렬화 가능할 경우 직렬화 가능합니다.
    Parameters
    	m - 변경 불가능한 뷰가 리턴되는 Map
    Returns
    	지정된 Map의 변경 불가능한 뷰
```



##### **`unmodifiableSortedMap`**

```java
public static <K,V> SortedMap <K,V> unmodifiableSortedMap(SortedMap <K,? extends V> m)
    // 지정된 SortedMap의 변경 불가능한 View를 리턴합니다. 이 메서드를 사용하면 모듈이 사용자에게 내부 SortedMap에 대한 "read-only" 접근 권한을 제공할 수 있습니다. 리턴된 SortedMap에서의 쿼리 작업은 지정된 SortedMap을 직접 읽어들입니다. 직접 또는 반복자를 사용하는 것 혹은 뷰의 subMap, headMap, tailMap을 사용하는 것과 관계없이 리턴된 SortedMap을 변경하려고 하면 UnsupportedOperationException이 발생합니다.
    // 리턴된 SortedMap은 지정된 SortedMap이 직렬화 가능할 경우 직렬화 가능합니다.
    Parameters
    	m - 변경 불가능한 뷰가 리턴되는 SortedMap
    Returns
    	지정된 SortedMap의 변경 불가능한 뷰
```



##### **`synchronizedCollection`**

```java
public static <T> Collection <T> synchronizedCollection(Collection <T> c)
    // 지정된 컬렉션을 기본으로 하는 동기화된(Thread Safe) 컬렉션을 리턴합니다. 직렬 액세스를 보장하기 위해, 백업 컬렉션에 대한 모든 액세스가 리턴된 컬렉션을 통해 수행되어야 합니다.
    // 리턴된 컬렉션의 반복 처리를 실시하는 경우, 사용자는 다음에 나타난 것과 같이 수동으로 동기화할 필요가 있습니다.
    	Collection c = Collections.synchronizedCollection(myCollection);
			...
		synchronized(c) {
        	Iterator i = c.iterator(); 	// Must be in the synchronized block
			while(i.hasNext())
                foo(i.next());
		}
	// 이것을 실시하지 않는 경우, 동작은 보장되지 않습니다.
	// 리턴된 컬렉션은 hashCode 및 equals 작업을 백업 컬렉션에 전달하지 않지만, Object의 equals 및 hashCode 메서드에 의존합니다. 이는 백업 컬렉션이 Set 또는 List인 경우, 이러한 작업의 규약을 지키기 위해 필요합니다.
	// 리턴된 컬렉션은 지정된 컬렉션이 직렬화 가능할 경우 직렬화 가능합니다.
    Parameters
    	c - 동기화된 컬렉션에서 "Wrapping" 될 컬렉션
    Returns
    	지정된 컬렉션의 동기화된 뷰
```



##### **`synchronizedSet`**

```java
public static <T> Set <T> synchronizedSet(Set <T> s)
    // 지정된 Set을 기본으로 하는 동기화된(Thread Safe) Set을 리턴합니다. 직렬 액세스를 보장하기 위해, 백업 Set에 대한 모든 액세스가 리턴된 Set을 통해 수행되어야 합니다.
    // 리턴된 Set의 반복 처리를 실시하는 경우, 사용자는 다음에 나타난 것과 같이 수동으로 동기화할 필요가 있습니다.
    	Set s = Collections.synchronizedSet(new HashSet());
			...
		synchronized(s) {
        	Iterator i = s.iterator(); 	// Must be in the synchronized block
			while(i.hasNext())
                foo(i.next());
		}
	// 이것을 실시하지 않는 경우, 동작은 보장되지 않습니다.
	// 리턴된 Set은 지정된 Set이 직렬화 가능할 경우 직렬화 가능합니다.
    Parameters
    	c - 동기화된 Set에서 "Wrapping" 될 Set
    Returns
    	지정된 Set의 동기화된 뷰
```



##### **`synchronizedSortedSet`**

```java
public static <T> SortedSet <T> synchronizedSortedSet(SortedSet <T> s)
    // 지정된 SortedSet을 기본으로 하는 동기화된(Thread Safe) SortedSet을 리턴합니다. 직렬 액세스를 보장하기 위해, 백업 SortedSet에 대한 모든 액세스가 리턴된 SortedSet(또는 그 뷰)을 통해 수행되어야 합니다.
    // 리턴된 SortedSet 또는 subSet, headSet, tailSet 뷰의 반복 처리를 실시하는 경우, 사용자는 다음에 나타난 것과 같이 수동으로 동기화할 필요가 있습니다.
    	SortedSet s = Collections.synchronizedSortedSet(new HashSortedSet());
			...
		synchronized(s) {
        	Iterator i = s.iterator(); 	// Must be in the synchronized block
			while(i.hasNext())
                foo(i.next());
		}
		또는
        SortedSet s = Collections.synchronizedSortedSet(new HashSortedSet());
		SortedSet s2 = s.headSet(foo);
			...
        synchronized(s) {
        	Iterator i = s2.iterator(); 	// Must be in the synchronized block
			while(i.hasNext())
                foo(i.next());
		}
	// 이것을 실시하지 않는 경우, 동작은 보장되지 않습니다.
	// 리턴된 SortedSet은 지정된 SortedSet이 직렬화 가능할 경우 직렬화 가능합니다.
    Parameters
    	c - 동기화된 SortedSet에서 "Wrapping" 될 SortedSet
    Returns
    	지정된 SortedSet의 동기화된 뷰
```



##### **`synchronizedList`**

```java
public static <T> List <T> synchronizedList(List <T> list)
    // 지정된 리스트를 기본으로 하는 동기화된(Thread Safe) 리스트를 리턴합니다. 직렬 액세스를 보장하기 위해, 백업 리스트에 대한 모든 액세스가 리턴된 리스트을 통해 수행되어야 합니다.
    // 리턴된 리스트의 반복 처리를 실시하는 경우, 사용자는 다음에 나타난 것과 같이 수동으로 동기화할 필요가 있습니다.
    	List list = Collections.synchronizedList(new ArrayList());
			...
		synchronized(list) {
        	Iterator i = list.iterator(); 	// Must be in the synchronized block
			while(i.hasNext())
                foo(i.next());
		}
	// 이것을 실시하지 않는 경우, 동작은 보장되지 않습니다.
	// 리턴된 리스트는 지정된 리스트가 직렬화 가능할 경우 직렬화 가능합니다.
    Parameters
    	list - 동기화된 리스트에서 "Wrapping" 될 리스트
    Returns
    	지정된 리스트의 동기화된 뷰
```



##### **`synchronizedMap`**

```java
public static <K,V> Map <K,V> synchronizedMap(Map <K,V> m)
    // 지정된 Map을 기본으로 하는 동기화된(Thread Safe) Map을 리턴합니다. 직렬 액세스를 보장하기 위해, 백업 Map에 대한 모든 액세스가 리턴된 Map을 통해 수행되어야 합니다.
    // 리턴된 Map의 반복 처리를 실시하는 경우, 사용자는 다음에 나타난 것과 같이 수동으로 동기화할 필요가 있습니다.
    	Map m = Collections.synchronizedMap(new HashMap());
			...
		Set s = m.keySet();			// Needn't be in synchronized block
			...
		synchronized(m) {				// Synchronizing on m, not s!
        	Iterator i = s.iterator(); 	// Must be in the synchronized block
			while(i.hasNext())
                foo(i.next());
		}
	// 이것을 실시하지 않는 경우, 동작은 보장되지 않습니다.
	// 리턴된 Map은 지정된 Map이 직렬화 가능할 경우 직렬화 가능합니다.
    Parameters
    	m - 동기화된 Map에서 "Wrapping" 될 Map
    Returns
    	지정된 Map의 동기화된 뷰
```



##### **`synchronizedSortedMap`**

```java
public static <K,V> SortedMap <K,V> synchronizedSortedMap(SortedMap <K,V> m)
    // 지정된 SortedMap을 기본으로 하는 동기화된(Thread Safe) SortedMap을 리턴합니다. 직렬 액세스를 보장하기 위해, 백업 SortedMap에 대한 모든 액세스가 리턴된 SortedMap을 통해 수행되어야 합니다.
    // 리턴된 SortedMap 또는 subMap, headMap, tailMap 뷰의 반복 처리를 실시하는 경우, 사용자는 다음에 나타난 것과 같이 수동으로 동기화할 필요가 있습니다.
    	SortedMap m = Collections.synchronizedSortedMap(new HashSortedMap());
			...
		Set s = m.keySet();				// Needn't be in synchronized block
			...
		synchronized(m) {				// Synchronizing on m, not s!
        	Iterator i = s.iterator(); 	// Must be in the synchronized block
			while(i.hasNext())
                foo(i.next());
		}
		또는
		SortedMap m = Collections.synchronizedSortedMap(new HashSortedMap());
		SortedMap m2 = m.subMap(foo, bar);
			...
		Set s2 = m2.keySet();				// Needn't be in synchronized block
			...
		synchronized(m) {					// Synchronizing on m, not m2 or s2!
        	Iterator i = s2.iterator(); 	// Must be in the synchronized block
			while(i.hasNext())
                foo(i.next());
		}
	// 이것을 실시하지 않는 경우, 동작은 보장되지 않습니다.
	// 리턴된 SortedMap은 지정된 SortedMap이 직렬화 가능할 경우 직렬화 가능합니다.
    Parameters
    	m - 동기화된 SortedMap에서 "Wrapping" 될 SortedMap
    Returns
    	지정된 SortedMap의 동기화된 뷰
```



##### **`frequency`**

```java
public static int frequency(Collection <?> c, Object o)
    // 지정된 컬렉션 내에서 지정된 객체와 동일한 요소의 수를 리턴합니다. 즉, (o==null ? e==null : o.equals(e))를 만족하는 컬렉션 내의 요소 e의 갯수를 리턴합니다.
    Parameters
    	c - 지정된 객체(o)의 빈도를 판단할 컬렉션
    	o - 빈도를 판단할 객체
    Returns
    	지정된 컬렉션(c) 내에 지정된 객체(o)와 동일한 요소의 수
    Exceptions
    	NullPointerException - c가 null인 경우
    Since Version
    	1.5
```



##### **`disjoint`**

```java
public static boolean disjoint(Collection <?> c1, Collection <?> c2)
    // 지정된 2개의 컬렉션에 공통의 요소가 존재하지 않는 경우 true를 리턴합니다.
    Parameters
    	c1 - 공통의 요소가 존재하는지 판단할 컬렉션
    	c2 - 공통의 요소가 존재하는지 판단할 컬렉션
    Returns
    	지정된 두 컬렉션에 공통 요소가 존재하지 않으면 true
    Exceptions
    	NullPointerException - (c1 == null || c2 == null)인 경우
    Since Version
    	1.5
```



##### **`addAll`**

```java
public static <T> boolean addAll(Collection <? super T> c, T... a)
    // 지정된 모든 요소(a)가 지정된 컬렉션(c)에 삽입됩니다. 이 메소드의 동작은 c.addAll(Arrays.asList(element))와 동일하지만, 대부분의 구현에서 더 빠르게 실행됩니다.
    Parameters
    	c - 지정된 요소를 삽입할 컬렉션
    	a - 지정된 컬렉션에 삽입될 요소들
    Returns
    	이 호출의 결과, 컬렉션이 변경되었을 경우 true
    Exceptions
    	UnsupportedOperationException - 지정된 컬렉션이 add 메소드를 지원하지 않는 경우
    	NullPointerException - 지정된 요소(a) 중, 1개 이상의 null 요소가 포함되어 있고, 지정된 컬
렉션이 null 요소를 지원하지 않는 경우. 또는 지정된 컬렉션 혹은 요소가 null인 경우
    	IllegalArgumentException - 지정된 요소의 일부 속성으로 인해 이 컬렉션에 추가할 수 없는 경우
    Since Version
    	1.5
```







> 출처

- https://docs.oracle.com/javase/8/docs/api/index.html
- http://cris.joongbu.ac.kr/course/java/api/java/util/Collections.html

