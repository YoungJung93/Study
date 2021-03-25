> # Arrays

### `Class Arrays`



이 클래스에는 정렬이나 검색 등 배열을 조작하기 위한 다양한 메서드가 있습니다. 또, 배열을 리스트로서 표시하기 위한 static 팩토리도 있습니다.

지정된 배열 참조가 null인 경우, 그 이외의 처리가 명시되고 있는 경우를 제외하고 이 클래스의 메서드는 모두 `NullPointerException`을 Throw 합니다.

이 클래스에 있는 검색 메서드의 문서에는 구현의 간단한 설명이 포함되어 있습니다. 이 설명은 규격의 일부가 아니라 구현 참고서로 간주해야 합니다. 구현자는 규격 자체를 준수하는 한, 다른 알고리즘을 자유롭게 사용할 수 있습니다. 예를 들어, sort(Object[])가 사용하는 알고리즘은 합병 정렬일 필요는 없지만, `고정(stable)`의 알고리즘이 아니면 안됩니다.



> ## Arrays의 Method



### **`sort`**

```java
public static void sort(long[] a)
public static void sort(int[] a)
public static void sort(short[] a)
public static void sort(char[] a)
public static void sort(byte[] a)
    // 지정된 배열을 오름차순으로 정렬합니다. 정렬 알고리즘은 퀵 정렬이고, 이 알고리즘은 n^2의 시간복잡도인 다른 퀵 정렬 알고리즘과 달리 n*log(n)의 시간복잡도를 제공합니다.
    Parameters
    	a - 정렬되는 배열
   
public static void sort(long[] a, int fromIndex, int toIndex)
public static void sort(int[] a, int fromIndex, int toIndex)
public static void sort(short[] a, int fromIndex, int toIndex)
public static void sort(char[] a, int fromIndex, int toIndex)
public static void sort(byte[] a, int fromIndex, int toIndex)
    // 지정된 배열을 오름차순으로 정렬합니다. 정렬되는 범위는 인덱스 fromIndex로부터 toIndex가 됩니다. 정렬 알고리즘은 퀵 정렬이고, 이 알고리즘은 n^2의 시간복잡도인 다른 퀵 정렬 알고리즘과 달리 n*log(n)의 시간복잡도를 제공합니다.
    Parameters
    	a - 정렬되는 배열
    	fromIndex - 정렬되는 최초의 요소의 인덱스
    	toIndex - 정렬되는 마지막 요소 직후의 인덱스
    Exceptions
    	IllegalArgumentException - fromIndex > toIndex인 경우
    	ArrayIndexOutOfBoundsException - fromIndex < 0 또는 toIndex > a.length인 경우
  
public static void sort(double[] a)
public static void sort(float[] a)
    // 지정된 배열을 오름차순으로 정렬합니다.
    // < 릴레이션은 모든 부동 소수점 값에 대한 전체 순서부를 제공하지 않습니다. 이 부동 소수점 값은 절대값이 다른 수치지만, -0,0f == 0.0f 는 true이며, NaN 값은 모든 부동 소수점 값이나 그 자체와 비교해도 작거나 크지도 않습니다. 이 메서드는 수치의 오름차순을 결정하는 < 릴레이션을 사용하는 대신에 Double.compareTo(java.lang.double), Float.compareTo(java.lang.float)이 실시하는 전체 순서부를 사용합니다. -0,0f는 0.0f 미만으로 다루어져 NaN이 다른 부동 소수점 값보다 크다고 보여지며, 이 순서부는 < 릴레이션과는 다릅니다. 정렬을 실행하기 위해서 모든 NaN 값은 같다고 여겨집니다.
    // 정렬 알고리즘은 퀵 정렬이고, 이 알고리즘은 n^2의 시간복잡도인 다른 퀵 정렬 알고리즘과 달리 n*log(n)의 시간복잡도를 제공합니다.
    Parameters
    	a - 정렬되는 배열
  
public static void sort(double[] a, int fromIndex, int toIndex)
public static void sort(float[] a, int fromIndex, int toIndex)
    // 지정된 배열을 오름차순으로 정렬합니다. 정렬되는 범위는 인덱스 fromIndex로부터 toIndex가 됩니다.
    // < 릴레이션은 모든 부동 소수점 값에 대한 전체 순서부를 제공하지 않습니다. 이 부동 소수점 값은 절대값이 다른 수치지만, -0,0f == 0.0f 는 true이며, NaN 값은 모든 부동 소수점 값이나 그 자체와 비교해도 작거나 크지도 않습니다. 이 메서드는 수치의 오름차순을 결정하는 < 릴레이션을 사용하는 대신에 Double.compareTo(java.lang.double), Float.compareTo(java.lang.float)이 실시하는 전체 순서부를 사용합니다. -0,0f는 0.0f 미만으로 다루어져 NaN이 다른 부동 소수점 값보다 크다고 보여지며, 이 순서부는 < 릴레이션과는 다릅니다. 정렬을 실행하기 위해서 모든 NaN 값은 같다고 여겨집니다.
    // 정렬 알고리즘은 퀵 정렬이고, 이 알고리즘은 n^2의 시간복잡도인 다른 퀵 정렬 알고리즘과 달리 n*log(n)의 시간복잡도를 제공합니다.
    Parameters
    	a - 정렬되는 배열
    	fromIndex - 정렬되는 최초의 요소의 인덱스
    	toIndex - 정렬되는 마지막 요소 직후의 인덱스
    Exceptions
    	IllegalArgumentException - fromIndex > toIndex인 경우
    	ArrayIndexOutOfBoundsException - fromIndex < 0 또는 toIndex > a.length인 경우
  
public static void sort(Object[] a)
    // 요소의 자연 정렬에 따라, 지정된 객체의 배열을 오름차순으로 정렬합니다. 배열의 모든 요소는 Comparable 인터페이스를 구현해야 합니다. 또, 배열의 모든 요소는 서로 비교할 수 있어야 합니다.(즉, e1.compareTo(e2)는 배열의 요소 e1 및 e1에 대해 ClassCastException을 발생시키지 않아야 합니다.)
    // 이 정렬은 안정성이 보장됩니다. 즉, 정렬을 실행해도 동등한 요소의 순서는 바뀌지 않습니다.
    // 정렬 알고리즘은 수정 Merge Sort입니다. 이 알고리즘은 항상 n*log(n)의 시간복잡도를 제공합니다.
    Parameters
    	a - 정렬되는 배열
    Exceptions
    	ClassCastException - 배열에 서로 비교할 수 없는 요소(예 : 문자열 및 정수)가 포함된 경우
    	IllegalArgumentException - 배열 요소의 자연스러운 순서가 Comparable 계약을 위반하는 
    								것으로 확인된 경우
    References
    	Comparable
  
public static void sort(Object[] a, int fromIndex, int toIndex)
    // 요소의 자연 정렬에 따라, 지정된 객체의 배열을 오름차순으로 정렬합니다. 정렬되는 범위는 인덱스 fromIndex로부터 toIndex가 됩니다. 배열의 모든 요소는 Comparable 인터페이스를 구현해야 합니다. 또, 배열의 모든 요소는 서로 비교할 수 있어야 합니다.(즉, e1.compareTo(e2)는 배열의 요소 e1 및 e1에 대해 ClassCastException을 발생시키지 않아야 합니다.)
    // 이 정렬은 안정성이 보장됩니다. 즉, 정렬을 실행해도 동등한 요소의 순서는 바뀌지 않습니다.
    // 정렬 알고리즘은 수정 Merge Sort입니다. 이 알고리즘은 항상 n*log(n)의 시간복잡도를 제공합니다.
    Parameters
    	a - 정렬되는 배열
    	fromIndex - 정렬되는 최초의 요소의 인덱스
    	toIndex - 정렬되는 마지막 요소 직후의 인덱스
    Exceptions
    	ClassCastException - 배열에 서로 비교할 수 없는 요소(예 : 문자열 및 정수)가 포함된 경우
    	ArrayIndexOutOfBoundsException - fromIndex < 0 또는 toIndex > a.length인 경우
    	IllegalArgumentException - 배열 요소의 자연스러운 순서가 Comparable 계약을 위반하는 
    								것으로 확인된 경우
    References
    	Comparable
  
public static void sort(T[] a, Comparator <? super T> c)
    // 지정된 Comparator가 지시하는 순서에 따라 지정된 객체의 배열을 오름차순으로 정렬합니다. 배열의 모든 요소는 서로 비교할 수 있어야 합니다.(즉, e1.compareTo(e2)는 배열의 요소 e1 및 e1에 대해 ClassCastException을 발생시키지 않아야 합니다.)
    // 이 정렬은 안정성이 보장됩니다. 즉, 정렬을 실행해도 동등한 요소의 순서는 바뀌지 않습니다.
    // 정렬 알고리즘은 수정 Merge Sort입니다. 이 알고리즘은 항상 n*log(n)의 시간복잡도를 제공합니다.
    Parameters
    	a - 정렬되는 배열
    	c - 배열의 순서를 결정하는 Comparator. null값은 요소의 자연 정렬을 사용하는 것을 나타냅니다.
    Exceptions
    	ClassCastException - 배열에 서로 비교할 수 없는 요소(예 : 문자열 및 정수)가 포함된 경우
    	IllegalArgumentException - 배열 요소의 자연스러운 순서가 Comparable 계약을 위반하는 
    								것으로 확인된 경우
    References
    	Comparator
  
public static void sort(T[] a, int fromIndex, int toIndex, Comparator <? super T> c)
    // 지정된 Comparator가 지시하는 순서에 따라 지정된 객체의 배열을 오름차순으로 정렬합니다. 정렬되는 범위는 인덱스 fromIndex로부터 toIndex가 됩니다. 배열의 모든 요소는 서로 비교할 수 있어야 합니다.(즉, e1.compareTo(e2)는 배열의 요소 e1 및 e1에 대해 ClassCastException을 발생시키지 않아야 합니다.)
    // 이 정렬은 안정성이 보장됩니다. 즉, 정렬을 실행해도 동등한 요소의 순서는 바뀌지 않습니다.
    // 정렬 알고리즘은 수정 Merge Sort입니다. 이 알고리즘은 항상 n*log(n)의 시간복잡도를 제공합니다.
    Specified by
    Parameters
    	a - 정렬되는 배열
    	fromIndex - 정렬되는 최초의 요소의 인덱스
    	toIndex - 정렬되는 마지막 요소 직후의 인덱스
    	c - 배열의 순서를 결정하는 Comparator. null값은 요소의 자연 정렬을 사용하는 것을 나타냅니다.
    Exceptions
    	ClassCastException - 배열에 서로 비교할 수 없는 요소(예 : 문자열 및 정수)가 포함된 경우
    	ArrayIndexOutOfBoundsException - fromIndex < 0 또는 toIndex > a.length인 경우
    	IllegalArgumentException - 배열 요소의 자연스러운 순서가 Comparable 계약을 위반하는 
    								것으로 확인된 경우
    References
    	Comparator
```



