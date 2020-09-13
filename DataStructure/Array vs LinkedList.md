# Java로 구현

0. Array를 기반으로 한 ArrayList 구현
1) ArrayList 는 크기가 한정되어 있다. 
2) 삽입과정: 
- list의 크기를 삽입될 자료만큼 늘리는 연산을 수행한다. 
- 삽입될 자료의 위치를 기준으로 기존의 데이터들을 뒤로 혹은 앞으로 이동하는 연산을 수행한다. 
- 해당 위치에 자료를 입력한 후 삽입연산을 마친다. 
3) 삭제과정:
- 삭제될 자료가 위치한 인덱스의 자료를 삭제한다. 
- 삭제할 자료의 인덱스를 기준으로 이후의 자료들을 이동한느 연산을 수행한다. 
- list 맨 마지막은 비어있는 상태로 삭제를 완료한다.
4) 복잡도 
시작 O(n), 끝 O(1), 중간 O(n)


```java
package list;

public class MyArrayList {
    final static int MAX_SIZE = 100;
    private int[] data;
    int length;
    
    public MyArrayList() {
      super();
      this.length = 0;
      data = new int[MAX_SIZE];
    }
    public MyArrayList(int size){
        this.length = 0;
        data = new int[size];
    }
    /**
    * 배열의 마지막에 데이터를 추가한다. 
    * @param data
    */
    public void add(int data){
        int size = this.data.length;
        // 현재 배열의 길이와 사이즈가 같으면 사이즈를 증가시켜 새로운 배열에 복사한다. 
        if (this.length == size){
            copyArray(data, size);
        }else{
            this.data[this.length] = data;
        }
        //
        this.length++;
    }
    
     /**
      * 배열의 특정인덱스에 데이터를 추가한다.  
      * @param data
      */
    public void add(int index, int data){
        int size = this.data.length;
        // 현재 배열의 길이와 사이즈가 같으면 사이즈를 증가시켜 새로운 배열에 복사한다. 
        if(this.legnth == size){
            copyArrayWithIndex(index, data, size);
        } else{
            // 배열의 인덱스를 중심으로 뒤로 한칸씩 이동한다. 
            for (int i = this.length-1; i> index-1; i--){
              this.data[i+1] = this.data[i];
            }
            this.data[index-1] = data;
        }
        //
        this.length++;
    }
    
     /**
    * 배열의 마지막에 데이터를 삭제한다. 
    * @param data
    */
    public void remove() {
        if(this.legnth == 0){ throw new ArrayIndexOutOfBoundsException();}
        this.data[this.length-1] = 0;
        this.length--;
    }
    
     /**
    * 특정 인덱스의 데이터를 삭제한다. 
    * @param data
    */
    public void remove(int index) {
        if (this.length == 0 ) { throw new ArrayIndexOutOfBoundsException(); }
        this.data[index-1] = 0;
        // 삭제된 이후 데이터로 차례대로 채운다. 
        for(int i = index-1; i < this.length-1; i++){
            this.data[i] = this.data[i+1];
        }
        this.length==;
    }
    
     /**
    * 배열 복사 메소드. 
    * @param data
    * @param size
    */
    prvate void copyArray(int data, int size){
        int newSize = size + 1; 
        int[] newArray = new int[newSize];
        
        newArray[newSize-1] = data;
        
        for (int i = 0; i < size; i++){
            newArray[i] = this.data[i];
        }
        this.data = new int[newSize];
        
        for (int i = 0; i< newArray.length; i++){
            this.data[i] = newArray[i];
        }
        
    }
     /**
    * 특정 인덱스 배열복사메소드 
    * @param index
    * @param data
    * @param size
    */
    private void copyArrayWithIndex(int index, int data, int size){
        int newSize = size + 1; 
        int[] newArray = new int[newSize];
        newArray [index-1] = data;
        
        // 인덱스를 중심으로 이전 데이터 복사 
        for(int i = 0 ; i< index-1; i++){
            newArray[i] = this.data[i];
        }
        
        // 인덱스를 중심으로 이후 데이터 복사 
        for(int i = newSize-1; i> index-1; i--)[
            newArray[i] = this.daat[i-1];
        }
        
        this.data = new int[newSize];
        
        for(int i = 0; i< newArray.length; i++){
            this.data[i] = newArray[i];
        }
    }
    
    public int get(int index){
        return this.data[index];
    }
}

```

### LinkedList 
1) 데이터가 없는 시작노드를 가진다. 이 노드는 처음 노드가 추가될 대 다음의 노드를 가리키기만 한다. 
2) 각 노드는 재귀적으로 다음의 노드를 가지고 있다. 
3) 각 노드는 데이터를 가지고 있다. 
4) 추가, 삭제 기능이 있다. 
5) 노드의 구조
```java
class Node{
    private int data;
    prviate Node next;
    
    public Node(int data){
        this.data = data;
    }
}
```

1. Array 를 기반으로 한 Linked List 구현 


2. ArrayList를 기반으로 한 LinkedList 구현
