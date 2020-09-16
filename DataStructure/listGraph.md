# JAVA

1. 인접행렬로 그래프 구현하기 
```java
/*
 * @ TITLE Adjacency Array (인접행렬)
 */
 
 // 그래프(행렬) 클래스 
 class ArrGraph {
    private
 
 }
```


2. 인접리스트로 그래프 구현하기 

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
