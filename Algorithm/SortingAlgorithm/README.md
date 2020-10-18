# 정렬 

### Sorting Algorithm
* Sorting 알고리즘은 크게 **Comparisons** 방식과 **Non-Comparisons** 방식으로 나눌 수 있다.

### Sorting Algorithm's Complexity 정리

|   Algorithm    | Space Complexity | (average) Time Complexity | (worst) Time Complexity |
| :------------: | :--------------: | :-----------------------: | :---------------------: |
|  Bubble sort   |       O(1)       |          O(n^2)           |         O(n^2)          |
| Selection sort |       O(1)       |          O(n^2)           |         O(n^2)          |
| Insertion sort |       O(1)       |          O(n^2)           |         O(n^2)          |
|   Merge sort   |       O(n)       |         O(nlogn)          |        O(nlogn)         |
|   Heap sort    |       O(1)       |         O(nlogn)          |        O(nlogn)         |
|   Quick sort   |       O(1)       |         O(nlogn)          |         O(n^2)          |
|   Count sort   |       O(n)       |           O(n)            |          O(n)           |
|   Radix sort   |       O(n)       |           O(n)            |          O(n)           |


* Comparisons Sorting Algorithm (비교 방식 알고리즘):<br>
`Bubble Sort`, `Selection Sort`, `Insertion Sort`, `Merge Sort`, `Heap Sort`, [Quick Sort](#Quick-Sort)

*  non-Comparisons Sorting Algorithm: <br>
`Counting Sort`, `Radix Sort` 

-----

# Quick Sort 
### 기본 컨셉 
1. <b> 분할 정복 (Divide and Conquer)</b> 전략과 <b>재귀 알고리즘</b>을 사용하는 정렬 기법이다. 
2. pivot 개념을 사용한다. 입력된 배열을 pivot 값 기준으로 더 작은 값과 큰 값으로 반복적으로 분할하여 정렬해나가는 방식을 취하고 있습니다.
3. 반복되는 partition 재귀 과정에서는 pivot으로 설정된 값을 포함시키지 않는다.
4. 파이썬의 list.sort() 함수나 자바의 Arrays.sort()처럼 프로그래밍 언어 차원에서 기본적으로 지원되는 내장 정렬 함수는 대부분은 퀵 정렬을 기본으로 합니다.

### Pivot 설정방법 
1. pivot을 각 원소와 비교. 첫번째 원소부터 시작.
2. 그 값이 pivot보다 작다면 그대로 둔다.
3. 그 값이 pivot보다 크다면 맨 마지막에서 그 앞의 원소와 자리를 바꿔준다. (k-1번째와 바꿔줌)
4. 이 과정을 반복한다. 
5. 작은 값들이 채워지는 인덱스를 가리키고 있는 값에 1을 더한 index 값과 pivot 값을 바꿔준다. 
(최종 pivot 의 인덱스는 i)


### 복잡도 
1. 최적의 시간복잡도: O(nlogn) / pivot 값을 기준으로 동일한 개수의 작은 값들과 큰 값들이 분할되는 경우.
2. 최악의 시간복잡도: O(N^2) / 한 편으로만 모든 값이 몰리게 되는 경우.
3. pivot 값 선택 기준: 중앙값(median)에 가까운 pivot 값, 배열의 첫값과 중앙값 그리고 마지막값 중에 크기가 중간인 값
4. 공간복잡도: O(1) / 입력 배열이 차지하는 메모리만을 사용하는 in-place sorting 방식

### 구현
1. pivot 값 선택 
1. 작은값, 동일한 값 큰 값 
1. 반복문 
1. 작은 값 배열 & 큰 값 배열 퀵정렬함수 재귀적으로 호출  
1. 마지막으로 재귀호출의 결과를 다시 크기 순으로 합침 



https://www.daleseo.com/sort-quick/
