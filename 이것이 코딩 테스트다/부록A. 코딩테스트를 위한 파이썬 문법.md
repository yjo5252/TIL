# 부록 A 코딩 테스트를 위한 파이썬 문법 

## 01.자료형 

#### 1. 수자료형
* 정수, 실수, round(), 연산 (%, //, **) 
#### 2. 리스트 자료형
  * 0으로 초기화한느 코드 [0] * n
  * 인덱싱 [], 슬라이싱 [ : 마지막 인덱스-1]
  * 리스트 컴프리헨션 : 반복문 + 조건문
  * insert() 메서드 : O(1)
  * append() 메서드 : O(1)
  * remove 메서드 : O(N)
  * remove all: set {}에 제외할 원소 정의하고, 리스트 컴프리헨션 조건문에 not 사용해서 제외시킨다.
#### 3. 문자열 자료형
* "", '', 백슬래시 (/), 연산 (덧셈 +), 인덱싱, 슬라이싱
#### 4. 튜플 자료형
* 소괄호(), 내용 변경 불가
* 그래프 알고리즘, 우선순위 큐
#### 5. 사전 자료형
  * " " : " "
  * 검색, 수정, O(1), 
  * 찾고 있는 데이터가 있는 지 파악하는 법: 원소 in 사전 형태
  * keys(), values() : 리스트형 반환
#### 6. 집합 자료형
* set 함수 초기화 
  * 중괄호 {} 콤마 ,  update more
  * 학생번호가 선택되었는 지 확인
  * 집합 자료형 연산: 합집합 (|) 교집합 (&) 차집합 (-) 


## 02. 조건문 

#### 0. 활용
* 리스트에 있는 원소의 값을 또다른 리스트로 만든다
```python
# 리스트 컴프리헨션, 조건문 사용
a = [1, 2, 3, 4, 5, 5, 5]
remove_set={3,5}

result = [i for i in a if not in remove_set]

print(result) # [1, 2, 4]
```
#### 1. 조건에 따라 로직 설명
#### 2. if (elif) (else) 
#### 3. 코드의 들여쓰기
* 파이썬 커뮤니티 표준은 4개의 공백문자를 사용하는 것 '    '
#### 4. 비교연산자
* != == < > <= >=
* True/False 반환
* 파이썬에서는  x > 0 and x < 20 와 0 < x < 20 로 표현할 수 있다.

#### 5. 논리연산자 
* and or not 
* True/False 반환

#### 6. 파이썬의 기타 연산자
* 데이터 담는 자료형: 리스트, 튜플, 문자열, 사전 
* ex) 
  * x in 리스트 
  * x in 문자열 
  * x not in 리스트 

### 03. 반복문 

#### 1. while 문 
* 무한 루프 조심
* 홀수만 더하고자 할 때 어떻게 할 수 있을까?
  * 조건문 만족할 때 변수 result에 더함 
  
  
#### 2. for 문
* for (변수) in (리스트)
* continue 사용 => 특정 조건 제외 
  * 예제: 블랙리스트는 점수가 높아도 합격할 수 없다. 
* 2중 중첩 반복문 for for
  * 플로이드 뒤셜 (**)
  * 다이나믹 프로그래밍 (**)

## 04. 함수
#### 1. 동일한 알고리즘 사용 시 유용하다. 
#### 2. return, print() 
#### 3. 인자를 넘겨줄 때 파라미터의 변수를 직접 지정해서 값을 넣어줄 수 있다. 
``` python
def add(a,b):
    print('함수의 결과:', a+b)
add(b = 3, a = 7) # 함수의 결과: 10
```
#### 4.  함수 밖에 있는 변수 데이터를 변경해야 하는 경우, global 키워드를 사용한다. 
```python
a = 0 
def func(): 
    global a
    a +=1
for i in range(10): 
    func()
print(a)
```
#### 5. 람다 표현식 (Lambda Express)
    * 간단한 함수를 한 줄에 정의해야 할 때 효과적으로 사용할 수 있다. 
    * 파이썬의 정렬 라이브러리를 사용할 때 람다식은 정렬 기준(Key)를 설정할 때 사용된다. (**)
    ```python
    print((lambda a, b: a+b) (3,7)) # 10    
    ```
    
## 05. 입출력 
#### 1. 입력 input() 
* 한 줄의 <b>문자열</b>을 입력받도록 해줌
* 정수형 데이터로 처리하려면 문자열을 정수로 바꾸는 int() 함수 사용
     * int(input())
     
#### 2. 입력을 위한 전형적인 소스코드 
* 입력 데이터 구성 
   * <1> 데이터의 개수 
   * <2> 처리할 데이터는 그 다음에 주어진다
* 공백으로 구분되는 데이터를 각각 정수형 자료로 저장하는 코드 
```python
# 데이터의 개수 입력
n = int(input())

# 각 데이터를 공백으로 구분하여 입력
data = list(map(int, input.split()))
    
data.sort(reverse = True) # 내림차순으로 정렬
print(data) # [99, 90, 75, 65, 34]
```

#### 3. 많은 수의 데이터가 연속적으로 입력된다 
* ex) 정렬, 이진탐색, 최단경로  (**)
* 입력의 개수가 많은 경우 & 입력을 최대한 빠르게 받아야 하는 경우 
(1000만 개가 넘는 라인이 입력되는 경우)
* python의 sys 라이브러리 readline() 함수를 이용한다 (엔터가 줄 바꿈 기호로 입력된다)
* 공백 문자를 제거하려면 rstrip() 함수를 이용해야 한다.
```python
import sys
sys.stdin.readline().rstrip()
```

#### 4. 출력
* print() 변수, 상수를 매개변수로 받는다
* 콤마 (,) 
    * 띄어쓰기로 구분되어 출력한다. 
    * 자료형을 콤마 기준으로 구분 시 문자열과 수를 함께 출력 가능하다. 
```python
answer = 7
print("정답은", answer, "입니다.") # 정답은 7 입니다.
```
* 더하기 연산자 (+)
    * 문자열, 자료형끼리만 연산가능 
    * str() 함수를 이용해서 출력변수를 문자열로 변경해준다
```python
answer = 7
print("정답은" + str(answer)+"입니다.") # 정답은 7 입니다.
```
 #### 5. fstring 
 ```python
 answer = 7
 print(f"정답은 {answer}입니다.")
 
 ```