### **`binarySearch`**

```java
public static int binarySearch(long[] a, long key)
public static int binarySearch(int[] a, int key)
public static int binarySearch(short[] a, short key)
public static int binarySearch(char[] a, char key)
public static int binarySearch(byte[] a, byte key)
    // 이진 탐색 알고리즘을 사용해 지정된 배열로부터 지정된 key 값을 검색합니다. 이 메서드를 호출하기 전에 sort 메서드를 이용하여 배열을 정렬할 필요가 있습니다. 배열이 정렬되어 있지 않은 경우 결과는 정의되지 않습니다. 범위에 지정된 값을 가진 여러 요소가 포함된 경우, 어떤 요소를 찾을지 보장할 수 없습니다.
    Parameters
    	a - 검색되는 배열
    	key - 검색되는 값
    Returns
    	배열에 key가 있는 경우는 key의 인덱스. 그렇지 않으면 (-(삽입 지점)-1) 값이 리턴됩니다.
    	삽입 지점은 key가 배열에 삽입되는 지점으로 정의됩니다. 즉, key 보다 큰 최초의 요소의 인덱스,
		또는 해당 범위의 모든 요소가 key보다 작은 경우는 a.length가 됩니다. 
		이렇게 하면, key가 발견된 경우에만 반환 값이 0이상이고, 발견되지 않은 경우에는 음수가 됩니다.
    References
		sort();
            
public static int binarySearch(double[] a, double key)
public static int binarySearch(float[] a, float key)
    // 이진 탐색 알고리즘을 사용해 지정된 배열로부터 지정된 key 값을 검색합니다. 이 메서드를 호출하기 전에 sort 메서드를 이용하여 배열을 정렬할 필요가 있습니다. 배열이 정렬되어 있지 않은 경우 결과는 정의되지 않습니다. 범위에 지정된 값을 가진 여러 요소가 포함된 경우, 어떤 요소를 찾을지 보장할 수 없습니다. 이 메서드에서는 모든 NaN 값은 같다고 여겨집니다.
    Parameters
    	a - 검색되는 배열
    	key - 검색되는 값
    Returns
    	배열에 key가 있는 경우는 key의 인덱스. 그렇지 않으면 (-(삽입 지점)-1) 값이 리턴됩니다.
    	삽입 지점은 key가 배열에 삽입되는 지점으로 정의됩니다. 즉, key 보다 큰 최초의 요소의 인덱스,
		또는 해당 범위의 모든 요소가 key보다 작은 경우는 a.length가 됩니다. 
		이렇게 하면, key가 발견된 경우에만 반환 값이 0이상이고, 발견되지 않은 경우에는 음수가 됩니다.
	References
		sort();

public static int binarySearch(Object[] a, Object key)
    // 이진 탐색 알고리즘을 사용해 지정된 배열로부터 지정된 객체를 검색합니다. 이 메서드를 호출하기 전에 sort 메서드를 이용하여 배열을 정렬할 필요가 있습니다. 배열이 정렬되어 있지 않은 경우 결과는 정의되지 않습니다. 범위에 지정된 객체를 가진 여러 요소가 포함된 경우, 어떤 요소를 찾을지 보장할 수 없습니다.
    Parameters
    	a - 검색되는 배열
    	key - 검색되는 값
    Returns
    	배열에 key가 있는 경우는 key의 인덱스. 그렇지 않으면 (-(삽입 지점)-1) 값이 리턴됩니다.
    	삽입 지점은 key가 배열에 삽입되는 지점으로 정의됩니다. 즉, key 보다 큰 최초의 요소의 인덱스,
		또는 해당 범위의 모든 요소가 key보다 작은 경우는 a.length가 됩니다. 
		이렇게 하면, key가 발견된 경우에만 반환 값이 0이상이고, 발견되지 않은 경우에는 음수가 됩니다.
	Exceptions
		ClassCastException - Key가 배열의 요소와 동등하지 않은 경우
	References
		Comparable, sort();

public static <T> int binarySearch(T[] a, T key, Comparator <? super T> c)
    // 이진 탐색 알고리즘을 사용해 지정된 배열로부터 지정된 객체를 검색합니다. 이 메서드를 호출하기 전에 지정된 Comparator에 따라 배열이 정렬됩니다. 배열이 정렬되지 않은 경우 결과는 정의되지 않습니다. 범위에 지정된 객체를 가진 여러 요소가 포함된 경우, 어떤 요소를 찾을지 보장할 수 없습니다.
    Parameters
    	a - 검색되는 배열
    	key - 검색되는 값
    	c - 배열의 순서를 결정하는 Comparator. null값은 요소의 자연 정렬을 사용하는 것을 나타냅니다.
    Returns
    	배열에 key가 있는 경우는 key의 인덱스. 그렇지 않으면 (-(삽입 지점)-1) 값이 리턴됩니다.
    	삽입 지점은 key가 배열에 삽입되는 지점으로 정의됩니다. 즉, key 보다 큰 최초의 요소의 인덱스,
		또는 해당 범위의 모든 요소가 key보다 작은 경우는 a.length가 됩니다. 
		이렇게 하면, key가 발견된 경우에만 반환 값이 0이상이고, 발견되지 않은 경우에는 음수가 됩니다.
	Exceptions
		ClassCastException - 지정된 Comparator로 서로 비교할 수 없는 요소가 배열에 포함되어 있는
            				경우, 혹은 key가 Comparator를 사용하는 배열의 요소와 서로 비교할 수
            				없는 경우
	References
		Comparable, sort(Object[], Comparator);
```



