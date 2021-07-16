```
// LinkedList 구현 클래스

public class SingleLinkedListPractice {
	private Node node;
	
	// 리스트의 head 부분에 노드 추가
	public void addFirst(String data) {
		Node newNode = new Node(data, node);
		node = newNode;
	}
	
	// 리스트의 마지막 노드 반환
	public Node getLast() {
		Node curr = node;
		
		while(curr != null && curr.link != null) curr = curr.link;
		return curr;
	}
	
	// 리스트의 마지막 부분에 노드 추가
	public void addLast(String data) {
		
		Node last = getLast();
		if(last == null) addFirst(data);
		else {
			Node newNode = new Node(data);
			last.link = newNode;
		}
	}
	
	// 리스트의 중간에 노드를 추가 
	public void addMid(Node prev, String data) {
		if(prev == null) return;
		
		Node newNode = new Node(data, prev.link);
		prev.link = newNode;
	}
	
	// data를 기준으로 해당 노드 반환
	public Node getByData(String data) {
		for(Node curr=node; curr != null; curr = node.link) {
			if(curr.data.equals(data)) return curr;
		}
		return null;
	}
	
	// 인덱스 번호를 기준으로 해당 노드를 반환
	public Node get(int Idx) {
		int nowIdx = 0;
		for(Node curr=node; curr != null; curr=curr.link) {
			if(nowIdx == Idx) return curr;
			nowIdx++;
		}
		
		return null;
	}
	
	// 삭제 작업을 위한 이전 노드 찾기
	public Node getPrev(Node target) {
		for(Node curr=node; curr != null; curr = curr.link) {
			if(curr.link == target) return curr;		// target의 이전 노드 반환
		}
		return null;
	}
	
	// 인덱스를 기준으로 삭제
	public void del(int idx) {
		if(node == null) return;
		
		if(idx == 0 && node != null) {
			node = node.link;
			return;
		}
		
		int nowIdx = 0;
		Node prevNode = null;
		
		for(Node curr=node; curr != null; curr = curr.link) {
			if(nowIdx+1 == idx) prevNode = curr;
			else if(nowIdx == idx) {
				prevNode.link = curr.link;
				curr.link = null;
				break;
			}
			nowIdx++;
		}
	}
	
	// 데이터를 기준으로 노드 삭제
	public void delByData(String data) {
		if(node == null) return;
		
		Node currNode = getByData(data);
		if(currNode == null) return;
		
		Node prevNode = getPrev(currNode);
		if(prevNode == null) {
			node = currNode.link;
			return;
		}
		
		prevNode.link = currNode.link;
		currNode.link = null;
		
	}

	// 오버로딩 리스트의 전체 노드 출력
	public void print() {
		StringBuilder sb = new StringBuilder();
		int i=0;
		for(Node curr=node; curr != null; curr=curr.link) {
			sb.append(i++ + " : " + curr.data + "\n");
		}
		System.out.println(sb);
	}
	
	// 리스트에서 해당 노드의 data 출력
	public void print(Node node) {
		if(node == null) {
			System.out.println("Out Of Bound Index");
			return;
		}
		
		System.out.println(node.data);
	}
}


// 노드 객체
public class Node {
	public String data;
	public Node link;
	
	public Node(String data) {
		super();
		this.data = data;
	}
	
	public Node(String data, Node link) {
		super();
		this.data = data;
		this.link = link;
	}
}


// 테스트 메인
public class SingleLinkedListTest {
	public static void main(String[] args) {
		SingleLinkedListPractice list = new SingleLinkedListPractice();
		
		list.addFirst("A");
		list.addLast("B");
		
		list.addMid(list.get(0), "C");
		list.addMid(list.get(2), "D");
		list.print();
		
		list.print(list.getByData("C"));
		list.print(list.get(5));
		
		list.print(list.getLast());
		
		list.del(0);
		list.delByData("B");
		
		list.addFirst("X");
		list.print();
	}
}


```
