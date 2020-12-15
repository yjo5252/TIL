## BFS 
1. BFS 용도 : Root Node혹은 다른 임의의 노드에서 "인접한 노드를 먼저 탐색하는 방법 . 


2. BFS로 효과적으로 풀 수 있는 문제들이 있다.

3가지의 조건을 만족한다.

1. 최소 비용 문제

2. 간선의 가중치가 1이다.

3. 정점과 간선의 개수가 적다. (시간 제약, 메모리 제한 내에 만족한다.)


3. 
class Graph {
  private int V;
  private LinkedList<Integer> adj[];
 
  Graph(int v) {
    V = v;
    adj = new LinkedList[v];
    for (int i=0; i<v; ++i)
      adj[i] = new LinkedList();
  }
 
  void addEdge(int v, int w) { adj[v].add(w); }
 
  /* BFS */
  void BFS(int s) {
    boolean visited[] = new boolean[V];
    LinkedList<Integer> queue = new LinkedList<Integer>();
 
    visited[s] = true;
    queue.add(s);
 
    while (queue.size() != 0) {
      // 방문한 노드를 큐에서 추출(dequeue)하고 값을 출력
      s = queue.poll();
      System.out.print(s + " ");
 
      // 방문한 노드와 인접한 모든 노드를 가져온다.
      Iterator<Integer> i = adj[s].listIterator();
      while (i.hasNext()) {
        int n = i.next();
        // 방문하지 않은 노드면 방문한 것으로 표시하고 큐에 삽입(enqueue)
        if (!visited[n]) {
          visited[n] = true;
          queue.add(n);
        }
      }
    }
  }
}
