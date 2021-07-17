아연  
### 1. 스택 두개로 큐 구현해보기   
### 2. Binary Tree와 Binary Search Tree의 차이점 설명하기  

<br>

진우  

  ### 1. 연결 리스트를 직접 구현할 때 리스트의 가장 앞 쪽 위치에 노드를 추가하는 메소드를 만들어보자!
  <br>



  ### 2. 그래프와 트리의 차이점과 특징에 대해 설명해보자!




  <br><br><br><br>


  ### Solve

  #### 1.
  :arrow_forward: [LinkedList 보러가기](./LinkedList/Readme.md)
  <br>
  Node 객체는 만들어져 있다고 가정   
  <br>
  Field  
  String data;  
  Node link;  
  ```

  private Node node;          // 노드 객체 

  public void addFirst(String data){
    Node newNode = new Node(data, node);    // 새 노드를 생성해서 넘어온 Data를 담고 가장 앞쪽 노드로 Link를 건다.
    node = newNode;                         // 첫번째 위치에 새 노드가 추가된 newNode 변수를 node에 할당한다.
  }

  ```   
  
  <br>
  
  #### 2.  
  - 그래프는 노드와 다른 노드를 연결하는 간선을 하나로 모아놓은 자료구조이며 트리는 그래프의 한 종류로써 방향성이 없는 비순환 그래프를 의미합니다.  
  - 그래프는 네트워크 모델 / 트리는 계층적 모델  
  - 또한, 트리의 경우 그래프에서는 존재하지 않는 Root Node라는 개념이 존재합니다. Root Node가 최상위 부모 노드가 되며 해당 노드로 부터 자식 노드를 통해 뻗어 나가는 구조입니다.  
  - 그래프는 노드 간 모두 평등한 개념이지만 트리의 경우 부모-자식이라는 계층적인 개념을 가지는 구조입니다.  
  - 트리의 또 다른 특징으로 간선의 수는 항상 노드 개수-1 입니다.  


  2021.07.16

  
