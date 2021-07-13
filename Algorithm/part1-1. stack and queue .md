# list 

*  list 자료구조는 "순서를 지킨다" -- 자료구조의 역할론
* list은 동적으로 할당이 되어있고 + 동적으로 추가/삭제하고 
* 맨 뒤에 추가 시 상수 시간이지만, 그 외에는 O(n) 이다. 


### list([]) append()
```python
>>> list = [x, y, z, ...]
>>> list.append(r) 
>>> list
[x, y, z, ..., r]
```

### list 추가 함수 append(...)
```python
codes = [] # empty list
for i in range(1, 101, 2):
    codes.append(i)
print(codes)
```
### list network 
* this is more advanced and recommended version than the previous algo.
```python
codes = [i for i in range(1, 101, 2)]
```
### list([]) insert(index, data-structre)
* downfall : O(n) 시간 복잡도
```python
>>>list = [ ..., x, y, z, ...]
>>>list.insert(index, r)
>>>list 
[ ..., x, r, y, z, ...] 
```

### 맨 앞에 추가하는 경우 
* downfall: O(k*n) --> 차라리 다른 자료구조 또는 insert() 메소드를 사용해라.
```python
list = [ x, y, z, ... ]
list = [ r ] + list 
list => [r, x, y, z, ...]
```
### list 삭제 함수 delete(...)
```python
>>>list = [ ..., x, y, z, ...] # index 위치의 항목이 y 인 경우 
>>>del(list[index])
>>>list 
[ ..., x, z, ... ]
```
*  remove로 지우는 경우와 다름
```python
>>>list = [ ..., y, ..., x, y, z, ...] # index 위치의 항목이 두번째 y인 경우 
>>>list.remove(list[index])
>>>list 
[..., x, y, z, ...]
```

### 리스트 내포 
* for 반복문을 통해서 리스트를 추가하는 방법을 간단하게 처리한다. 
```python
list = []
for k in range(1,11):
    list.append( k )
list     # [ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

list = [ k for k in range(1, 11)]
list    # [ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```
### 중첩된 for 반복문에 대한 리스트 내포 
```
[ <수식문> for <반복자1> in <반복객체1> if <반복조건1>
         for <반복자1> in <반복객체1> if <반복조건1> 
         ...
         for <반복자1> in <반복객체1> if <반복조건1>
]
```
------------
# stack 
* stack은 알고리즘에서 사용 빈도가 가장 많은 자료구조이다. 
* 함수의 재귀호출로 대신한다. 

### case 1 : stack이라는 이름의 리스트로 구현하는 경우 

1. `push` 기능 : stack.append(<new item>)
2. `pop` 기능 : stack.pop()
3. `top` 기능 : stack[-1]
4. `empty` 기능 : len(stack) == 0

### case 2: queue이라는 이름의 자료구조로 구현하는 경우 
* 문제유형
  1. 시뮬레이션(줄서기) - 관공서, 은행, 우체국, 병원 
  2. 그래프 이론 - 우선순위큐 
* 구현 
  1. `add` 기능: queue.append(<new item>)
  2. `pop` 기능: queue.pop(0)
  3. `front` 기능: queue[0]
  4. `empty` 기능: len(queue) == 0


### case 3: queue
* 구현 가능하다. but 이러면 에러가 뜬다.  비추천. 
-----------
## 후위연산자  - stack 응용

### 중위표현식 -> 후위표현식 알고리즘 설계 
1. 피연산자면 출력 
2. '('이면 스택에 push 
3. ')'이면 '('이 나올 때까지 스택에서 pop, 출력
4. 연산자이면 스택에서 이보다 높은 우선순위 것들을 pop + 출력, 연산자는 스택에 push 
5. 스택에 남아 있는 연산자는 모두 pop + 출력

* 후위연산자로 변환하면 개발하기 편하다. 
* 연산자 우선순위, ( ) 고려 안해도 되기 때문이다. 


### 보충 설명 

* 예제 1) 
```
2 + (3 + 2) x 3
** 연산자 우선순위 3 1 2 
2 3 2 + 3 x + 
```
* 예제 2) 
```
3 * (2 + 7) ==> 3 3 7 + * 
3 * 2 + 7 ==> 3 2 * 7 + 
(2 + 3 ) x (3 - 1) ==> 2 3 + 3 1 - * 
```

### 후위연산자 계산 
* 중위연산자를 후위연산자로 변환하는 경우 
* 문자열이 모두 붙어 있는 경우 = parsing을 해줘야함

```python
# 후위연산자 
exprs = input("Enter the expression: ").split() # 입력 처리 (return list)

# 스택을  생성합니다. (파이썬에서는 리스트로 사용해도 ok)
stack = [ ] 

# express 리스트에서
for e in exprs: 
    if e == '+' or e == '-' or e == '*' or e == '/':
        opr2 = stack.pop()
        opr1 = stack.pop()
        if e == '+': r = opr1 + opr2
        elif e == '-': r = opr1 - opr2 
        elif e == '*': r = opr1 * opr2
        elif e == '/': r = opr1 / opr2
        stack.append(r)
    else: 
        # put number into stack 
        stack.append(float(e)) # change string into number

print(stack[0])
```


### 가장 큰 숫자 구하기 
```python
# 가장 큰 숫자 구하기 
# 길이 n 인 문자열 
# k = 지워야 하는 작은 값의 개수 

"""
1. k = 지워야 하는 작은 값의 개수  
2. 입력하려는 값과 마지막 입력값 pop해서 비교, 작은 것 지우고, 나머지 push, k 하나 감소 
3. 나머지 stack 에 입력

"""

n, k = map(int, input().split()) #"Enter the numbers: "
numbers = input()

# make a stack 
stack = [ ]

n -= k
for c in numbers:     
    # conditions to be able to 'pop' : 1. stack is not empty 2. stack's last value is smaller than c 
    while len(stack) > 0 and k > 0 and stack[-1] < c: 
        stack.pop()
        k -= 1
    stack.append(c)

print(''.join(stack[:n]))

```

### 요세푸스 문제 풀기 
* 문제 설명 
  * 1번 ~ n번 까지 숫자를 원형으로 나열함. 
  * k 번째 숫자를 하나씩 뽑아서 만드는 수열 
  * (n, k)
  * solution: 최종 생존자? 죽는 순서? 

* 문제풀이 
```python
"""
1. 1부터 n까지의 숫자를 큐에 넣는다.
2. K-1개의 숫자를 큐에서 제거하고 다시 큐에 넣는다. 
3. 큐에서 하나의 숫자를 꺼내고 그 숫자를 출력한다. 
4. 큐가 비어있다면 종료, 그렇지 않다면 다시 b 로 돌아간다.

"""

# use list for queue (performance is not good)
n, k = map(int, input().split())

queue = [i for i in range(1, n+1)]
while len(queue) > 0: 
    # k-1 pop and push 
    for _ in range(k-1):
        queue.append(queue.pop(0))
    # print popped item
    print(queue.pop(0))
```