### **`equals`**

```java
public static boolean equals(long[] a, long[] a2)
public static boolean equals(int[] a, int[] a2)
public static boolean equals(short[] a, short[] a2)
public static boolean equals(char[] a, char[] a2)
public static boolean equals(byte[] a, byte[] a2)
public static boolean equals(boolean[] a, boolean[] a2)
    // 지정된 2개의 배열이 서로 동등한 경우 true를 리턴합니다. 2개의 배열이 동등이라는 것은 양쪽 모두의 배열에 같은 수의 요소가 있고 대응하는 요소가 모두 동등한 경우입니다. 즉, 같은 순서로 같은 요소가 있는 2개의 배열은 동등합니다. 또, 2개의 배열이 모두 null을 참조하는 경우에도 동등하다고 판단합니다.
    Parameters
    	a - 동등한지를 판단하는 첫 번째 배열
    	a2 - 동등한지를 판단하는 두 번째 배열
    Returns
    	2개의 배열이 동등한 경우 true
    
public static boolean equals(double[] a, double[] a2)
public static boolean equals(float[] a, float[] a2)
    // 지정된 2개의 배열이 서로 동등한 경우 true를 리턴합니다. 2개의 배열이 동등이라는 것은 양쪽 모두의 배열에 같은 수의 요소가 있고 대응하는 요소가 모두 동등한 경우입니다. 즉, 같은 순서로 같은 요소가 있는 2개의 배열은 동등합니다. 또, 2개의 배열이 모두 null을 참조하는 경우에도 동등하다고 판단합니다.
    // == 연산자와 달리, 이 메서드는 NaN은 자기 자신과 동일하고, 0.0f, 0.0d는 각각 -0,0f, -0,0d와 동등하지 않습니다.
    Parameters
    	a - 동등한지를 판단하는 첫 번째 배열
    	a2 - 동등한지를 판단하는 두 번째 배열
    Returns
    	2개의 배열이 동등한 경우 true
    References
    	Double.equals(Object), Float.equals(Object)
    
public static boolean equals(Object[] a, Object[] a2)
    // 지정된 2개의 배열이 서로 동등한 경우 true를 리턴합니다. 2개의 배열이 동등이라는 것은 양쪽 모두의 배열에 같은 수의 요소가 있고 대응하는 요소가 모두 동등한 경우입니다. 즉, 같은 순서로 같은 요소가 있는 2개의 배열은 동등합니다. 또, 2개의 배열이 모두 null을 참조하는 경우에도 동등하다고 판단합니다.
    Parameters
    	a - 동등한지를 판단하는 첫 번째 배열
    	a2 - 동등한지를 판단하는 두 번째 배열
    Returns
    	2개의 배열이 동등한 경우 true
```

 

