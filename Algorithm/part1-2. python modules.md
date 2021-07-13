# python module 
* 모듈명: random, os, re, ...
* 함수명 

```python
import <모듈명>
<모듈명>.<함수명>(...)

from <모듈명> import <함수명1>, <함수명2>, ...
<함수명2>(...)

from <모듈명> import * 
<함수명3>(...)

```

## 모듈 만들기
* 파일에 실행되는 명령문이 없도록 작성 
* if __ name __ == "__ main __": 을 이용해서 해당 명령문을 격리한다. 
    * __ main __ 메소드는 script로 실행할 때만 작동한다. 

## itertools 
* permutation, combination 등 '나열형 반복함수' 
* 반복함수로 처리 
```python
def mul2o3(n):
    for i in range(1, n+1):
        if i%2==0 or i%3==0: yield i
n = int(input("n=="))
sum = 0
for k in range(n): 
    sum += k 
print(sum)

```

1. `product(p, q)`: p, q의 아이템을 카테시안 곱을 수행한다.
2. `accumulate(p)`: p에 있는 아이템을 차례대로 더한다.
3. `permutations(p[, r])`: p에 있는 아이템을 r길이만큼 순열
4. `combinations (p, r)` p에 있는 아이템을 r만큼 조합 

```python
from itertools import combinations 
friends = ['홍', '성', '이']
for k in combinations(friends, 2): 
    print(k) 
('홍' '성')
('홍' '이')
('성' '이')
```
## random 
* 난수를 발생시켜서 시뮬레이션, 테스트에서 사용된다. 
* `randrange(stop)`: 0 ~ stop-1 수를 발생 
* `randrange(start, stop[, step])`: start - stop-1 수를 발생시킨다 (step 지정되면 건너뛴 수는 발생 안한다.)
* `choice(list)`: list에서 한 개를 임의로 선택 
* `shuffle(list)`: lsit에 있는 아이템들을 임의로 섞음 (튜플, 문자열에서 허용 안됨)

```python
import random 
x = [random.radnrange(1, 101) for _ in range(10)]
print(x)

```

## heapq 
* 최소힙(minheap)만 을 사용할 수 있게 제공한다.
* list 자료구조를 이용해 구현한다. 
* 최대힙(maxheap)은 heapq를 응용 혹은 직접 구현.

* `heapify(list)`: list을 힙 구조로 생성 
* `heappush(heap, x)`: heap에 x 아이템을 추가 
* `heappop(heap)` : heap에서 가장 작은 아이템을 가져온다. 

```python
import heapq

h = list(map(int, input("숫자입력: ").split()))
heapq.heapify(h) # O(N)
print([heapq.heappop(h) for _ in range(len(h)) ]) # O(logN) O(Nlogn) ==> O(N(logN+1)) = O(Nlog2N)
```

## bisect 
* binary + 
* 이미 정렬된 리스트에서 원하는 아이템을 끼어넣기 할 위치를 이진탐색으로 찾는다. 
    * `bisect_left(list, x)` : list에서 x 를 끼어넣어야할 위치를 왼쪽에서 찾는다. 
    * `bisect_right(list, x)`: list에서 x 를 끼어넣어야할 위치를 왼쪽에서 찾는다. 
    * x의 값과 같은 값이 list에 존재하지 않는다면 같은 결과를 반환한다. !!

```python
from bisect import *
a = [1, 2, 2, 4, 5]
print(bisect_left(3)) # 3
print(bisect_right(3)) # 3
print(bisect_left(4)) # 3
print(bisect_right(4)) # 4

```


## queue 
* queue는 큐 자료구조를 따로 구현한다. 
* 일반 큐, 우선순위큐, 큐, LIFO 큐 
  * `qsize()`: 큐에 들어있는 아이템의 개수 출력 
  * `empty()`:  큐가 비어있는 경우 Tre 반환
  * `put(item)`: 큐에 item 추가 
  * `get()` : 큐에서 item을 제거하고 해당 item 반환 

``` python
import queue
q = queue.Queue()
q.put(10)
q.put(20)
println(q.get()) #10
println(q.empty()) #False
println(q.get()) #20
println(q.empty())#True

```


------------
* 2021.7.12 (monday)
* 알고리즘 코딩테스트 교육 day 1
