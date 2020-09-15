# Tree


## Binary Search Tree 구현하기 
이진탐색트리는 데이터를 저장하고 특정 데이터의 위치를 찾을 수 있는 이진트리의 일종이다.
1) 이진 탐색 트리의 노드에 저장된 키는 유일하다. 
2) 루트 노드의 키가 왼쪽 서브 트리를 구성하는 어떠한 노드의 키보다 크다. 
3) 루트 노드의 키가 오른쪽 서브 트리를 구성하는 어떠한 노드의 키보다 작다. 
4) 왼쪽과 오른쪽 서브트리도 이진 탐색 트리이다. 

저장 순서에 따라 계속 한 쪽으로만 노드가 추가되는 경우가 발생하기 때문이다. 


```java
import java.util.LinkedList;
import java.util.Queue;

public class BinarySearchTree {
    private Node root;
    
    private class Node{
        int key;
        
        Node leftChild;
        Node rightChild;
        
        Node(int key) {
          this.key = key;
        }
        
        public String toString(){
            return "key:" + this.key;
        }
    }
    
    public String toString(){
        return "key:" + this.key;
    }
}

public Node getRoot(){
    return this.root;
}


public void addNode(int key){
    if (findNode(key) != null) return;
    
    Node newNode = new Node(key);
    
    if(root == null){
        root = newNode; // 트리가 비어있으면 root에 삽입
    } else{
        Node focusNode = root; // 탐색용 노드
        Node parent;           // 탐색용 노드의 부모 노드 
        
        while(true){
            parent = focusNode; // 이동
            
            if (key < parent.key){             // 삽입하려는 키가 현재 노드보다 작으면
                focusNode = parent.leftChild;  // 왼쪽으로 이동
            
                if (focusNode == null) {       // 왼쪽 노드가 비어있으면
                    parent.leftChild = newNode;// 왼쪽 노드에 삽입
                    return
                }
            } else{                             // 삽입하려는 키가 현재 노드보다 크면
                 focusNode = parent.rightChild; //오른쪽으로 이동
                 
                 if(focusNode == null){         // 오른쪽 노드가 비어있으면
                    parent.rightChild = newNode;// 오른쪽 노드에 삽입
                    return;
                 }
            }
        }
    }
}

public boolean deleteNode(int key){
      // focusNode와 parent가 같을 수 있는 경우는 찾으려는 key가 root인 경우 
      Node focusNode = root;
      Node parent = root;
      boolean isLeftChild = true;
      
      // while 문이 끝나고 나면 focusNode는 삭제될 노드를 가리키고, parent는 삭제될 노드의 부모노드를 가리키게 되고, 
      // 삭제될 노드의 부모노드의 left 인지 right인지 에 대한 정보를 가지게 된다.
      while(focusNode.key != key){
            parent = focusNode;
            
            if(key < focusNode.key){
                isLeftChild = true;   // 지우려는 노드가 왼쪽에 있는 노드나 기록용
                focusNode = parent.leftChild;
            } else{
                isLeftChild = false;
                focusNode = parent.rightChild;
            }
        //찾으려는 노드가 없는 경우 
        if(focusNode == null) {
              return false;
        }
      }
      
      
      Node replacementNode;
      // 지우려는 노드의 자식 노드가 없는 경우 
      if(focusNode.leftChild == null && focusNode.rightChild == null){
          if(focusNode == root)
              root = null;
          else if(isLeftChild)
              parent.leftChild = null;
          else
              parent.rightChild = null;
      }
      
      // 지우려는 노드의 오른족 자식노드가 없는 경우(왼쪽 자식노드만 있는 경우)
      else if(focusNode.rightChild == null){
          replacementNode = focusNode.leftChild;

          if(focusNode == root)
              root = replacementNode;
           else if(isLeftChild);
              parent leftChild = replacementNode;
           else
              parent.rightChild = replacementNode; 
      }
      //  지우려는 노드의 왼쪽 자식노드가 없는 경우 (오른쪽 자식 노드만 있는 경우)
      else if(focusNode.leftChildNode == null){
            replacementNode = focusNode.rightNode;
            
            if(focusNode == root)
                root = replacementNode;
            else if(isLeftChild)
                parent.leftChild = replacementNode;
            else 
                parent.rightChild = replacementNode;
      }
      // 지우려는 노드의 양쪽 자식노드가 모두 있는 경우 
      // 오른쪽 자식 노드의 sub tree에서 가장 작은 노드를 찾아서 지우려는 노드가 있던 자리에 위치시킨다. 
      else{
            Node rightSutbTree = focusNode.rightChild;    // 삭제될 노드의 오른쪽 sub tree를 저장해둔다. 
            replacementNode = getRightNode(focusNode.rightChild); 
            
            if (focusNode == root)
                root = replacementNode;
            else if (isLeftChild)
                parent.leftChild = replacementNode;
            else
                parent.rightChild = replacementNode;
                
            replacementNode.rightChild = rightSubTree;
            if(replacementNode == rightSubTree)   // 지우려는 노드의 오른쪽 subtree에 노드가 하나밖에 없는 경우
               replacementNode.rightChild = null;
               
            replacementNode.leftChild = focusNode.leftChild;  // 지우려는 노드의 왼쪽 sub tree를 연결시킨다. 
      }
}


}
```

## 주어진 트리가 Binary 트리인지 확인하는 알고리즘 구현하기 