### **`fill`**

```java
public static void fill(long[] a, long val)
public static void fill(int[] a, int val)
public static void fill(short[] a, short val)
public static void fill(char[] a, char val)
public static void fill(byte[] a, byte val)
public static void fill(boolean[] a, boolean val)
public static void fill(double[] a, double val)
public static void fill(float[] a, float val)
    // 지정된 배열에 val 값을 할당합니다.
    Parameters
    	a - 값을 대입할 배열
    	val - 배열에 모든 요소에 할당할 값
    
public static void fill(long[] a, int fromIndex, int toIndex, long val)
public static void fill(int[] a, int fromIndex, int toIndex, int val)
public static void fill(short[] a, int fromIndex, int toIndex, short val)
public static void fill(char[] a, int fromIndex, int toIndex, char val)
public static void fill(byte[] a, int fromIndex, int toIndex, byte val)
public static void fill(boolean[] a, int fromIndex, int toIndex, boolean val)
public static void fill(double[] a, int fromIndex, int toIndex, double val)
public static void fill(float[] a, int fromIndex, int toIndex, float val)
    // 지정된 배열의 지정된 범위에 있는 각 요소에 val 값을 할당합니다. 값을 할당하는 범위는 인덱스 fromIndex로부터 toIndex 직전까지가 됩니다. (fromIndex==toIndex인 경우, 할당하는 범위는 비웁니다.)
    Parameters
    	a - 값을 대입할 배열
    	fromIndex - 지정된 값을 할당하는 최초의 요소의 인덱스
    	toIndex - 지정된 값을 대입하는 마지막 요소 직후의 인덱스
    	val - 배열에 모든 요소에 할당할 값
    Exceptions
    	IllegalArgumentException - fromIndex > toIndex 인 경우
    	ArrayIndexOutOfBoundsException - fromIndex < 0 또는 toIndex > a.length인 경우

public static void fill(Object[] a, Object val)
    // 지정된 Object 배열의 각 요소에 val의 참조값을 할당합니다.
    Parameters
    	a - 값을 대입할 배열
    	val - 배열의 모든 요소에 할당할 값
    
public static void fill(Object[] a, int fromIndex, int toIndex, Object val)
    // 지정된 Object 배열의 지정된 범위에 있는 각 요소에 val의 참조값을 할당합니다. 값을 할당하는 범위는 인덱스 fromIndex로부터 toIndex 직전까지가 됩니다. (fromIndex==toIndex인 경우, 할당하는 범위는 비웁니다.)
    Parameters
    	a - 값을 대입할 배열
    	fromIndex - 지정된 값을 할당하는 최초의 요소의 인덱스
    	toIndex - 지정된 값을 대입하는 마지막 요소 직후의 인덱스
    	val - 배열에 모든 요소에 할당할 값
    Exceptions
    	IllegalArgumentException - fromIndex > toIndex 인 경우
    	ArrayIndexOutOfBoundsException - fromIndex < 0 또는 toIndex > a.length인 경우
```



