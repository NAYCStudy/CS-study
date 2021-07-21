   ```
   import java.util.Stack;

   // Stack 2개로 Queue 구현
   public class Stack_Practice {
    static int[] src = {0, 1, 2, 3, 4, 5};
    static Stack<Integer> stack1 = new Stack<>();
    static Stack<Integer> stack2 = new Stack<>();

    public static void main(String[] args) {

     stack1.add(1);
     stack1.add(2);
     stack1.add(3);
     stack1.add(4);
     stack1.add(5);

     while(!stack1.isEmpty()) System.out.println(poll());
    }

    static public void moveAll() {
     while(!stack1.isEmpty()) {
      stack2.add(stack1.pop());
     }
    }

    static public void moveAllBack() {
     while(!stack2.isEmpty()) {
      stack1.add(stack2.pop());
     }
    }

    static public void add(int data) {
     stack1.add(data);
    }

    static public int peek() {
     if(stack2.isEmpty()) moveAll();
     int ret = stack2.peek();
     moveAllBack();
     return ret;
    }

    static public int poll() {
     if(stack2.isEmpty()) moveAll();
     int ret = stack2.pop();
     moveAllBack();
     return ret;
    }
   }

   ```  
