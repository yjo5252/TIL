## Graph 

### Overview 
* 그래프 
* 모든 정점 방문하기 
  * DFS
  * BFS
* 최소 신장트리 
  * 프림 알고리즘 
  * 크루스칼 알고리즘 
* 다익스트라 알고리즘: 하나의 정점에서 출발했을 때 다른 모든 정점의 최단 경로를 구하는 알고리즘 
* 플로이드 와샬 알고리즘: "모든" 정점에서 "모든" 정점"으로의 최단 경로를 구한다. 
                * '거쳐가는 정점'을 기준으로 알고리즘을 수행한다.
                * '현재까지 계산된 최소비용'을 테이블에 저장한다.


## 그래프 
* 'adjacent' = 간선을 두고 이어진 정점 
* adjacent matrix : adj[4][1] = 1 등 

* 4가지 
    * 무향 무가중치 
    * 무향 유가중지 
    : 가중치를 이용해 표현한 소셜 미디어 내 유저 간의 관계 
    * 유향 무가중치 
    * 유향 유가중치  
    : Default을 유향유가중치로 본다. 

* 그래프의 표현방법 
1. 인접행렬 
    * 간선의 수가 많은 경우     
``` 
adj[i1][i2]
```
    
2. 인접 리스트
    * 간선의 개수가 정점의 개수보다 많지 않은 경우 
```
adj = [[]]
adj[a].append((b,w))
adj[b].append((a,w))
```

## 모든 정점 방문하기 
* DFS : stack을 사용한다 => 재귀호출을 사용해도 된다. 
* BFS : queue을 사용한다 
```
queue.empty()
queue.put()
queue.get()
```
### 예제  
* 인접리스트로 구현
* DFS, BFS로 풀이 

```python
""" 
" -------------------------------------------------------------------------------------
"	Graph  - 섬의 개수
"   - in algo online class (zoom)
" 	- created at : 2021-07-14 
" -------------------------------------------------------------------------------------
"""

"""
입력예제 
6 8
01110000
01100110
01111011
00000011
01110110
01111110
"""

"""
풀이중 주의 
*  multi-list 행렬 입력받을 때 구현 방법 
    * 경계선 체크 #if (nc<0 or nc>=m)
    * or 경계선 바깥에 공간 추가 # (n+2, m+2)

"""
from queue import Queue 

# dfs 
#   M       [IN] map
#   r       [IN] start row
#   c       [IN] start column 
def dfs (M, r, c): 
    M[r][c] = 0
    dxy = { (0,1), (1,0), (0, -1), (-1, 0) }
    for (dr, dc) in dxy: 
        nr, nc = r + dr, c + dc 
        # boundary check 
        if nr < 0 or nr >= len(M): continue 
        if nc < 0 or nc >= len(M[0]) : continue 
        # check can go there
        if M[nr][nc] == 0: continue
        # recursive call 
        dfs (M, nr, nc)

#bfs
# 방문여부 반드시 check 
def bfs(M, r, c): 
    # make a queue
    q = Queue()
    q.put((r,c))
    # do for while queue is not empty
    while not q.empty():
        (r, c) = q.get()
        if M[nr][nc] == 0: continue
        dxy = { (0,1), (1,0), (0, -1), (-1, 0) }
        for (dr, dc) in dxy: 
            nr, nc = r + dr, c + dc 
            # boundary check 
            if nr < 0 or nr >= len(M): continue 
            if nc < 0 or nc >= len(M[0]) : continue 
            # check can go there
            if M[nr][nc] == 0: continue
            # recursive call 
            q.put((r,c))


n,m = map(int, input("n,m = ").split())
M = [ [0]*m for _ in range(n) ]  # make a multi-list sized nxm

for i in range(n): 
    s = input("")
    for j in range(m): 
        if s[j] == "1" : M[i][j] = 1

islands = 0
for i in range(n): 
    for j in range(m): 
        if M[i][j] == 0: continue
        islands += 1
        dfs(M, i, j)


```

-------------
## 최소신장 트리 
*  가중치가 있는 그래프에서 모든 정점을 방문하는 트리 중 최소의 가중치 합을 가지는 트리  
    * 프림 (Prim) 알고리즘 
    * 크루스칼 (Kruskal) 알고리즘 
#### BFS -> prim -> dijkstra -> a*

## 1. 프림 알고리즘 
* 정점과 간선에 값이 배정됨. 정점의 값이 작도록 간선을 연결시킴. 
* 구현 방법 기초. - 크루스칼 알고리즘에 응용 가능 
```python
# pseudo code 
def prim (V, E): 
    n = len(V)
    dist, visited =  [ infity ] * n,  [False] * n #?
    dist[0] = 0 
    pq.add(0, 0)        # 시작 지점을 입력한다. 
    while not pq.empty(): 
        u = pq.pop()
        visited[u] = True
        for e in E[u]: 
            if visited[e.to] == False and e.weight < dist[e.to]: 
                pq.add(e.to, dist[e.to] = e.weight)      # 정점 값을 weight으로 바꿔준다.
```
### 문제 풀이 코드 

```python
""" 
" -------------------------------------------------------------------------------------
"	MST - 최장 신장 트리 구하기 
"   - in algo online class (zoom)
" 	- created at : 2021-07-14 
" -------------------------------------------------------------------------------------
"""

"""
입력예제 
3 3 
1 2 1
2 3 2
1 3 3

답 
3
"""
# MST (Prim version)
from queue import PriorityQueue

Infinity = 1000000000

v, e = map(int, input().split())

# adjecent list 
adj = [ [] for _ in range(v) ]
for _ in range(e):
	a, b, w = map(int, input().split())
	# directed adjacent list
	adj[a-1].append((b-1, w))
	adj[b-1].append((a-1, w))

# Make a priority queue
pq = PriorityQueue()

# vertex values
d = [ Infinity ]*v

# visited or not
visit = [ False ]*v

# start vertex
d[0] = 0
pq.put((0, 0))			# first value : vertex value, second value : vertex index

# for queue is not empty
MST = 0
while not pq.empty():
	# get smallest priority from queue
	(_, u) = pq.get()
	if visit[u]: continue
	visit[u] = True
	MST += d[u]
	for (to, w) in adj[u]:
		if not visit[to] and d[to] > w:
			d[to] = w
			pq.put((d[to], to))

print(MST)
```