### **`asList`**

```java
public static <T> List <T> asList(T...a)
    // 지정된 배열을 기본으로 하는 고정 사이즈의 리스트를 리턴합니다. 리턴된 리스트의 변경은 그대로 배열에 출력됩니다. 이 메서드는 Collection.toArray()와 함께 배열 기반 API와 컬렉션 기반 API 사이의 다리 역할을 합니다. 반환된 목록은 직렬화가 가능하며 RandomAccess를 구현합니다.
    // 또한, 이 메서드는 여러 요소를 포함하도록 초기화된 고정 크기 리스트를 만드는 편리한 방법도 제공합니다.
    // List<String> stooges = Arrays.asList("Larry", "Moe", "Curly");
    Type Parameters
    	T - 배열의 객체 클래스
    Parameters
    	a - 리스트로 변환될 배열
    References
    	Collection.toArray()    
```



### **`hashCode`**

```java
public static int hashCode(long[] a)
public static int hashCode(int[] a)
public static int hashCode(short[] a)
public static int hashCode(char[] a)
public static int hashCode(byte[] a)
public static int hashCode(boolean[] a)
public static int hashCode(double[] a)
public static int hashCode(float[] a)
    // 지정된 배열의 내용을 기반으로 해시 코드를 리턴합니다. Arrays.equals(a,b)로 표현될 수 있는 두 개의 배열 a, b의 경우, Arrays.hashCode(a)==Arrays.hashCode(b) 라고도 표현할 수 있습니다.
    // 이 메서드가 리턴하는 값은 a 요소를 같은 순서로 표현하는 인스턴스의 순서를 포함한 리스트에 대해 hashCode 메서드를 호출해 얻는 값과 같습니다. a가 null인 경우, 이 메서드는 0을 리턴합니다.
    Parameters
    	a - 해시 값을 계산할 배열
    Returns
    	a 내용 기반의 해시 코드
    
public static int hashCode(Object[] a)
    // 지정된 배열의 내용을 기반으로 해시 코드를 리턴합니다. 배열에 다른 배열이 요소로 포함되어 있는 경우, 해시 코드는 내용이 아닌 식별 정보를 기반으로 합니다. 따라서 하나 이상의 배열 수준을 통해 직접 또는 간접적으로 자신을 요소로 포함하는 배열에서 이 메서드를 호출할 수 있습니다.
    // Arrays.equals(a,b)로 표현될 수 있는 두 개의 배열 a, b의 경우, Arrays.hashCode(a)==Arrays.hashCode(b) 라고도 표현할 수 있습니다.
    // 이 메서드가 리턴하는 값은 a 요소를 같은 순서로 포함한 리스트에 대해 hashCode 메서드를 호출해 얻는 값과 같습니다. a가 null인 경우, 이 메서드는 0을 리턴합니다.
    Parameters
    	a - 해시 값을 계산할 배열
    Returns
    	a의 내용 기반의 해시 코드
    Since Version
    	1.5
    References
    	deepHashCode(Object[])
```



