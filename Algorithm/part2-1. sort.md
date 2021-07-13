# 정렬 

### 구성 
* 기본정렬 
    * 선택 정렬
    * 삽입 정렬 
    * 버블 정렬 
* 고급 정렬
    * 힙정렬 
    * 합병정렬 
    * 퀵정렬 !! 

* 팁
    * __O(NlogN)__ vs O(N^2) 
    * 개념 + 구현 + 성능 테스트 

## 선택정렬 
* "알고리즘 이해에 편리/순차탐색의 기본단계"
* 조금씩 정렬된 범위를 늘린다. 
* 입력에 민감하지 않다. = 데이터에 위치 변환 적음. = 입력무관 항상 O(N^2)
* 실제 교환하는 데이터 횟수가 n-1번임

## 삽입정렬 
* "기본 정렬 중 1순위"
* 정렬이 이미 이루어진 리스트에 데이터가 추가되는 경우 유용하다. !!
* 입력 크기가 작은 경우에도 좋은 성능 
* 추가정보 
    * 커스터니안 Quastion 연산 
    * 매트릭스 matrix 연산 
    * 지금은, 계산을 다 GPU 에서 작업해 multiprocessing으로 프로세스 처리해서, 애니메이션 업데이트가 중요한 이슈는 아니다. 
* 매번 교환하는 횟수 (경향성이 없고 정렬이 안된 데이터의 경우 시간이 오래걸림) 
* <=> 반대로 경향성이 있는 정렬된 데이터는 시간이 훨씬 적게 걸림 : __O(n)__


## 버블정렬 
* "효율이 떨어져 사용이 힘들다"
* 인접한 쌍들을 비교한다.
* 순서대로 되어 있지 않으면 자리 바꾼다
* 입력에 민감하다 = 데이터 이동속도가 느리다 = 효율이 떨어진다. = 최선의 경우 O(N)



## 기본 정렬 구현 
### 선택정렬 구현 
```python
import time 
import random 
# 값 교체 편의성을 위해 '인덱스'를 지정해둔다.

def selectionSort(v):
    n = len(v) 
    for i in range(n-1):
        m = i 
        for j in range(i+1, n):
            if v[m] > v[j] : m = j
        v[m], v[i] = v[i], v[m]

n = int(input("n = "))
v = [ random.randrange(1000000) for _ in range(n)]

ts = time.time()  # 1970년 현재 시간을 second로 계산한다. [timestamp]
selectionSort(v)
et = int((time.time() - ts)*1000)  # selectionSort 수행 시간 + ms 로 변환 + 정수형 변환 
print(*v[:10])
print(f"Elapsed time is {et}ms.")

```
---------

## 분할정복 알고리즘 
* subproblem 의 해를 취합하여 원래 문제의 해를 구함 
* 예시1) 1 ~ n에 대해 sum(n)을 구하는 solution 함수. sum(n) = sum(n-1) + n
* 예시2) sum(a, b) 을 구하는 solution 함수. sumb(a,b) = sum(a,c) + sum(c+b) (c = (a+b)/2)

```
T(n) = T(A)+T(B) + O(f(n)) = 2T(A) 
```
### a T(n/b) 
* a = 2, b = 2 : 합병 정렬, 최근접 점의 쌍 찾기, 공제선 문제 
* a = 3, b = 2 : 큰 정수의 곱셈
* a = 4, b = 2 : 큰 정수의 곱셈
* a = 7, b = 2 : 스트라센(Strassen)의 행렬 곱셈 알고리즘 

## 고급문제 

## 합병정렬 (merge sort)
* "합병 정렬을 위해 분할 정복을 만들었다고 말할 정도."
* 예시1) 1724 6539 => 12345679

* 합병 정렬 시간 복잡도
* T(n) = 입력이 n인 데이터를 합병정렬로 정렬하는 시간 
    * T(n/2) = 분할된 입력을 정렬하는 시간 
    * O(n) = 분할된 두 데이터를 합병하는 데 걸리는 시간 
    * 결과: T(n) = O(nlon)
```
T(n) = 2T(n/2) + n
T(n) = nlogn
LHS = nlog2n
RHS = 2 (n/2logn/2) + n = n(logn - 1) + n = nlogn
```

### 합병정렬의 특징 
- __병렬처리__ 에 적용 가능 
    - = 멀티 프로세스나 분산처리에 유용 
    - 코어가 많은 경우 그걸 잘 분할해서 (코어 개수만큼 분할해서) 정렬해놓고 삽입 정렬 사용해도 될 정도로 정렬한다. 
- 디스크에서 읽는 시간은 메모리에서 읽는 시간의 몇 만 배이다. 
     - __외부 정렬__ 로 
     - 대규모 데이터를 정렬할 때 
     - 합병 정렬이 유리하다. 
- __정적 정렬__ 
    - 합병 정렬만 정적 정렬(static sort) 가능
- 자료구조가 __연결리스트__ 인 경우에 사용 가능 
    - 공간복잡도를 소모 안 한다. 
- 다만, 공간복잡도가 O(n)으로 다른 공갑정렬 O(1)에 비해 추가 공간이 필요하다. 

* 버블 정렬의 특징
  * O(nlogn)  
  * log 백만 = 20, 
  * 2천만 
