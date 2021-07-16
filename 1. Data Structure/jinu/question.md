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

  #### 2.
  