### **`deepHashCode`**

```java
따라서 하나 이상의 배열 수준을 통해 직접 또는 간접적으로 자신을 요소로 포함하는 배열에서 이 메서드를 호출할 수 있습니다.public static int deepHashCode(Object[] a)
    // 지정된 배열의 "심층 내용"에 근거하는 해시 코드를 리턴합니다. 배열에 다른 배열이 요소로 포함되어 있는 경우, 해시 코드는 내용 및 그 외 모두에 근거한 것이 됩니다. 따라서 하나 이상의 배열 수준을 통해 직접 또는 간접적으로 자신을 요소로 포함하는 배열에서 이 메서드를 호출할 수 없습니다. 이런 종류의 호출 동작은 정의되지 않습니다.
    // Arrays.deepEquals(a,b)로 표현될 수 있는 두 개의 배열 a, b의 경우, Arrays.deepHashCode(a)==Arrays.deepHashCode(b) 라고도 표현할 수 있습니다.
    // 이 메서드가 리턴하는 값은 a 요소를 같은 순서로 포함한 리스트에 대해 List.hashCode() 메서드를 호출해 얻는 값과 유사합니다. 다만, a 요소 e 자신이 배열일 경우, 그 해시 코드의 계산은 e.hashCode()를 호출하는 것이 아니라, Arrays.hashCode(e)의 적절한 오버로딩을 호출하여 계산됩니다.(e가 원시 유형의 배열인 경우) (e가 참조 유형의 배열인 경우) Arrays.deepHashCode(e)를 재귀적으로 호출하여 계산됩니다. a가 null인 경우, 이 메서드는 0을 리턴합니다.
    Parameters
    	a - 심층 내용 기반의 해시 코드를 계산할 배열
    Returns
    	a의 심층 내용 기반의 해시 코드
    Since Version
    	1.5
    References
    	hashCode(Object[])
```