## 2. 크루스칼 알고리즘 
* 정점에 {} 집합이 있음. 작은 가중치부터 비교하면서.. 같은 집합이면 연결 불가능 
```python
def kruskal (V, E):
    E.sort()    # weight 값을 기준으로 정렬
    MST = [ ]
    for v in V:
        Set[v] = v  # 자기 자신을 가리키는 root
    for e in E: 
        if Set[e.from] == Set[e.to] : continue
        MST.add(e)
        Set[e.e] = Set[e.from]

    return MST
```
### 문제 풀이 
```python
""" 
" -------------------------------------------------------------------------------------
"	MST - 최장 신장 트리 구하기 
"   - in algo online class (zoom)
" 	- created at : 2021-07-14 
" -------------------------------------------------------------------------------------
"""

"""
입력예제 
3 3 
1 2 1
2 3 2
1 3 3
"""

# MST - Kruskal version
v, e = map(int, input().split())

def getRoot(S, k): 
    if k == S[k]: return k
    S[k] = getRoot(S[k], k)  # 축약과정을 거친게 while 루프보다 성능이 좋다.
    return k

# edge list 
E = []
for _ in range(e):
    a, b, w = map(int, input().split())
    E.append( (w, a-1, b-1) )           # w is first for sorting
E.sort()

# Make v sets for set operation
S = [ i for i in range(v) ]     # s = list (range(v))

MST = 0 
for (w, a, b) in E: 
    # get roots of a and b from sets
    ra = getRoot(S, a)
    rb = getRoot(S, b)
    # if set a and set b are same 
    if ra == rb: continue
    # union set a and set b 
    S[rb] = ra
    MST += w

print(MST)

```

* 시간 복잡도 
    * O((E + V) logV ) : 프림 알고리즘 -- edge 가 많은 경우
    * O(E(logE)) : 크루스칼 알고리즘 -- edge 가 적은 경우


### 예제 - 최단 경로 구하기 
* dijkstra 알고리즘 
* 문제 풀이 

```python 
""" 
" -------------------------------------------------------------------------------------
"	  - 최단 경로 구하기 
"   - in algo online class (zoom)
" 	- created at : 2021-07-14 
" -------------------------------------------------------------------------------------
"""

"""
입력예제 
5 6 1 
5 1 1 
1 2 2
1 3 3
2 3 4
2 4 5
3 4 6
"""

# 정점 개수, 간선 개수, 시작정점
# 간선들 정보 (시작점, 끝점, 가중치)
# 유향유가중치 그래프

# Dijkstra

from queue import PriorityQueue

Infinity = 1000000000

v, e, s = map(int, input().split())
# adjacent list
adj = [[] for _ in range(v)]
for _ in range(e): 
    a, b, w = map(int, input().split())
    # directed adjacent list 
    adj[a-1].append((b-1, w))


# Make a priority queue
pq = PriorityQueue()

# vertex values
d = [ Infinity ] * v

# visited or not 
visit = [ False ] * v

# start vertex
d[s-1] = 0
pq.put((0, s-1))      # first value: vertex value, second value: vertex index

# for queue is not empty 
while not pq.empty(): 
    # get smallest priority from queue
    (_, u) = pq.get()
    if visit[u]: continue
    visit[u] = True
    for (to, w) in adj[u]: 
        if not visit[to] and d[ to ] > d[u]+w :
            d[to] = d[u] + w
            pq.put((d[to], to))

print(d)
for t in d: 
    print(t if t != Infinity else "INF")

```

### 예제 - 하노이 타워 
```python 
""" 
" -------------------------------------------------------------------------------------
"	하노이탑 
"   - in algo online class (zoom)
" 	- created at : 2021-07-14 
" -------------------------------------------------------------------------------------
"""

"""
입력예제 

"""
# k 번째 움직인 원반은 몇번째로 작은 원반일까요? 
# 31개의 원반을 가진 하노이 탑에서 최소횟수로 원반을 옯깁니다. 

# 30개 옮김(1 - 30 번째 작음) # 1개 옮김 (31번째 작음) # 30개 옮김 (30-1번째 작음)
# 32 - 30, 33 - 29, 34 - 28, 61 - 1
def hanoi_me(k): 
    if k == 31: 
        return 31
    elif (k > 31): 
        return  k - (k-31)*2  
    else: 
        return k
move = 0
solve = -1
def hanoi(n, a, b, c):
    global move
    global k
    global solve 
    if n == 1: 
        r = a[1].pop()
        move += 1
        b[1].append(r)
        print("%20s: %s ==> %s (%d)"%(bin(move), a[0], b[0], r))
        if move == k : 
            print(r)
            return 0
        return 1
    r = hanoi(n-1, a, c, b)
    if r == 0: return 0
    r = hanoi(1, a, b, c)
    if r == 0: return 0
    hanoi(n-1, c, b, a)
    if r == 0 : return 0
    return 1

# stack 사용 
stack = [ 31-i for i in range(31) ]
k = int (input("k = "))
#hanoi(31, ("A", stack), ("B", []), ("C", []))
ans = hanoi_me(k)
print(ans)

```