### mergeSort 구현 
```python
import time
import random
# merge 함수는 temp 데이터가 필요함
# 참고)(performance 고려안함)
def merge(v, a, c, b):
	temp = []
	i, j = a, c+1
	while i <= c and j <= b:
		if v[i] <= v[j]:
			temp.append(v[i])
			i += 1
		else:
			temp.append(v[j])
			j += 1
	while i <= c:
		temp.append(v[i])
		i += 1
	while j <= b:
		temp.append(v[j])
		j += 1
	for i in range(len(temp)):
		v[a+i] = temp[i]

# 재귀함수는 탈출조건이 필요하다. 
# data 개수가 1개이면 정렬할 필요가 없다.
def mergeSort(v, a, b):
	if a == b: return
	c = (a+b)//2
	mergeSort(v, a, c)
	mergeSort(v, c+1, b)
	merge(v, a, c, b)

n = int(input("n = "))
v = [ random.randrange(100000000) for _ in range(n) ]

ts = time.time()
mergeSort(v, 0, n-1)
et = int((time.time() - ts)*1000)
print(*v[:10])
print(f"Elapsed time is {et}ms.")

```

## 퀵 정렬 
* 예제) 17249536 , 6을 기준.
    * 12453[6] 97 -> 12345[6]79
    * O(n) 시간 
* 퀵 정렬 시간 복잡도
    * 파티션 O(n) + 각 분할된 영역을 정렬하는 시간 T(n/2) 
    * T(n) = 2T(n/2) + O(n) 
    * 결과: T(n) = O(nlogn)
    * 분할된 영역이 한쪽으로 치우치게 되면 최악의 경우 T(n) = O(n^2)
```
T(n) = T(n-1) + n 
Sum(T(n) - T(n-1) = Sum(n)
T(n) - T(1) =  n (n+1)/2
T(n) = n^2

```
* 중앙값을 기준으로 정렬하면 3-pivot 
* 캐쉬 효율이 좋다. (고급 알고리즘)
* 일부 비재귀 처리로 평균 속도가 가장 빠르다.
### quickSort 구현 
```python
import time 
import random 

def partition(v, a, b): 
    pivot, i, j = v[b], a, b-1
    while i <= j: 
        if v[i] <= pivot: i += 1
        else: 
            v[i], v[j] = v[j], v[i] # 왜?
            j -= 1
    v[i], v[b] = pivot, v[i]
    return i 

# 탈출조건
# a = b  data 1개 
# a > b : data 0개 
def quickSort(v, a, b): 
    if a >= b : return 
    c = partition(v, a, b)
    quickSort(v, a, c-1)
    quickSort(v, c+1, b)


random.seed(100)
n = int(input("n = "))
v = [ random.randrange(100000000) for _ in range(n) ]

ts = time.time()  #  [timestamp]
quickSort(v, 0, n-1)
et = int((time.time() - ts)*1000)  # selectionSort 수행 시간 + ms 로 변환 + 정수형 변환 
print(*v[:10])
print(f"Elapsed time is {et}ms.")

ts = time.time()  #  [timestamp]
quickSort(v, 0, n-1)
et = int((time.time() - ts)*1000)  # selectionSort 수행 시간 + ms 로 변환 + 정수형 변환 
print(*v[:10])
print(f"Elapsed time is {et}ms.")
```

## 힙정렬

### 힙의 리스트 표현법 
* 꽉 찬 이진트리는 각각의 노드값이 바로 리스트값으로 표현할 수 있다. 
```
3
6 4
8 9 7 . 
```
```
A = [3, 6,4,8,9,7]
```
### 시간 복잡도 
* "힙정렬은 시간복잡도 측면에서 최상임."
* 입력이 n인 데이터를 힙 정렬로 정렬하는 시간을 T(n)이라고 했을 때, 
    * 힙을 만드는 시간복잡도 O(n)
    * 최소(최대)값을 가져오는 시간 복잡도 O(log*n) = O(logn)으로 표기.. 
    * 최소(최대)값을 가져오는 횟수 n-1
    * 결과: T(n) = O(n log*n)

### 힙정렬의 특징 
* 이론적으로 중복된 값이 없다고 가정한다. 
* 이론적으로 가장 빠른 시간 복잡도임. O(nlog*n) => O(log2n!)
* 캐시효율이 나쁨 


### heapSort 구현 
```python 
import time 
import random 
import heapq

random.seed(100)
n = int(input("n = "))
v = [ random.randrange(100000000) for _ in range(n) ]

ts = time.time()  #  [timestamp]
heapq.heapify(v)
v = [ heapq.heappop(v) for _ in range(len(v))]

et = int((time.time() - ts)*1000)  # selectionSort 수행 시간 + ms 로 변환 + 정수형 변환 
print(*v[:10])
print(f"Elapsed time is {et}ms.")
```



## 응용 예제 

### nth Element 
```python
# O(n) 알고리즘 
# heapq를 이용하면 O(nlogn) 이다. 안 좋은 알고리즘임. 

import time 
import random 
import heapq

def partition(v, a, b): 
    pivot, i, j = v[b], a, b-1
    while i <= j: 
        if v[i] <= pivot: i += 1
        else: 
            v[i], v[j] = v[j], v[i] # 왜?
            j -= 1
    v[i], v[b] = pivot, v[i]
    return i 

# 시간복잡도 O(n) 
# T(n) = T(n/2) + n
def nthElement(v, a, b, k): 
    if a >= b: return v[a]
    c = partition(v, a, b)
    if c == k: return v[c] # partition 에서 분할됨 O(n)
    if c > k: return nthElement(v, a, c-1, k)
    return nthElement(v, c+1, b, k)


random.seed(100)
n, k = map(int, input("n, k = ").split()) # 1000000 100 
v = [ random.randrange(100000000) for _ in range(n) ]


ts = time.time()  #  [timestamp]
#r = nthElement(v, 0, n-1, k) # 1000000 100 (278ms)
v.sort() # 내장함수 성능이 그다지 좋지 않아; # 1000000 100  (285ms)
r = v[k]
et = int((time.time() - ts)*1000)  # selectionSort 수행 시간 + ms 로 변환 + 정수형 변환 
print(*v[:10])
print(f"Elapsed time is {et}ms.")
```