### **`deepEquals`**

```java
public static boolean deepEquals(Object[] a1, Object[] a2)
    // 2개의 지정된 배열이 서로 "심층적으로 등가"인 경우, true를 리턴합니다. equals(Object[], Object[] ) 메서드와는 달리, 이 메서드는 임의 깊이의 중첩 배열에 사용하기 적합합니다.
    // 양쪽 모두가 null인 경우, 2개의 배열은 심층적으로 등가하다고 판단됩니다. 또, 동일한 수의 요소를 포함하고 두 배열의 대응되는 모든 요소가 동일할 경우도 심층적으로 등가하다고 판단됩니다.
    // null 가능성이 있는 2개의 요소 e1 및 e2는 다음의 조건 중 하나 이상에 적합한 경우, 심층적으로 등가합니다.
    // 1. e1와 e2 양쪽 모두가 객체 참조형의 배열이며, Arrays.deepEquals(e1, e2)가 true이다.
    // 2. e1와 e2가 같은 원시형의 배열이며, Arrays.equals(e1, e2)의 적절한 Overload가 true이다.
    // 3. e1 == e2
    // 4. e1.equals(e2)가 true이다.
    // 이 정의에서는 임의의 깊이의 null 요소가 허용된다는 점에 주의하세요.
    // 지정된 배열 중 하나가 하나 이상의 배열 수준을 통해 직접 또는 간접적으로 요소로서 자신을 포함하는 경우, 이 메서드의 동작은 정의되지 않습니다.
    Parameters
    	a1 - 동등한지를 판단할 첫 번째 배열
    	a2 - 동등한지를 판단할 두 번째 배열
    Returns
    	2개의 배열이 심층적으로 등가일 경우 true
    Since Version
    	1.5
    References
    	equals(Object[], Object[])
```



