# JAVA

### 1. 인접행렬로 그래프 구현하기 
* 그래프에 간선이 많이 존재하는 밀집 그래프 
* 공간복잡도: O(V^2)
```java
/*
 * @ TITLE Adjacency Array (인접행렬)
 */
 
 // 그래프(행렬) 클래스 
 class ArrGraph {
    private int[][] arrGraph;
    
    // 그래프 초기화
    public ArrGraph(int initSize){
      this.arrGraph = new int[initSize+1][initSize+1];
    }
    
    // 그래프 return 
    public int[][] getGraph() {
      return this.arrGraph;
    }
    
    // 그래프 추가 (양방향) 
    public void put(int x, int y){
      arrGraph[x][y] = arrGraph[y][x] = 1;
    }
    
    // 그래프 추가 (단방향)
    public void putSingle(int x, int y){
      arrGraph[x][y] = 1;
    }
 
    // 그래프 출력 (인접행렬)
    public void printGraphtoAdjArr(){
      for(int i=0; i< arrGraph.length; i++){
        for(int j=0; j<arrGraph[i].length; j++){
           System.out.print("" + arrGraph[i][j]);
        }
        System.out.pringln();
      }
    }
 }
 ```
 ```java
public class AjacencyArray { 
   public static void main(String[] args){
     int initSize = 6;
     ArrGraph adjArr = new ArrGraph(initSize);
     
     adjArr.put(1,2);
     adjArr.put(1,3);
     adjArr.put(2,3);
     adjArr.put(2,4);
     adjArr.put(3,4);
     adjArr.put(3,5);
     adjArr.put(4,5);
     adjArr.put(4,6);
 
     adjArr.printGraphToAdjArr();
 }
```


### 2. 인접리스트로 그래프 구현하기 
* 그래프에 간선이 적게 존재하는 희소 그래프  
* 공간복잡도 O(V+E)
```java
import java.util.ArrayList;

// 그래프 (리스트) 클래스
class ListGraph{
  private ArrayList<ArrayList<Integer>> listGraph;
  
  // 그래프 초기화
  public ListGraph(int initSize){
    this.listGraph= new ArrayList<ArrayList<Integer>>(); //  그래프 생성
    
    for (int i=0; i< initSize+1; i++){
      listGraph.add(new ArrayList<Integer>());
    }
  }
  
  // 그래프 return 
  public ArrayList<ArrayList<Integer>> getGraph() {
    return this.listGraph;
  }
  
  // 그래프의 특정 노드 return 
  public ArrayList<Integer> getNode(int i) {
    return this.listGraph.get(i);
  }
  
  // 그래프 추가 (양방향 가중치)
  public void put (int x, int y, int w){
    // 1 대신 가중치 값 w (weight)를 설정함
    arrGraph[x][y] = arrGrapy[y][x] = w;
  }
  
  // 그래프 추가 (양방향)
  public void put (int x, int y) {
    listGraph.get(x).add(y);
    listGraph.get(y).add(x);
  }
  // 그래프 추가 (단방향)
  public void putSingle(int x, int y){
    listGraph.get(x).add(y);
  }
  // 그래프 출력 (인접리스트) 
 public void printGraphToAdjList() {
    for(int i=1; i<listGraph.size(); i++){
      System.out.print("정점 " + i + "의 인접리스트");
      
      for(int j=0; j<listGraph.get(i).size(); j++){
          System.out.print("->" + listGraph.get(i).get(j));
      }
      System.out.println();
    }
  }
}
```

```java
public class AdjacencyList {
  public static void main(String[] args){
      int initSize = 6; 
      ListGraph adjList = new ListGraph(initSize);
      
      adjList.put(1,2);
      adjList.put(1,3);
      adjList.put(2,3);
      adjList.put(2,4);
      adjList.put(3,4);
      adjList.put(3,5);
      adjList.put(4,4);
      adjList.put(4,6);
      
      adjList.printGraphToAdjList();
      /*
      * 정점 1의 인접리스트 -> 2 -> 3
      * 정점 2의 인접리스트 -> 1 -> 3 -> 4
      * 정점 3의 인접리스트 -> 1 -> 2 -> 4 -> 5
      * 정점 4의 인접리스트 -> 2 -> 3 -> 5 -> 6
      * 정점 5의 인접리스트 -> 3 -> 4
      * 정점 6의 인접리스트 -> 4
      */
  }
  
}
```

### 3. 깊이 우선 탐색 (DFS)
* Depth First Search (DFS)는 Stack으로 구성한다.

### 4. 너비 우선 탐색
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



### 5. Minimum Spanning Tree 
Minimum Spanning Tree: 그래프 G의 spanning tree 중 edge weight의 합이 최소인 spanning tree





