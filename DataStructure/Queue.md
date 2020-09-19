# JAVA 
- 큐는 FIFO 형태의 자료구조 
- 자바에서 Queue는 인터페이스이므로 객체 생성이 불가능하다. 
- 따라서 LinkedList를 형변환하여 조작한다.

### 1. Linked List를 형변환하여 큐 조작 
``` java
import java.util.LinkedList;
import java.util.Queue;
import java.util.Stack;
public class StackQueueTest {
  public static void main(String[] args) {
    Queue<String> queue = new LinkedList<String>();
    for (int i=0; i<3; i++)
      queue.add("데이터-"+i); // 큐에 데이터를 삽입한다. 
     //  queue = ["데이터-0", "데이터-1", "데이터-2"], front=0, rear=2
     
     System.out.println(queue.peek()); // 큐의 front가 가리키는 값을 반환한다. 
     System.out.println(queue.poll()); // 큐의 front가 가리키는 값을 반환하고 삭제한다. 
     System.out.println(queue.isEmpty()); //false
     System.out.println(queue);           // [데이터-1, 데이터-1]
  }
}
```


### 2. Stack 두개로  Queue 자료구조 구현하기 
```java
public class Queue {
  private Stack inBox = new Stack();
  private Stack outBox = new Stack();
  
  public voide enQueue(Object item) {
      inBox.add(item);
  }
  public Object deQueue() {
    if (outBox.isEmpty()){
      while(!inBox.isEmpty()){
        outBox.push(inBox.pop());
      }
    }
    return outBox.pop();
  } 
  public static void main(String[] args){
    Queue queue = new Queue();
    queue.enQueue("A");
    queue.enQueue("B");
    queue.enQueue("C");
    
    System.out.println(queue.deQueue());
    System.out.println(queue.deQueue());
    System.out.println(queue.deQueue());
  }
}
```
출력 결과: A, B, C






