

### 문제 : 가중치가 있는 유향그래프

* 문제: 파일 입출력을 이용하여 정점과 엣지의 개수, 그리고 엣지와 해당 엣지의 가중치를 입력받아 <b> 가중치가 있는 유향그래프</b> 를 구성하여 출력하시오.
* 입력: 파일 입출력을 이용하여 파일의 첫 줄에는 정점의 개수와 엣지의 개수, 그 다음 줄부터는 입력된 엣지의 수만큼 한 줄에 엣지의 시작 정점, 엣지의 끝 정점, 엣지의 가중치가 입력된다.
* 출력: 입력된 정점과 엣지 정보를 이용하여 가중치 유형그래프를 출력하시오. 

* code 

#include <stdio.h> 
#include <stdlib.h>
#define MAX 1000

int main(void) {
    FILE *in = fopen("input.txt", "r");
    int vertex, edge, i, j, v1,v2, weight;
    int **matrix;
    
    fscanf(in, "%d", &vertex);
    fscanf(in, "%d", &edge);
    matrix = (int**) malloc(sizeof(int*)*vertex);
    
    for(i=0; i<vertex; i++){
        matrix[1] = (int*)malloc(sizeof(int)*vertex);
        for(j=0; j<vertex; j++) 
            matrix[i][j] = 0;
    }
    
    for(i=0; i<edge; i++){
        fscanf(in, "%d %d %d", &v1, &v2, &weight);
        matrix[v1-1][v2-1]= weight;
    }

    for(i=0; i<vertex; i++){
        for(j=0; j<vertex; j++){
            printf("%d ",  matrix[i][j]);
        }
        printf("\n");
    }
    for(i=0; i<vertex; i++){
        free(matrix[i]);
    }
    free(matrix);

    return 0;
}


### 가중치가 있는 유향그래프에서 제일 짧은 경로 구하기 
* 문제: 그래프의 정점, 엣지의 개수, 엣지를 입력받아 가중치가 있는 유향그래프를 구성하시오.
그리고 구성된 그래프를 이용하여 각 정점에서 가장 많은 정점을 거치며 제일 짧은 경로의 길이를 갖는 경로와 해당 경로의 비용을 출력하시오

* 입력: 파일입출력을 이용하여 파일의 첫째줄에는 정점의 개수와 엣지의 개수, 그 다음 줄부터는 입력된 엣지의 수만큼 엣지의 시작 정점과 끝 정점이 입력된다.
* 출력: 각 정점에서 가장 많은 정점을 거치며 비용이 제일 적은 경로의 path와 비용


#include <stdio.h>
#include <stdlib.h>
#define INF 100000
#define TRUE 1
#define FALSE 0

int isFinished(const int *visited, int n) {
    for (int i=0; i<n; i++){
        if(!visited[i])
            return FALSE;
    }
    return TRUE;
}

int getMin(int **matrix, int *visited, int n, int current){
    int min = INF, minindex= -1, weight=0;
    printf(" >> %d", current+1);
    visited[current]=TRUE;
    if(isFinished(visted, n)) return weight;
    
    for(int i=0; i<n; i++){
        if(!visited[i] && min > matrix[current][i]){
            min = matrix[current][i];
            minindex= i;
        }
    }
    if(minindex != INF && mindindex != -1){
        weight += min;
        weight += getMin(matrix, visited, n, mindindex);
    }
    return weight;
}



int main(void) {
    FILE *in =open("input.txt", "r");
    int vertex, edge, i, j, v1, v2, weight;
    int **matrix, *visited;

    fscanf(in, "%d", &vertex);
    fscanf(in, "%d", &edge);
    matrix = (int**)malloc(sizeof(int*)*vertex);
    visited = (int*)malloc(sizeof(int)*vertex);
    
    for(i=0; i<vertex; i++)[
        matrix[i]=(int*)malloc(sizeof(int)*vertex;
        for(j=0; j<vertex; j++){
            matrix[i][j]=INF;
        }
    }
    
    for(i=0; i<edge; i++){
        fsanf(in, "%d %d %d", &v1, &v2, &weight);
        matrix[v1-1][v2-1] = weight;
    }
    fclose(in);
    
    for(i=0; i<vertex; i++){
        int total=0;
        for(j=0; j<vertex; j++){
            visitd[j]=FALSE;
        }
        printf("%d path", i+1);
        total = getMin(matrix, visited, vertex, i);
        printf("\nminimumcycle length from %d vertex: %d:\n", i+1, total);
    }
    for(i=0; i<vertex; i++)
        free(matrix[i];
    free(matrix);
    
    return 0;
}



