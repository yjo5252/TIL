# JAVA
- Heap는 배열에 기반한 `Complete Binary Tree`이다. 
- 배열에 트리의 값을 넣어줄 때 1번 인덱스부터 루트노드가 시작된다. (노드의 고유번호 값과 배열의 index를 일치시켜 혼동을 줄이기 위해)
- `Max Heap`은 각 노드의 값이 해당 children 의 값보다 크거나 같은 Complete Binary Tree를 발한다. 
- `Max Heap`에서는 최대값을 찾는데 소요되는 연산의 시간복잡도가 O(1)이다. 
- `Max Heap`에서 루트 노드를 삭제했을 경우, 구조를 계속 유지하기 위해서는 맨 마지막 노드를 제거된 루트 노드로 대체시킨 후, heapify 과정을 거쳐 heap 구조를 유지한ㄷ.ㅏ 
이 경우 최대값은 시간복잡도 O(log n)으로 접근할 수 있다. 

### Queue를 사용하여 Heap 자료구조 구현하기 
```java


```

### Heapify 구현하기 


### Max Heap 삽입, 삭제, 연산
```Java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.ArrayList;

public class MaxHeap {
  public static class maxHeap {
    private ArrayList<Integer> heap;
    public maxHeap(){
      heap = new ArrayList<>();
      heap.add(1000000); // 인덱스 1부터 시작하기 위함
    }
    public void insert(int val){
      heap.add(val);
      int p = heap.size() - 1;
      // 루트까지 이동, 자식노드가 더 크면 swap 
      while(p > 1 && heap.get(p / 2) < heap.get(p){
        int temp = heap.get(p / 2);
        heap.set(p / 2, heap.get(p);
        heap.set(p, temp);
        p = p / 2;
      }
    }
    
    public void delete(){
      if(heap.size()-1 < 1){
        return 0;
      }
      
      int deleteItem = heap.get(1);
      
      heap.set(1, heap.get(heap.size()-1));
      heap.remove(heap.size()-1);
      
      int pos = 1;
      while((pos * 2) < heap.size()) {
        int max = heap.get(pos * 2);
        int maxPos = pos * 2;
        
        if(((pos*2+1) <heap.size()) && max < heap.get(pos*2+1)){
          max = heap.get(pos*2+1);
          maxPos = pos*2+1;
        }
        
        if(heap.get(pos) > max){
          break;
        }
      
        int temp = heap.get(pos);
        heap.set(pos, heap.get(maxPos));
        heap.set(maxPos, temp);
        pos = maxPos;
      }
      return deleteItem;
    }
  }
  public static void main(String[] args) throws Exception{
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    
    int N = Integer.parseInt(br.readLine());
    
    maxHeap heap = new maxHeap();
    
    for (int i = 0; i < N; i++){
        int val = Integer.parseInt(br.readLine());
        
        if(val ==0){
          System.out.println(hap.delete());
        }else{
          heap.insert(val);
        }
    }
  }
}
```

### Mean Heap 삽입, 삭제, 연산 
```Java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.ArrayList;

public class MinHeap{
  public static class minHeap{
    private ArrayList<Integer> heap;
    
    // 힙 생성자 
    public minHeap() {
      heap = new ArrayList<>();
      heap.add(0); // 인덱스 0 채우기 (1부터 채우기 위함)
    }
    
    // 삽입
    public void insert(int val) {
      heap.add(val);
      int p = heap.size() - 1;
      
      // (힙 사이즈 -1)이 1보다 작아질 때까지 진행 -> root으로 이동
      while(p > 1 && heap.get(p / 2) > heap.get(p)){
        System.out.println("Swap");
        // 부모보다 자식 노드가 더 작으면 바뀌어야 함 (최소힙)
        int tmp = heap.get(p/2);
        heap.set(p/2,heap.get(p));
        heap.set(p, tmp);
        
        p = p/2; // p는 부모 값으로 변경 (부모 노드 인덱스로 이동) 
      }
    }
    // 삭제
    public int delete{
      // (힙 사이즈 -1)이 1보다 작으면 0 리턴 
      if (heap.size()-1 < 1){
        return 0;
      }
      
      //  삭제할 노드는 루트 노드임 
      int deleteItem = heap.get(1);
      
      // root에 가장 마지막 값 넣고 마지막 값 삭제
      heap.set(1, heap.get(heap.size() -1));
      heap.remove(heap.size()-1);
      
      int pos = 1;
      while((pos * 2) < heap.size()){
        int min = heap.get(pos * 2);
        int minPos = pos * 2;
        
        if((pos * 2 + 1) < heap.size()) && min > heap.get(pos * 2 + 1) {
            min = heap.get(pos * 2 + 1);
            minPos = pos * 2 + 1;
        }
        if(heap.get(pos) < min) break;
        
        // 부모 자식 노드 교환
        int tmp = heap.get(pos);
        heap.set(pos, heap.get(minPos);
        heap.set(minPos, tmp);
        pos = minPos;
      }
      return deleteItem;
    }
  }
  
  public static void main(String[] args) throws Exception {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    int N = Integer.parseInt(br.readLine());
    minHeap heap = new minHeap();
    for (int i = 0; i < N; i++){
      int val = Integer.parseInt(br.readLine);
      
      if(val == 0){
        System.out.println(heap.delete());
      } else{
        heap.insert(val);
      }
    }
  }
}
```