### **`toString`**

```java
public static String toString(long[] a)
public static String toString(int[] a)
public static String toString(short[] a)
public static String toString(char[] a)
public static String toString(byte[] a)
public static String toString(boolean[] a)
public static String toString(double[] a)
public static String toString(float[] a)
    // 지정된 배열의 내용에 대한 문자열 표현을 리턴합니다. 문자열 표현은 대괄호("[]")로 둘러싸인 배열 요소의 리스트로 구성됩니다. 인접하는 요소는 문자(,)로 구분됩니다. 요소는 String.valueOf()에 의해 문자열로 변환됩니다. a가 null일 경우, null을 리턴합니다.
    Parameters
    	a - 문자열로 변환할 배열
    Returns
    	a의 문자열 표현
    Since Version
    	1.5
    
public static String toString(Object[] a)
    // 지정된 배열의 내용에 대한 문자열 표현을 리턴합니다. 배열에 다른 배열이 요소로 포함되어 있으면 Object.toString() 메서드에 의해 배열이 문자열로 변환됩니다. Object에는 내용이 아닌 식별 정보가 기술됩니다.
    // 이 메서드에 의해 리턴된 값은, a가 null인 경우를 제외하면, Arrays.asList(a).toString()에 의해 리턴된 값과 동일합니다. a가 null인 경우, null을 리턴합니다.
    Parameters
    	a - 문자열로 변환할 배열
    Returns
    	a의 문자열 표현
    Since Version
    	1.5
    References
    	deepToString(Object[])
```



### **`deepToString`**

```java
public static String deepToString(Object[] a)
    // 지정된 배열의 내용에 대한 "심층 내용"의 문자열 표현을 리턴합니다. 배열에 다른 배열이 요소로 포함되어 있으면 문자열에 해당 내용 등이 포합됩니다. 이 메서드는 다차원 배열을 문자열로 변환하도록 설계되었습니다.
    // 문자열 표현은 대괄호("[]")로 둘러싸인 배열 요소의 리스트로 구성됩니다. 인접하는 요소는 문자(,)로 구분됩니다. 요소는 그 자체가 배열이 아닌 한, String.valueOf(Object)에 의해 문자열로 변환됩니다.
    // 요소 e가 원시형의 배열인 경우, Arrays.toString(e)의 적절한 Overload를 호출하여 문자열로 변환됩니다. 요소 e가 참조형의 배열인 경우, 이 메서드를 재귀적으로 호출하여 문자열로 변환합니다.
    // 무한의 재귀를 방지하기 위해, 배열이 자신을 요소로 포함하거나 하나 이상의 배열 수준을 통해 자신에 대한 간접 참조를 포함하는 경우 자체 참조는 문자열 "[...]"로 변환됩니다. 예를 들어, 자신에 대한 참조만 포함하는 배열은 "[[...]]"로 렌더링됩니다.
    // 지정된 배열이 null인 경우, 이 메서드는 null을 리턴합니다.
    Parameters
    	a - 문자열로 변환할 배열
    Returns
    	a의 문자열 표현
    Since Version
    	1.5
    References
    	toString(Object[])
```







> 출처

- https://docs.oracle.com/javase/8/docs/api/index.html
- http://cris.joongbu.ac.kr/course/java/api/java/util/Arrays.html