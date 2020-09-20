# Stack 

### 1. Stack 자료구조 구현하기 


### 2. arrayDequeue로 Stack 자료구조 구현하기 
```java 
import java.util.ArrayDeque;
Deque<Integer> deque = new ArrayDeque<>(8);
deque.push(5); //[5]
deque.push(4); //[5,4]
System.out.println(deque.pop()); // 4출력, [5] => Stack(LIFO)
deque.offerFirst(3); //[3,5] => DeQueue
deque.offerLast(6); //[3,5,6] => Queue
System.out.println(deque.pollFirst()); //3출력, [5,6] => Queue(FIFO)
```
