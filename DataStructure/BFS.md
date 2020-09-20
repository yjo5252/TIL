# JAVA

### 1. 너비 우선 탐색
* Breadth Firsth Search (BFS)는 Queue로 구성한다.
* 그래프 내에 적은 숫자의 간선만을 갖니는 희소그래프(Sparse Graph)는 인접리스트를 사용하는 것이 유리하다. 

<b>1)ArrayDequeue로 Queue </b>

인접 행렬로 표현된 그래프의 너비우선탐색(BFS)의 시간 복잡도 : O(N+E)

```java
import java.util.ArrayDeque;
import java.util.ArrayList;

public class BreadthFirstSearch{
  // 정점의 개수 
  static int V = 5;
  
  // 인접리스트 
  static ArrayList<Integer> [] adjList = new ArrayList[V];
  
 public static void main(String[] args){
   adjList[0] = new ArrayList<>();
   adjList[0].add(1);
   adjList[0].add(2);
   
   adjList[1] = new ArrayList<>();
   adjList[1].add(0);
   adjList[1].add(2);
 
   adjList[2] = new ArrayList<>();
   adjList[2].add(0);
   adjList[2].add(1);
   adjList[2].add(3);
   adjList[2].add(4);
   
   adjList[3] = new ArrayList<>();
   adjList[3].add(2);
   
   adjList[4] = new ArrayList<>();
   adjList[4].add(2);
   
   bfs();
   
 }

 public static void bfs() {
   int node; 
   
    // 발견된 정점을 표시하는 배열  (초깃값: false)
   static int[] discovered = new int[V];
   static ArrayDeque<Integer> queue = new ArrayDeque<>();   // 발견 정점 큐 

   queue.add(0);  // 큐의 끝에 추가
   discovered[0] = 1;  // 발견 표시
   
   // 큐에서 꺼낸 노드와 인접한 노드들을 모두 차례로 방문한다. 
   while(queue.size()>0) {
     node = queue.pollFirst(); // 큐의 앞에서 방문할 노드 추출    
     System.out.println(node +1);
     if(adjList[node] != null) {
       for(int adjacent : adjList[node]){  // 인접정점들을 발견  
         if(discovered[adjacent] == 0){ // 이미 발견된 정점이 아니라면
            queue.add(adjacent); // 큐의 끝에 추가 
            discovered[adjacent] = 1; // 발견 표시
        }
      }
    }
  }
} 
 
}

```

<b> 2) LinkedList 로 Queue 구현 </b>

인접 리스트로 표현된 그래프의 너비 우선탐색(BFS)의 시간 복잡도 : O(N^2)

```java
import java.io.*;
import java.util.*;

/* 인접리스트를 이용한 방향성 있는 그래프 클래스 */
class Graph{
  private int V; // 노드 개수 
  private LinkedList<Integer> adj[]; // 인접 리스트 
  
  /* 생성자 */ 
  Graph(int v){
     V = v; 
     adj = new LinkedList[v];
     for (int i=0; i<v; ++i) // 인접 리스트 초기화 
        adj[i] = new LinkedList();
  }
  
  /* 노드를  연결 v -> w */
  void addEdge(int v, int w) {
     adj[v].add(w);
  }
  
  /* s를 시작 노드로 한 BFS로 탐색하면서 탐색한 노드들을 출력 */
  void BFS(int s) {
    // 노드의 방문 여부 판단 (초깃값: false)
    boolean visited[] = new boolean[V];
    // BFS 구현을 위한 큐 (Queue) 생성 
    LinkedList<Integer> queue = new LikedList<Integer>();
    
    // 현재 노드를 방문한 것으로 표시하고 큐에 삽입 (enqueue) 
    visited[s] = true;
    queue.add(s);
    
    // 큐(Queue)가 빌 때까지 반복 
    while(queue.size() != 0) {
      // 방문한 노드를 큐에서 추출 (dequeue)하고 값을 출력 
      s = queue.poll();
      System.out.println(s + " ");
    
      // 방문한 노드와 인접한 모든 노드를 가져온다. 
      Iterator<Integer> i = adj[s].listIterator();
      while(i.hasNext()){
        int n = i.next();
        // 방문하지 않은 노드면 방문한 것으로 표시하고 큐에 삽입(enqueue)
        if(!visited[n]){
          visited[n] = true;
          queue.add(n);
        }
      }
    }
  }
}
```

```java
// 사용 방법
public static void main(String[] args){
  Graph g = new Graph(4);
  
  g.addEdge(0,1);
  g.addEdge(0,2);
  g.addEdge(1,2);
  g.addEdge(2,0);
  g.addEdge(2,3);
  g.addEdge(3,3);
  
  g.BFS(2); // 주어진 노드를 시작으로 BFS 탐색 
}
```
