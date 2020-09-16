# JAVA

1. 인접행렬로 그래프 구현하기 


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
  
  // 그래프 

}


2. 인접리스트로 그래프 구현하기 
