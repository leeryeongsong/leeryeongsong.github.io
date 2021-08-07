---
title:  "[9단계] 파이썬3으로 백준 단계별로 풀어보기- 기본 수학 2"
excerpt: "9단계 1978번, 2581번, 11653번"
toc: true
toc_sticky: true
toc_label: "백준 단계별로 풀어보기 9단계"
categories:
  - baekjoon
tags:
  - 백준
  - 백준단계별로풀어보기
  - Algorithm
  - 파이썬3
  - Python3
  - 사칙연산
  - 수학
  - 정수론
  - 소수_판정
  - 에라토스테네스의_체 
---
<br>
백준의 **저작권** 안내에 따라   
**문제 본문: 링크**로 제공   
**소스 코드: 제가 작성한 소스 코드**   
백준 아이디: [leelee9797](https://www.acmicpc.net/user/leelee9797)  
<br>
**사용 언어: Python 3**  
**외부 에디터: Visual Studio Code**  
<br>
9단계 작성 기간 : 2021년 8월 5일 ~ 2021년 8월 
<br>
<br>
# 9단계, 기본 수학 2
[백준 단계별로 풀어보기 9단계](https://www.acmicpc.net/step/9)  
백준 사이트의 "단계별로 풀어보기" 문제 중 난이도 9단계 문제입니다.  
9단계에는 예제가 11개 있습니다.  
아래 소제목 이름은  
**(예제 n단계), (문제 번호), (문제 제목), (알고리즘 분류) 순서**입니다.  
<br>


### 예제 1단계, 1978번, "소수 찾기", 수학, 정수론, 소수 판정, 에라토스테네스의 체  
[백준 1978번 문제](https://www.acmicpc.net/problem/1978)  
**해결책**  
```python
import math

def is_prime_number(n):
    array = [True for i in range(n+1)] 
    for i in range(2, int(math.sqrt(n)) + 1): 
        if array[i] == True: 
            j = 2
            while i * j <= n:
                array[i * j] = False
                j += 1
    return [ i for i in range(2, n+1) if array[i] ]


N = int(input())
N_list = list(map(int, input().split()))
prime_num = is_prime_number(max(N_list))
count = 0

for i in N_list:
    if i in prime_num:
        count += 1

print(count)
```
<br> 
<br>
 


[에라토스테네스의 체 설명 블로그 글](https://velog.io/@koyo/python-is-prime-number)

<br> 
<br> 
* * *

<br> 
<br> 
* * *
### 예제 2단계, 2581번, "소수", 수학, 정수론, 소수 판정   
[백준 2581번 문제](https://www.acmicpc.net/problem/2581)  
**해결책**  
```python
import math

def is_prime_number(n):
    array = [True for i in range(n+1)] 
    for i in range(2, int(math.sqrt(n)) + 1): 
        if array[i] == True: 
            j = 2
            while i * j <= n:
                array[i * j] = False
                j += 1
    return [ i for i in range(2, n+1) if array[i] ]

M = int(input())
N = int(input())
prime_num = [x for x in is_prime_number(N) if x not in is_prime_number(M-1)]

if len(prime_num) > 0:
    print(sum(prime_num))
    print(min(prime_num))
else:
    print(-1)
```
<br> 
<br>
자연수 M과 N을 입력 받고,   
M 이상 N 이하의 자연수 중 소수의 합과 최소값을 출력해야 한다.  
<br> 
<br> 
* * *
예제 1단계 문제와 같이  
N 이하의 소수를 리스트 자료형으로 반환하는 함수 is_prime_number()를 정의하고 이용했다.  
해당 함수에 대한 내용은 아래 링크에 있다.  
[에라토스테네스의 체 설명 블로그 글](https://velog.io/@koyo/python-is-prime-number)  
```python
import math

def is_prime_number(n):
    array = [True for i in range(n+1)] 
    for i in range(2, int(math.sqrt(n)) + 1): 
        if array[i] == True: 
            j = 2
            while i * j <= n:
                array[i * j] = False
                j += 1
    return [ i for i in range(2, n+1) if array[i] ]
```
<br> 
<br> 
* * *
함수 정의가 끝나고,  
M과 N을 한 줄에 하나씩 입력 받아 저장한다.  
```python
M = int(input())
N = int(input())
```
<br> 
<br> 
* * *
M 이상 N 이하의 소수를 찾아야 한다.  
is_prime_number(n)는 n 이하의 소수를 반환하는 함수이다.  
<br> 
그렇다면,  
M-1 이하의 소수와 N 이하의 소수를 찾고, 그 차집합을 구하면 된다.  
<br> 
리스트의 합을 구할 때는 더하기 연산자를 이용하면 되지만  
리스트의 차를 구할 때는 빼기 연산자를 사용할 수 없다.  
<br> 
이를 위해 다음의 방법,  
1) 리스트 컴프리헨션을 이용한다.  
```python
prime_num = [x for x in is_prime_number(N) if x not in is_prime_number(M-1)]  
```
is_prime_number(N)의 원소 x 중, is_prime_number(M-1)에 있지 않은 x만 가져와서 prime_num 리스트에 저장한다.  
<br> 
2) 다른 방법으로 set 자료형끼리 빼기 연산자로 차집합을 구할 수 있다.  
리스트 자료형끼리 빼기 연산자는 사용할 수 없지만  
set 자료형끼리 빼기 연산자를 사용할 수 있다.  
그 외에도 & 기호로 교집합을, \| 기호로 합집합을 구할 수 있다.  
<br> 
<br> 
* * *
다음으로 넘어가자.  
M 이상 N 이하의 자연수 중 소수의 합을 첫째 줄에, 최솟값을 둘째 줄에 출력해야 하고,  
소수가 없을 경우에는 -1을 출력해야 한다.  
<br> 
그러므로 if문으로 소수가 있는지 확인한다.  
소수를 저장한 리스트 prime_num의 길이가 0보다 크면, 소수가 있는 것이다.  
<br> 
따라서
len(prime_num) > 0 일 때  
sum() 함수로 prime_num의 합을 구하고 print() 함수로 출력하고,  
min() 함수로 prime_num의 최솟값을 구하고 print() 함수로 출력한다.  
<br> 
else, 소수가 없을 때 -1을 출력한다.  
```python
if len(prime_num) > 0:
    print(sum(prime_num))
    print(min(prime_num))
else:
    print(-1)
```
<br> 
<br> 
* * *
문제 조건을 충족했다.  
<br> 
<br> 
* * *
### 예제 3단계, 11653번, "소인수분해", 수학, 정수론, 소수 판정   
[백준 11653번 문제](https://www.acmicpc.net/problem/11653)  
**해결책**  
```python
N = int(input())
i = 2

if N > 1:
    while N > i:
        if N % i == 0:
            print(i)
            N = N // i
            continue
        else:
            i += 1
    print(N)
```
<br> 
<br>
정수 N을 입력 받고 소인수분해를 진행하자.  
소인수분해는 1보다 큰 자연수를 소수들만의 곱으로 나타내는 것이다.  
<br>
1) 가장 작은 소수인 2부터 1씩 나누는 방법
2) 소수를 찾아내서 N을 나누는 방법
두 가지가 있다.  
<br>
위 소스 코드는 첫 번째 방법을 사용했다.
<br> 
<br> 
* * *
정수 N을 입력 받아 N에 저장한다.  
N을 나눌 숫자 i의 초기값을 2로 설정한다.  
```python
N = int(input())
i = 2
```
<br> 
<br> 
* * *
N이 1이면 아무것도 출력하지 않고,  
N이 2 이상이면 소인수분해를 진행하므로  
if문으로 N > 1 일 때 소인수분해를 진행한다.  
```python
if N > 1:
```
<br> 
<br> 
* * *
소인수분해 과정은 다음과 같다.  
먼저 N을 가장 작은 소수인 2로 나눈다.  
N이 2로 나누어 떨어지면 2를 출력하고, N에 N//2를 저장한다.  
continue로 인해 다시 while 초반으로 돌아간다.  
N을 2로 나누는 과정을 반복한다.  
<br>
만약 N이 2로 나누어 떨어지지 않는다면, 2에 1을 더한다.  
while 초반으로 돌아가서,  
N을 3으로 나눈다.  
마찬가지로,  
N이 3으로 나누어 떨어지면 3을 출력하고, N에 N//3을 저장한다.  
continue로 인해 다시 while 초반으로 돌아간다.  
<br>
N이 3으로 나누어 떨어지지 않는다면, 3에 1을 더한다.  
while 초반으로 돌아가서,  
N을 4로 나눈다.  
하지만, 이미 2로 최대한 나눴기 때문에 나누어 떨어지지 않을 것이다.  
4에 1을 더하고 while 초반으로 돌아가게 된다.  
<br>
...
위와 같은 과정을 반복하면 N은 계속 작아진다.  
N이 i보다 작거나 같아지면, 소인수분해가 끝난 것이고 while 조건문에 거짓이므로 while문이 끝난다.  
마지막으로 N을 출력한다.  
```python
    while N > i:
        if N % i == 0:
            print(i)
            N = N // i
            continue
        else:
            i += 1
    print(N)
```
<br> 
<br> 
* * *
문제 조건을 충족했다.  
<br> 
<br> 
* * *
### 예제 4단계, 1929번, "소수 구하기", 수학, 정수론, 소수 판정, 에라토스테네스의 체  
[백준 1929번 문제](https://www.acmicpc.net/problem/1929)  
**시행착오**  
```python
# 시간 초과
import math
def is_prime_number(n):
    array = [True for i in range(n+1)] 
    for i in range(2, int(math.sqrt(n)) + 1): 
        if array[i] == True: 
            j = 2
            while i * j <= n:
                array[i * j] = False
                j += 1
    return [ i for i in range(2, n+1) if array[i] ]
M, N = map(int, input().split())
prime_num = [x for x in is_prime_number(N) if x not in is_prime_number(M-1)]
for i in range(len(prime_num)):
    print(prime_num[i])
```
<br> 
<br>
예제 1, 2단계 문제와 같이  
N 이하의 소수를 리스트 자료형으로 반환하는 함수 is_prime_number()를 정의하고 이용했다.  
해당 함수에 대한 내용은 아래 링크에 있다.  
[에라토스테네스의 체 설명 블로그 글](https://velog.io/@koyo/python-is-prime-number)  
<br> 
<br> 
* * *
M과 N을 입력받아서 저장한다.  
공백을 기준으로 나눠서 입력받고, int형으로 변환하여 저장하므로 아래와 같이 코드를 작성한다.  
```python
M, N = map(int, input().split())
```
<br> 
<br> 
* * *
M 이상 N 이하의 소수를 한 줄에 하나씩, 증가하는 순서대로 소수를 출력해야 한다.  
예제 2단계에서 M 이상 N 이하의 소수를 구하기 위해 리스트 컴프리헨션을 이용한 것과 동일한 방식을 사용했다.  
```python
prime_num = [x for x in is_prime_number(N) if x not in is_prime_number(M-1)]
```
N 이하의 소수를 리스트 자료형으로 반환하는 is_prime_number(N)에서 요소 x를 가져오는데,  
M-1 이하의 소수를 리스트 자료형으로 반환하는 is_prime_number(M-1)에 포함되지 않은 x만 가져와서  
prime_num에 저장한다.   
prime_num에는 M 이상 N 이하의 소수가 리스트 형태로 저장되어 있다.  
<br> 
<br> 
* * *
구한 소수를 한 줄에 하나씩, 증가하는 순서대로 출력해야 한다.  
이미 prime_num에는 증가하는 순서대로 소수가 저장되어 있으므로,  
for문을 이용하여 한 줄에 하나씩 출력한다.  
```python
for i in range(len(prime_num)):
    print(prime_num[i])
```
<br> 
<br> 
* * *
시간 초과 결과가 나왔다.  
아래처럼 코드를 수정했다.  
<br> 
<br> 
* * *
**해결책**  
```python
# 메모리 42488KB 시간 532ms 
import math
def is_prime_number(n):
    array = [True for i in range(n+1)] 
    for i in range(2, int(math.sqrt(n)) + 1): 
        if array[i] == True: 
            j = 2
            while i * j <= n:
                array[i * j] = False
                j += 1
    return [ i for i in range(2, n+1) if array[i] ]


M, N = map(int, input().split())
prime_num = is_prime_number(N)
for i in prime_num:
    if i>=M:
        print(i)
```
<br> 
<br>
M과 N을 입력받아 저장하고, 그 아래 코드 부분을 수정했다.  
<br> 
<br> 
* * *
is_prime_number(N)를 prime_num에 저장한다.  
prime_num에는 N 이하의 소수가 증가하는 순서대로 저장되어 있다.  
```python
prime_num = is_prime_number(N)
```
<br> 
<br> 
* * *
M 이상 N 이하의 소수를 증가하는 순서대로 출력해야 한다.  
for문으로, prime_num의 요소 i를 가져와서  
i가 M 이상이면 i를 출력한다.  
```python
for i in prime_num:
    if i>=M:
        print(i)
```
<br> 
<br> 
* * *
문제 조건을 충족했다.  
```python
# 메모리 42488KB 시간 532ms 
```
<br> 
<br> 
* * *
### 예제 5단계, 4938번, "베르트랑 공준", 수학, 정수론, 소수 판정, 에라토스테네스의 체  
[백준 4938번 문제](https://www.acmicpc.net/problem/4938)  
**시행착오**  
```python
# 시간 초과
import math
def is_prime_number(n):
    array = [True for i in range(n+1)] 
    for i in range(2, int(math.sqrt(n)) + 1): 
        if array[i] == True: 
            j = 2
            while i * j <= n:
                array[i * j] = False
                j += 1
    return [ i for i in range(2, n+1) if array[i] ]
n = 1
while n:
    n = int(input())
    if n == 0:
        break
    prime_num_2n = is_prime_number(2*n)
    prime_num_n = is_prime_number(n)
    print(len(prime_num_2n)-len(prime_num_n))
```
<br> 
<br>
예제 1, 2, 4단계 문제와 같이  
N 이하의 소수를 리스트 자료형으로 반환하는 함수 is_prime_number()를 정의하고 이용했다.  
해당 함수에 대한 내용은 아래 링크에 있다.  
[에라토스테네스의 체 설명 블로그 글](https://velog.io/@koyo/python-is-prime-number)   
<br> 
<br> 
* * *
입력받은 수를 n에 저장할 것이다.  
n을 입력할 때마다 n보다 크고, 2n보다 작거나 같은 소수의 개수를 출력해야 한다.  
n에 0을 입력하면 프로그램 실행을 끝내야 한다.  
그러므로 n의 초기값을 1로 설정하고,  
while n: 으로 n이 0이 아닐 때는 True로 취급하여 무한 루프로 동작시킨다.  
(while true라고 입력해도 된다.)  
<br> 
숫자 n을 입력받아 정수형으로 변환하고 n에 저장한다.  
<br> 
if문으로 n에 입력받은 자료가 0과 같으면 break로 while문을 끝낸다.  
```python
n = 1
while n:
    n = int(input())
    if n == 0:
        break
```
while n:으로 코드를 작성해뒀는데 왜 if문을 썼냐면,  
if문이 없다면  
n에 0을 저장해도, 진행하던 while은 그대로 실행되어 n이 0일 때의 결과물 0이 출력된 다음,  
while n: 조건을 확인하니 n이 0, False 조건이므로 프로그램 실행을 멈춘다.  
이런 동작은 소스 코드에서 n값을 확인하는 while n:이 n을 입력받아 저장하는 n = int(input()) 보다 앞에 있기 때문이다.  
<br> 
문제에서 원하는 동작 방식은  
0을 입력했을 때 출력 결과 없이 바로 프로그램 실행을 멈추는 것이다.  
따라서 n을 입력받아 저장한 다음, if문으로 n을 확인하는 코드를 작성했다.  
<br> 
<br> 
* * *
문제는 n보다 크고, 2n보다 작거나 같은 소수의 개수를 출력해야 한다.  
prime_num_2n에 is_prime_number(2\*n)를 저장하고,  
prime_num_n에 is_prime_number(n)를 저장했다.  
```python
    prime_num_2n = is_prime_number(2*n)
    prime_num_n = is_prime_number(n)
```
이로써 
prime_num_2n에 2n 이하 소수가 리스트 자료형으로 저장되었고,  
prime_num_n에 n 이하 소수가 리스트 자료형으로 저장되었다.  
<br> 
<br> 
* * *
prime_num_2n의 길이와 prime_num_n의 길이를 len() 함수로 구하고,  
빼기 연산자로 이들의 차를 구하면  
n보다 크고 2n보다 작거나 같은 소수의 개수를 구한 것이다.  
```python
print(len(prime_num_2n)-len(prime_num_n))
```
<br> 
<br> 
* * *
실행하니 '시간 초과'가 나왔다.  
아래에 같이 코드를 수정했다.  

<br> 
<br> 
* * *
**해결책**  
```python
# 메모리 34744KB 시간 4796 ms
import math
def is_prime_number_2n(n):
    array = [True for i in range(2*n+1)] 
    for i in range(2, int(math.sqrt(2*n)) + 1): 
        if array[i] == True: 
            j = 2
            while i * j <= 2*n:
                array[i * j] = False
                j += 1
    return [ i for i in range(n+1, 2*n+1) if array[i] ]

n = 1
while n:
    n = int(input())
    if n == 0:
        break
    print(len(is_prime_number_2n(n)))
```
<br> 
<br> 
* * *
이번에는 is_prime_number() 함수 정의를 수정했다.  
이름도 is_prime_number_2n()으로 바꾸고  
n을 함수에 전달하면  
n+1 이상 2\*n 이하의 소수를 리스트 형태로 반환하도록  
함수 내부의 리스트 자료형과 range() 함수의 범위, while문의 조건을 수정한다.  
<br> 
```python
def is_prime_number_2n(n):
    array = [True for i in range(2*n+1)] 
    for i in range(2, int(math.sqrt(2*n)) + 1): 
        if array[i] == True: 
            j = 2
            while i * j <= 2*n:
                array[i * j] = False
                j += 1
    return [ i for i in range(n+1, 2*n+1) if array[i] ]
```
<br> 
<br> 
* * *
n을 1로 초기화하고 while문을 시작, if문으로 n을 확인하는 것까지는 이전 코드와 동일하다.  
```python
n = 1
while n:
    n = int(input())
    if n == 0:
```
<br> 
<br> 
* * *
다음 과정으로  
이전 코드에서는 2n 이하의 소수와 2n 이하의 소수 개수를 각각 구하여 뺐지만,   
이번 코드에서는 바로 is_prime_number_2n(n)의 길이를 출력하면 된다.  
```python
    print(len(is_prime_number_2n(n)))
```
<br> 
<br> 
* * *
문제 조건을 충족했다.  
```python
# 메모리 34744KB 시간 4796 ms
```
<br> 
<br> 
* * *
