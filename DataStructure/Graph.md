

### 문제 : 가중치가 있는 유향그래프

: 파일 입출력을 이용하여 정점과 엣지의 개수, 그리고 엣지와 해당 엣지의 가중치를 입력받아 <b> 가중치가 있는 유향그래프</b> 를 구성하여 출력하시오.
* 입력: 파일 입출력을 이용하여 파일의 첫 줄에는 정점의 개수와 엣지의 개수, 그 다음 줄부터는 입력된 엣지의 수만큼 한 줄에 엣지의 시작 정점, 엣지의 끝 정점, 엣지의 가중치가 입력된다.
* 출력: 입력된 정점과 엣지 정보를 이용하여 가중치 유형그래프를 출력하시오. 

* code 

#include <stdio.h> 
#include <stdlib.h>
#define MAX 1000

int main(void) {
    FILE *in = fopen("input.txt", "r");
    int vertex, edge, v1,v2, i, j;
    int **matrix;
    
    fscanf(in, "%d", &vertex);
    fscanf(in, "%d", &edge);
    matrix = (int**) malloc(sizeof(int*)*vertex);
    
    for (i=0; i<vertex; i++){
        fscanf(in, "%d %d", &v1, &v2);
        
    
    }







}
