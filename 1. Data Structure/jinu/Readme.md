
-----
 ## 진우 

 ### 💡 Array
  - 연관된 데이터를 하나의 변수에 그룹핑하여 관리하기 위한 구조
  - 1차, 2차, 3차 배열 모두 데이터 구조에 속합니다. 
  - 배열은 고정된 크기를 가지도록 선언/초기화 할 수 있으며 배열 범위를 초과할 경우 인덱스 초과 런타임 오류가 발생합니다.
  - #### 장점 : 배열은 순차탐색, 랜덤액세스가 빠릅니다.
  - #### 단점 : 고정된 크기를 동적으로 바꿀 수 없습니다. 데이터 삽입, 삭제가 비효율적입니다.
  <br/><br/>
  

 Ex. 변수 A 에 스터디원의 이름을 담아보자
 
  |***A***|진우|가빈|윤아|아연|민영|
  |--|-|-|-|-|-|  
  
   -> 변수 A에 진우, 가빈, 윤아, 아연, 민영 순으로 담겼습니다.
 
  #### 그렇다면 배열로 각 사람들이 좋아하는 CS 과목을 함께 묶어서 저장할 수는 없을까??  
 
  |***A***|진우|가빈|윤아|아연|민영|
  |--|:-:|:-:|:-:|:-:|:-:|
  |  |OS|DB|AI|Network|Data Structure|
  
  다음과 같은 데이터 구조를 저장하는 Java 기준 소스
  ```
    String[][] data = new String[2][5];
    for(int i=0; i<2; i++){
        for(int j=0; j<5; j++) data[i][j] = [담을 정보];
    }
  ```
  <br><br>
  
 
  ### 💡  Linked List
   - LinkedList는 다음과 같이 표현됩니다.    
   ![linkedlist](./images/linkedlist.png)
   - LinkedList는 ArrayList와 함께 List를 구체화한 클래스입니다.
   - ArrayList는 배열을 이용하여 List를 구현한 클래스입니다.
   - 각 정보는 노드 내 데이터를 담는 파트에 저장되어있습니다.
   - 노드는 데이터와 함께 다음노드(next), 이전노드(prev)와 연결되어 있습니다.
   - #### 장점 : 삽입, 삭제가 빠릅니다. 어느 위치에 삽입, 삭제가 일어나도 해당 노드와 연결된 노드만 관리하면 됩니다.
   - #### 단점 : 다음노드 참조를 위해 추가적인 메모리가 할당되어야합니다. 순차 탐색을 하므로 랜덤 액세스가 느릴 수 있습니다.

<br><br>

   - 리스트 선언/초기화하는 방법
   ```
   LinkedList<Integer> integers1 = new LinkedList<>();  // iNT 타입의 원소를 가지는 리스트
   LinkedList<Integer> integers2 = new LinkedList<>(Arrays.asList(1, 2, 3, 4)); // 배열 값을 리스트로 초기화
   
   integers1.add(10);  // 리스트의 마지막노드 뒤에 '10'값을 가지는 데이터 담기   integers1 = {10}
   integers1.add(0, 20);  // 리스트의 첫번째 위치에 '20'값을 가지는 데이터 담기   integers1 = {20, 10}
   integers1.set(0, 5);  // integers1 리스트의 첫번째 노드의 데이터를 '5'로 변경   integers1 = {5, 10}
   integers1.remove(5);  // '5' 값을 가지고 있는 첫번째 노드를 삭제합니다.   integers1 = {10}
   ```
   
  <br><br>
  
 ### 💡  Hash Table
  - Key, Value 쌍으로 데이터를 저장하는 구조로 가장 빠르게 데이터를 탐색할 수 있는 자료구조 중 하나입니다.
  - 검색 속도가 빠른 이유는 내부적으로 배열을 사용하여 데이터를 저장하기 때문입니다.
  - 각각의 Key 값에 해시함수를 적용하여 배열의 고유한 Index를 생성하고 이를 통해 검색을 진행합니다.
  - 데이터 저장, 삭제, 조회에 드는 시간 복잡도는 O(1)입니다. (단, 해시 충돌 발생 시 O(N))
  - 해시 함수를 거친 값이 같아지는 현상인 해시 충돌의 경우는 '분리 연결법', '개방 주소법'를 통해 해결합니다.
  - #### 장점 : 저장, 삭제, 조회 속도가 빠릅니다.
  - #### 단점 : 공간 복잡도(메모리 사용)가 큽니다. 순서가 없으므로 순차적 작업이 필요할 때는 효율성이 떨어집니다.

  <br><br>
  * 해시테이블? 해시맵?
  -> 우리는 자바에서 주로 HashMap을 통해 Key, Value 쌍 데이터를 저장하고 사용합니다.
  -> HashTable과 HashMap의 차이는 동기화를 지원하는가? 여부에 있습니다.
   -> HashTable : 동기화 지원 / HashMap : 동기화 미지원
  <br>
  put(삽입) 작업에서 HashTable과 HashMap의 차이
  ```
  // 해시테이블의 put
  public synchronized V put(K key, V value) { // Make sure the value is not null
        if (value == null) { throw new NullPointerException(); }
        // Makes sure the key is not already in the hashtable.
        Entry<?,?> tab[] = table;
        int hash = key.hashCode();
        int index = (hash & 0x7FFFFFFF) % tab.length;
        
        @SuppressWarnings("unchecked") Entry<K,V> entry = (Entry<K,V>)tab[index];
        for(; entry != null ; entry = entry.next) { 
            if ((entry.hash == hash) && entry.key.equals(key)) { 
                V old = entry.value; entry.value = value; return old; 
            } } addEntry(hash, key, value, index); return null; 
    } 
    
    // 해시맵의 put 
    public V put(K key, V value) {
        return putVal(hash(key), key, value, false, true);
    }
  ```
  
  HashTable은 Synchronized 키워드가 붙어있는 것과 같이 병렬 프로그래밍 시 동기화를 지원합니다.
  병렬 처리를 고려한다면 HashTable을 그렇지 않다면 HashMap을 사용하면 됩니다.
  
  
  
  💡  Stack
  💡  Queue
  💡  Graph
  💡  Tree
  💡  그래프와 트리의 차이


-----


:arrow_forward: [테스트](../Readme.md)
