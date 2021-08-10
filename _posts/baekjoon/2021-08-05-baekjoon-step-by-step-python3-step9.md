---
title:  "[9단계] 파이썬3으로 백준 단계별로 풀어보기- 기본 수학 2"
excerpt: "9단계 1978번, 2581번, 11653번, 1929번, 4948번, 9020번, 1085번, 3009번, 4153번, 3053번, 1002번"
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
  - 기하학
  - 구현
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
9단계 작성 기간 : 2021년 8월 5일 ~ 2021년 8월 10
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
숫자 N개가 주어지고, 이 중 소수가 몇 개인지 찾아서 출력해야 한다. 
<br> 
<br> 
* * *
알고리즘 분류를 보니, 에라토스테네스의 체가 있어서 검색했다.  
<br> 
n 이하의 소수를 리스트 자료형으로 반환하는 함수 is_prime_number()를 정의하고 이용했다.  
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
n 이하의 소수를 반환하는 함수를 살펴보자.  
```python
import math

def is_prime_number(n):
```
풀이 중간에 제곱근을 구하는 math.sqrt()을 사용하므로, math를 import한다.  
def 키워드로 is_prime_number(n) 함수를 정의한다.  
<br> 
<br> 
* * *
True가 n+1개인 리스트 array를 선언한다.  
```python
    array = [True for i in range(n+1)] 
```
리스트 array\[j] = True이면 j가 소수라는 의미이므로  
리스트 array가 True n+1개로 이루어져 있다면, 0부터 n까지 모든 수가 소수라고 간주하는 것이다.  
<br> 
<br> 
* * *
에라토스테네스의 체는  
확인하지 않은 수 i 중 가장 작은 소수를 찾고,  
가장 작은 소수의 배수에 해당하는 수는 소수가 아니므로 제거한다.  
위 방법을 반복하는데, i를 n까지 확인하는 게 아니라 n의 제곱근까지 확인하면 된다.  
```python
    for i in range(2, int(math.sqrt(n)) + 1): 
        if array[i] == True: 
            j = 2
            while i * j <= n:
                array[i * j] = False
                j += 1
```
왜 i를 n까지가 아니라 n의 제곱근까지 확인하면 되는지 살펴보자.  

n이 121이면 n의 제곱근은 11이다.  
11^2 = 121  
121을 두 수의 곱으로 표현한다면,  
11보다 큰 두 수의 곱으로 121을 만들어 낼 수 없다. (12와 13의 곱으로 121을 만들어 낼 수 없다.)  
121과 그 이하의 숫자를 두 수의 곱 i \* j 으로 나타내려면, 두 수 i 와 j 중 적어도 하나(i라고 하자)는 11 이하이다.  
따라서 i를 11까지 확인하면 된다.  

수식으로 살펴보자.  
숫자 n이 i와 j의 곱으로 나타내어질 때(소수가 아님)  
i가 n의 제곱근보다 작다면 j는 n의 제곱근보다 크다는 것을 확인하자.    

n = i \* j = (n^(1/2)) \* (n^(1/2))  

i < n^(1/2) 이면  
양변에 j(양수)를 곱했을 때  
i \* j < (n^(1/2)) \* j  
이때 좌변 i \* j = n = (n^(1/2)) \* (n^(1/2)) 이므로  
i \* j = n = (n^(1/2)) \* (n^(1/2)) < (n^(1/2)) \* j  
즉,  
(n^(1/2)) \* (n^(1/2)) < (n^(1/2)) \* j  
양변에 양수 (n^(1/2))를 나누면  
(n^(1/2)) < j  

따라서, i이 n의 제곱근보다 작다면 j는 n의 제곱근보다 크다.  
에라토스테네스의 체에서 i를 2부터 n의 제곱근까지 확인하면 곱 i * j 중 작은 수를 충분히 확인하는 것이다.  
<br> 
<br> 
* * *
에라토스테네스의 체 과정이 끝나고  
2부터 n까지의 i 중 array\[i]가 True인 i를 가져와서 리스트 형태로 반환하면 된다.  
n 이하의 소수를 증가하는 순서대로, 리스트 형태로 반환한다.  
```python
    return [ i for i in range(2, n+1) if array[i] ]
```
<br> 
<br> 
* * *
이제 is_prime_number(n) 함수 정의가 끝났다.  
<br> 
수의 개수를 입력받아 N에 저장한다.  
N개의 수를 공백을 기준으로 입력받아 정수형으로 변환하고, 리스트 자료형으로 N_list에 저장한다.  
```python
N = int(input())
N_list = list(map(int, input().split()))
```
<br> 
<br> 
* * *
N 개의 수 중 최댓값(max(N_list))을 is_prime_number() 함수에 대입한다.  
N 개의 수 중 최댓값 이하의 소수를 리스트 자료형으로 구하여 prime_num에 저장한다.  
```python
prime_num = is_prime_number(max(N_list))
```
<br> 
<br> 
* * *
count 변수는 N 개의 수 중 소수의 개수를 저장할 변수이다.  
count를 0으로 초기화한다.  
```python
count = 0
```
<br> 
<br> 
* * *
for문으로 N_list의 각 요소를 i로 가져와서,  
i가 소수인 prime_num에 존재한다면(if)  
소수의 개수인 count에 1을 더한다.  
```python
for i in N_list:
    if i in prime_num:
        count += 1
```
<br> 
<br> 
* * *
for문이 끝나고  
N개의 숫자 중 소수의 개수인 count를 출력한다.  
```python
print(count)
```
<br> 
<br> 
* * *
문제 조건을 충족했다.  
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
### 예제 6단계, 9020번, "골드바흐의 추측", 수학, 정수론, 소수 판정, 에라토스테네스의 체  
[백준 9020번 문제](https://www.acmicpc.net/problem/9020)  
**시행착오**  
```python
# 시행착오 1
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

T = int(input())

for i in range(T):
    n = int(input())
    prime_num = is_prime_number(n)
    for j in range(-1, -len(prime_num)-1,-1):
        if prime_num[j] <= n//2:
            if n-prime_num[j] in prime_num:
                print(prime_num[j], n-prime_num[j])
                break


# 시행착오 2. input() 대신 sys.stdin.readline() 사용
# 시간 초과
import math
import sys

def is_prime_number(n):
    array = [True for i in range(n+1)] 
    for i in range(2, int(math.sqrt(n)) + 1): 
        if array[i] == True: 
            j = 2
            while i * j <= n:
                array[i * j] = False
                j += 1
    return [ i for i in range(2, n+1) if array[i] ]

T = int(sys.stdin.readline())

for i in range(T):
    n = int(sys.stdin.readline())
    prime_num = is_prime_number(n)
    for j in range(-1, -len(prime_num)-1,-1):
        if prime_num[j] <= n//2:
            if n-prime_num[j] in prime_num:
                print(prime_num[j], n-prime_num[j])
                break


# 시행착오 3. math.sqrt() 대신 ** 연산자 사용해 봄. 여전히 시간 초과. 큰 영향이 없을 수 있음.
# 시간 초과
import sys

def is_prime_number(n):
    array = [True for i in range(n+1)] 
    for i in range(2, int(n**0.5) + 1): 
        if array[i] == True: 
            j = 2
            while i * j <= n:
                array[i * j] = False
                j += 1
    return [ i for i in range(2, n+1) if array[i] ]

T = int(sys.stdin.readline())

for i in range(T):
    n = int(sys.stdin.readline())
    prime_num = is_prime_number(n)
    for j in range(-1, -len(prime_num)-1,-1):
        if prime_num[j] <= n//2:
            if n-prime_num[j] in prime_num:
                print(prime_num[j], n-prime_num[j])
                break
```
<br> 
<br>
첫째 줄에 테스트 케이스의 개수 T가 주어지고,  
각 테스트 케이스에 대해 주어진 짝수 n의 골드바흐 파티션을 출력해야 한다.  
n의 골드바흐 파티션은 합이 n이 되는 두 소수의 조합을 의미한다.  
n의 골드바흐 파티션이 여러 가지일 경우 두 소수의 차이가 가장 작은 것을 출력하며, 
골드바흐 파티션을 출력할 때 작은 수 먼저 출력하고 공백으로 구분해야 한다.  
<br> 
<br> 
* * *
예제 1, 2, 4, 5단계 문제와 같이  
N 이하의 소수를 리스트 자료형으로 반환하는 함수 is_prime_number()를 정의하고 이용했다.  
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
해당 함수에 대한 내용은 아래 링크에 있다.  
[에라토스테네스의 체 설명 블로그 글](https://velog.io/@koyo/python-is-prime-number)   
<br> 
<br> 
* * *
테스트 케이스의 개수를 입력받아 T에 저장한다.   
for-range() 문으로 for문을 T번 반복한다.  
```python
T = int(input())

for i in range(T):
```
<br> 
<br> 
* * *
짝수 n을 입력받아 n에 저장한다.  
```python
    n = int(input())
```
<br> 
<br> 
* * *
prime_num에 is_prime_number(n)를 저장한다.  
prime_num에 n 이하의 소수가 리스트 자료형으로 저장되었다.  
```python
    prime_num = is_prime_number(n)
```
<br> 
<br> 
* * *
이제 골드바흐 파티션을 찾아야 한다.  
<br>  
문제 조건에 의해 여러 골드바흐 파티션 중 두 소수의 차이가 가장 작은 것을 찾아야 하는데,  
두 소수의 차이가 작을수록, 두 소수는 n의 절반에 가깝다.
<br> 
prime_num에 소수는 증가하는 순서대로 저장되어 있다.  
<br> 
1) for문으로 두 소수 중 작은 수를 찾아낼 것이고,    
n의 절반에서 작아지는 방향으로 확인하려면... prime_num에 인덱스를 -1부터 1씩 감소하며 접근하면 되고,  
<br> 
2) for문으로 두 소수 중 큰 수를 찾아낼 것이고,  
n의 절반에서 증가하는 방향으로 확인하려면... prime_num에 인덱스를 0부터 1씩 증가하며 접근하면 된다.  
<br> 
이 코드는 1)의 방식으로 접근한다.  
prime_num의 각 요소를 인덱스 -1부터 앞으로 한 칸씩 끝까지 확인할 것이다.  
인덱스로 쓰일 j를 range(-1, -len(prime_num)-1, -1)에서 가져온다.  
인덱스 -1은 연속적인 자료형의 가장 오른쪽 끝의 인덱스를 의미한다.  
range()의 끝값을 -len(prime_num)-1로 설정하면, 연속적인 자료형의 왼쪽 끝까지 가져오게 된다.  
끝값은 포함 안 되니, -len(prime_num)으로 설정하면 왼쪽 끝 자료를 안 가져온다! -1 필수.  
<br> 
prime_num은 소수가 증가하는 순서대로 저장되어 있기 때문에,  
인덱스 -1부터 확인하면 소수가 감소하는 순서대로 확인하게 된다.  
```python
    for j in range(-1, -len(prime_num)-1,-1):  
```
<br> 
if문으로 prime_num\[j]이 n//2보다 작을 때,  
```python
        if prime_num[j] <= n//2:    
```
<br> 
n-prime_num\[j]도 prime_num에 해당한다면(소수에 해당한다면)  
prime_num\[j]과 n-prime_num\[j]은 골드바흐 파티션이다.  
<br> 
prime_num\[j]은 n의 절반보다 작은 수이므로 n-prime_num\[j]보다 항상 작다.
<br> 
골드바흐 파티션을 작은 수 먼저 출력해야 하므로 
prime_num\[j] n-prime_num\[j] 순서대로 출력한다.  
<br> 
구한 골드바흐 파티션이, 두 소수의 차이가 가장 작은 파티션이므로  
다음 골드바흐 파티션을 출력하면 안 된다.  
break로 for문 실행을 끝낸다.  
```python
            if n-prime_num[j] in prime_num:
                print(prime_num[j], n-prime_num[j])
                break
```
<br> 
<br> 
* * *
실행하니 '시간 초과'가 나왔다.  
<br> 
백준 15552번([단계별로 풀어보기 3단계 중 예제 4번](https://leeryeongsong.github.io/baekjoon/baekjoon-step-by-step-python3-step3/#%EC%98%88%EC%A0%9C-4%EB%8B%A8%EA%B3%84-15552%EB%B2%88-%EB%B9%A0%EB%A5%B8-ab-%EC%88%98%ED%95%99-%EA%B5%AC%ED%98%84-%EC%82%AC%EC%B9%99%EC%97%B0%EC%82%B0))에서,  
반복문으로 여러 줄 입력 받을 때 input()을 사용하면 시간 초과 나올 수 있다고 한 것이 생각났다.  
input() 대신 sys.stdin.readline()으로 바꿔보기도 하고...(<- 바꿔도 '시간 초과')  
math.sqrt()를 ** 연산자로 바꿔보기도 했다. (<- 바꿔도 '시간 초과', 큰 차이 없는 것인가?)  
<br> 
코드 풀이 과정을 바꿔야겠다고 생각하여, 아래와 같이 변경했다.  
<br> 
<br> 
* * *
**해결책**  
```python
# 메모리 29200KB, 시간 1856ms
import sys

array = [True] * 10001
for i in range(2, 101):
    if array[i] == True:
        for j in range(i+i, 10001, i):
            array[j] = False
prime_num = [i for i in range(2, 10001) if array[i] == True]

T = int(sys.stdin.readline())

for i in range(T):
    n = int(sys.stdin.readline())
    half = n//2
    for j in range(half, -1, -1):
        if j in prime_num and n-j in prime_num:
            print(j, n-j)
            break
```
<br> 
<br> 
* * *
이전 풀이는  
n 이하의 소수를 구하는 함수를 정의하고,  
각 테스트 케이스에서 n을 입력받으면  
n 이하의 소수를 구하고 -> 모든 소수를 확인하여 -> 소수가 n//2 이하이면 -> n-소수가 소수인지 확인하고 -> n-소수가 소수가 맞다면 소수, n-소수 출력  
<br> 
변경한 풀이는  
n은 4 이상 10000 이하이다.  
10000 이하의 소수를 구한다.  
(위에서 정의한 함수에 대입하면 된다.)  
각 테스트 케이스에서 n을 입력받으면  
n//2를 구하고 -> 정수 j를 n//2부터 0까지 -1씩 감소하며 확인하여 -> j가 소수에 속하고 n-j도 소수에 속하면 j, n-j 출력  
<br> 
<br> 
* * *
문제 조건을 충족했다.  
```python
# 메모리 29200KB, 시간 1856ms
```

<br> 
<br> 
* * *
### 예제 7단계, 1085번, "직사각형에서 탈출", 수학, 기하학  
[백준 1085번 문제](https://www.acmicpc.net/problem/1085)  
**해결책**  
```python
x, y, w, h = map(int, input().split())

a = w - x
b = h - y
c = x
d = y
print(min(a, b, c, d))
```
<br> 
<br>
좌표 공간에 각 변이 좌표축에 평행하는 직사각형이 있다.  
직사각형의 왼쪽 아래 꼭짓점은 (0, 0), 오른쪽 위 꼭짓점은 (w, h)에 있다.  
직사각형 내의 좌표 (x, y)가 주어지고,  
(x, y)에서 직사각형의 경계선까지의 최단거리를 출력해야 한다.  
<br> 
<br> 
* * *
x, y, w, h는 정수이다. 
첫째 줄에 x, y, w, h를 공백을 기준으로 입력받고 정수형으로 변환하여 저장한다.  
```python
x, y, w, h = map(int, input().split())
```
<br> 
<br> 
* * *
점 (x, y)에서 직사각형의 경계선까지의 최단 거리는  
경계선(x = 0, x = w, y = 0, y = h)이 좌표축과 평행하므로 |x좌표의 차이| 또는 |y좌표의 차이|로 나타낼 수 있다.  

점에서 선까지의 최단 거리는  
점에서 선으로 수선의 발을 내리고, 점에서 수선의 발까지의 거리를 계산해야 하는데,  
선이 좌표축과 평행하니 점에서 수선의 발까지의 선분도 다른 좌표축과 평행하다.  

점 (x, y)에서 4개의 경계선까지의 거리를 아래와 같이 모두 구한다.  
```python
a = w - x
b = h - y
c = x
d = y
```
<br> 
<br> 
* * *
4개의 거리 중 가장 작은 값을 출력하면 문제에서 요구하는 최단 거리이다.  
```python
print(min(a, b, c, d))
```
<br> 
<br> 
* * *
문제 조건을 충족했다.  
<br> 
<br> 
* * *
### 예제 8단계, 3009번, "네 번째 점", 구현, 기하학  
[백준 3009번 문제](https://www.acmicpc.net/problem/3009)  
**해결책**  
```python
import sys

x = [0, 0, 0]
y = [0, 0, 0]
for i in range(3):
    x[i], y[i] = map(int, sys.stdin.readline().split())

for j in x:
    if x.count(j) == 1:
        a = j
for k in y:
    if y.count(k) == 1:
        b = k

print(a, b)
```
<br> 
<br>
점 3개가 주어졌을 때, 축에 평행한 직사각형을 만드는 데 필요한 마지막 점의 좌표를 찾아야 한다.  
<br>
직사각형의 변이 축에 평행하지 않았다면.. 약간 복잡한 문제이지만,  
이 문제는 직사각형이 축에 평행하므로 간단한 문제이다.  
<br> 
<br> 
* * *
A--------B  
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|  
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|  
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|  
D--------C  
<br>
위와 같이 직사각형의 변이 축과 평행하면...   
점 A와 점 B는 y 좌표가 같고,  
점 D와 점 C는 y 좌표가 같다.  
또한  
점 A와 점 D는 x 좌표가 같고  
점 B와 점 C는 x 좌표가 같다.  
<br>
이를 좌표로 표시하면 다음과 같다.  
A(x1, y2) B(x2, y2)  
D(x1, y1) C(x2, y1)  
<br>
각 점의 좌표를 x 좌표끼리, y 좌표끼리 모아보면  
x 좌표에는 x1, x1, x2, x2  
y 좌표에는 y1, y1, y2, y2  
<br>
x 좌표, y 좌표 각각 2개의 좌표가 2번씩 나타나는 규칙성이 있다.  
<br> 
<br> 
* * *
만약 점이 3개만 주어진다면,  
마지막 점으로 위의 규칙성을 만족할 수 있어야 한다.  
즉,  
x 좌표끼리, y 좌표끼리 모아둔 리스트를 확인했을 때,  
1개만 있는 좌표가 마지막 점의 좌표가 된다.  
<br> 
<br> 
* * *
코드로 확인해보자.  
<br>
입력받을 때 sys를 사용하므로 sys를 import 한다.  
x와 y의 초기값을 \[0, 0, 0]으로 초기화한다.  
x와 y는 3개의 점의 x 좌표, y 좌표를 저장할 변수이다.  
```python
import sys

x = [0, 0, 0]
y = [0, 0, 0]
```
<br> 
<br> 
* * *
3개의 점의 좌표를 입력받는다.   
for-range() 함수로 3번 반복한다.   
x와 y 각각 x 좌표와 y 좌표를 공백으로 구분하여 저장한다.  
```python
for i in range(3):
    x[i], y[i] = map(int, sys.stdin.readline().split())
```
<br> 
<br> 
* * *
x의 요소를 for문의 j로 가져와서 확인한다.   
j가 x에 존재하는 개수를 count() 메소드로 확인했을 때, 1개라면(if문) a에 j를 저장한다.   
a는 네 번째 점의 x 좌표이다.   
<br> 
마찬가지로
y의 요소를 for문의 k로 가져와서 확인한다.  
k가 y에 존재하는 개수를 count() 메소드로 확인했을 때, 1개라면(if문) b에 k를 저장한다.  
b는 네 번째 점의 y 좌표이다.  
```python
for j in x:
    if x.count(j) == 1:
        a = j
for k in y:
    if y.count(k) == 1:
        b = k
```
<br> 
<br> 
* * *
네 번째 점의 x 좌표, y 좌표를 순서대로 출력한다.  
a, b를 순서대로 출력하면 된다.  
```python
print(a, b)
```
<br> 
<br> 
* * *
문제 조건을 충족했다.  
<br> 
<br> 
* * *
### 예제 9단계, 4153번, "직각삼각형", 수학, 기하학  
[백준 4153번 문제](https://www.acmicpc.net/problem/4153)  
**해결책**  
```python
import sys

while True:
    a, b, c = map(int, sys.stdin.readline().split())
    if a == 0 and b == 0 and c == 0:
        break
    if a == max(a, b, c):
        if a*a == b*b + c*c:
            print('right')
            continue
        
    elif b == max(a, b, c):
        if  b*b == a*a + c*c:
            print('right')
            continue
    elif c == max(a, b, c):
        if  c*c == a*a + b*b:
            print('right')
            continue    
    print('wrong')    
```
<br> 
<br>
세 변의 길이가 주어졌을 때,  
직각삼각형이라면 "right" 아니라면 "wrong"을 출력한다.  
입력이 여러 개의 테스트 케이스로 주어지며, 입력마다 위와 같이 출력해야 한다.  
0 0 0이 입력되면 실행을 멈춰야 한다.  
<br>   
직각삼각형을 확인하려면   
가장 긴 변을 찾아내고,  
가장 긴 변의 길이의 제곱 = 나머지 변의 길이의 제곱의 합  
이어야 한다.  
<br> 
<br> 
* * *
0 0 0이 입력될 때까지 반복해서 입력을 받아야 하므로,  
입력에 sys.sydin.readline()을 사용할 것이다.  
sys를 import 해야 한다.  
```python
import sys
```
<br> 
<br> 
* * *
반복 횟수를 모르는 상태에서 반복해야 하므로  
while문을 사용한다.  
while True:로 작성하면 무한 반복한다.  
```python
while True:
```
<br> 
<br> 
* * *
세 변의 길이를 입력받아 각각 a, b, c에 저장한다.  
입력받을 때는 sys.stdin.readline().split() 함수를 이용한다.  
a, b, c를 확인하여 모두 0이면(if문) while문 실행을 break로 종료한다.  
```python
    a, b, c = map(int, sys.stdin.readline().split())
    if a == 0 and b == 0 and c == 0:
        break
```
<br> 
<br> 
* * *
a에 저장된 값이 가장 긴 변의 길이(max(a, b, c))와 동일하다면(if문),  
a\*a == b\*b + c\*c인지 확인한다(if문).  
동일하다면, 직각삼각형이므로 'right'를 출력하고 continue로 while문의 처음으로 돌아간다.  
```python
    if a == max(a, b, c):
        if a*a == b*b + c*c:
            print('right')
            continue
```
a에 저장된 값이 가장 긴 변의 길이와 동일할 때,  
b에 저장된 값도 가장 긴 변의 길이와 동일할 수 있다.  
그렇더라도 a\*a == b\*b + c\*c인지 확인할 때 충분히 직각삼각형인가 검사할 수 있다.  
<br> 
<br> 
* * *
a에 저장된 값이 가장 긴 변의 길이(max(a, b, c))와 동일하지 않고(elif문),  
b에 저장된 값이 가장 긴 변의 길이(max(a, b, c))와 동일할 때(elif문),  
b\*b == a\*a + c\*c인지 확인한다(if문).  
동일하다면, 직각삼각형이므로 'right'를 출력하고 continue로 while문의 처음으로 돌아간다.  
```python
    elif b == max(a, b, c):
        if  b*b == a*a + c*c:
            print('right')
            continue
```
b에 저장된 값이 가장 긴 변의 길이와 동일할 때,  
c에 저장된 값도 가장 긴 변의 길이와 동일할 수 있다.  
그렇더라도 b\*b == a\*a + c\*c인지 확인할 때 충분히 직각삼각형인가 검사할 수 있다.  
<br> 
<br> 
* * *
a에 저장된 값이 가장 긴 변의 길이(max(a, b, c))와 동일하지 않고(elif문),  
b에 저장된 값이 가장 긴 변의 길이(max(a, b, c))와 동일하지 않고(elif문),  
c에 저장된 값이 가장 긴 변의 길이(max(a, b, c))와 동일할 때(elif문)!!!!,  
c\*c == a\*a + b\*b인지 확인한다(if문).  
동일하다면, 직각삼각형이므로 'right'를 출력하고 continue로 while문의 처음으로 돌아간다.  
```python
    elif c == max(a, b, c):
        if  c*c == a*a + b*b:
            print('right')
            continue    
```
<br> 
<br> 
* * *
위의 과정에서 조건을 충족하여 'right'를 출력하지 못했다면...  
그 외는 모두 직각삼각형이 아니므로 'wrong'을 출력한다.  
이미 'right'를 출력한 테스트 케이스는 'right' 출력 직후 continue로 while문의 처음으로 돌아갔기에,  
'wrong' 출력 코드까지 도달하지 않는다.  
```python
    print('wrong')    
```
<br> 
<br> 
* * *
문제 조건을 충족했다.  
<br> 
<br> 
* * *
### 예제 10단계, 3053번, "택시 기하학", 수학, 기하학  
[백준 3053번 문제](https://www.acmicpc.net/problem/3053)  
**해결책**  
```python
import math

R = int(input())

print(f"{math.pi*R*R:.6f}")
print(f"{2*R*R:.6f}")
```
<br> 
<br>
반지름 R이 주어지면  
첫째 줄에 유클리드 기하학에서 반지름 R인 원의 넓이,  
둘째 줄에 택시 기하학에서 반지름 R인 원의 넓이를 출력해야 한다.  
예제 출력을 확인하면 소수점 6번째 자리까지 출력해야 한다.  
<br> 
<br> 
* * *
택시 기하학에서 원의 정의는 유클리드 기하학에서 원의 정의와 같다고 한다.  
>원: 평면상의 어떤 점에서 거리가 일정한 점들의 집합  

택시 기하학과 유클리드 기하학은 **거리**의 정의가 다르다.  
<br> 
택시 기하학에서 두 점 T1(x1, y1), T2(x2, y2) 사이의 거리는 다음과 같다.  
거리 = \|x1-x2\| + \|y1-y2\|  
<br>
유클리드 기하학에서 두 점 T1(x1, y1), T2(x2, y2) 사이의 거리는 다음과 같다.  
거리 = ((x1-x2)^2 + (y1-y2)^2)^(1/2)  
<br>
거리의 정의가 다르므로 원의 모양이 다를 것이다.  
문제 풀이를 시작하자.  
<br> 
<br> 
* * *
원의 반지름을 구할 때 파이를 사용하므로 math를 import 한다.  
반지름을 입력받아 R에 저장한다.  
```python
import math

R = int(input())
```
<br> 
<br> 
* * *
먼저 유클리드 기하학에서 반지름이 R인 원의 넓이를 구하자.  
<br>
유클리드 기하학에서 원은 평면상의 어떤 점에서 거리가 일정한 점들의 집합이다.  
<br>
유클리드 기하학의 거리의 정의를 살펴보고,  
원점에서 거리가 일정한 점들의 집합의 함수를 살펴보자.  
<br>
유클리드 기하학의 두 점 T1(x1, y1), T2(x2, y2) 사이의 거리  
거리 R = ((x1-x2)^2 + (y1-y2)^2)^(1/2)  
<br> 
거리가 상수 R로 일정하니 R을 대입,  
x1과 y2에 원점 (0,0)을 대입,  
x2와 y2에 x와 y를 대입하면  
<br> 
x^2 + y^2 = R^2  
<br> 
초중고등학교에서 배우던 원의 방정식이 나온다.  
이러한 원의 넓이는 (원주율 파이)\*(반지름)^2이다.  
파이썬에서 원주율 파이는 math.pi이다.  
소수점 6번째 자리까지 출력해야 하므로  
f-string 문자열 포매팅 방법을 이용하고 큰따옴표 안에 {변수:.6f}를 입력한다.  
```python
print(f"{math.pi*R*R:.6f}")
```
<br> 
<br> 
* * *
택시 기하학에서 반지름이 R인 원의 넓이를 구하자.  
택시 기하학에서 원의 정의는 유클리드 기하학과 같이, 평면상의 어떤 점에서 거리가 일정한 점들의 집합이다.  
<br>
마찬가지로  
택시 기하학의 거리의 정의를 살펴보고,  
원점에서 거리가 일정한 점들의 집합의 함수를 살펴보자.  
<br>
택시 기하학의 두 점 T1(x1, y1), T2(x2, y2) 사이의 거리  
거리 = \|x1-x2\| + \|y1-y2\|  
<br>
거리가 상수 R로 일정하니 R을 대입,  
x1과 y2에 원점 (0,0)을 대입,  
x2와 y2에 x와 y를 대입하면  
<br>
\|x\| + \|y\| =  R  
<br>
택시 기하학에서 원은  
유클리드 기하학에서 각 변이 축과 45도 각도를 이루고, 대각선의 길이가 2R인 정사각형의 형태를 보인다.  
이 정사각형은  
(R, 0), (0, R), (-R, 0), (0, -R)이 네 꼭짓점이다.  
<br>
이 정사각형의 한 변의 길이는 R\*(2^(1/2))이고,  
넓이는 2\*R^2이다.  
<br>
택시 기하학의 원의 넓이도 소수점 6번째 자리까지 나타내야 하므로   
아래와 같이 f-string 문자열 포매팅과 {변수:.6f}를 사용한다.  
<br>
```python
print(f"{2*R*R:.6f}")
```
<br> 
<br> 
* * *
문제 조건을 충족했다.  
<br> 
<br> 
* * *
### 예제 11단계, 1002번, "터렛", 수학, 기하학  
[백준 1002번 문제](https://www.acmicpc.net/problem/1002)  
**해결책**  
```python
# 메모리 31312KB 시간 76ms
import sys
import math

T = int(sys.stdin.readline())

for i in range(T):
    x1, y1, r1, x2, y2, r2 = map(int, sys.stdin.readline().split())
    if x1 == x2 and y1 == y2:
        if r1 == r2:
            print(-1)
        else:
            print(0)
    else:
        xy = math.sqrt((x2-x1)**2 + (y2-y1)**2)
        rr = r1 + r2 
        if xy == rr or xy == (r2 - r1) or xy == (r1 - r2):
            print(1)       
        elif xy < (r2 - r1) or xy < (r1 - r2):
            print(0)
        elif xy > rr:
            print(0)
        else:
            print(2)
```
<br> 
<br>
첫째 줄에 테스트 케이스의 개수가 주어지고,  
테스트 케이스마다 두 원의 x, y 좌표와 반지름이 주어지면  
두 원이 몇 개의 점에서 만나는지 출력해야 한다.  
무한대의 점에서 만난다면 -1을 출력해야 한다.  
<br> 
<br> 
* * *
반복문에서 입력받아야 하므로 sys.stdin.readline()이 필요해, sys를 import한다.  
거리를 계산할 때 루트, math.sqrt()가 필요하므로 math를 import한다.  
(루트 대신 \*\*(1/2) 사용해도 된다.)  
```python
import sys
import math
```
<br> 
<br> 
* * *
테스트 케이스의 개수를 입력받아 T에 저장한다.  
for-range() 함수로 반복문을 T번 반복한다.  
x1, y1, r1, x2, y2, r2를 공백을 기준으로 입력받아 정수형으로 변환하고 저장한다.  
```python
T = int(sys.stdin.readline())

for i in range(T):
    x1, y1, r1, x2, y2, r2 = map(int, sys.stdin.readline().split())
```
<br> 
<br> 
* * *
두 원의 중심이 동일할 때(if문, x1 == x2 and y1 == y2)  
두 반지름의 길이가 같다면(if문, r1 == r2)  
두 원이 일치하므로 무한대의 점에서 만나, -1을 출력한다.   
<br> 
두 반지름의 길이가 같지 않다면(else)  
동심원 상태로, 접점이 없으므로 0을 출력한다.  

```python
    if x1 == x2 and y1 == y2:
        if r1 == r2:
            print(-1)
        else:
            print(0)
```
<br> 
<br> 
* * *
두 원의 중심이 동일하지 않을 때(else)  
<br> 
두 점 사이의 거리 xy를 구한다.  
두 반지름의 합 rr를 구한다.   
<br> 
두 원이 외접하거나 내접할 때(if)  
외접 : xy == rr  
내접 : == (r2 - r1) or xy == (r1 - r2)  
한 점에서 만나므로 1을 출력한다.   
<br> 
두 원이 외접하지 않고, 내접하지 않고(elif)  
한 원이 다른 원의 내부에 있을 때(elif)  
한 원이 다른 원 내부 : xy < (r2 - r1) or xy < (r1 - r2)  
접점이 없으므로 0을 출력한다.   
<br> 
위의 조건에 모두 False이고 한 원이 다른 원의 외부에 있을 때(elif)  
한 원이 다른 원의 외부에 존재 : xy > rr  
접점이 없으므로 0을 출력한다.  
<br> 
위의 조건에 모두 False일 때(else)  
남은 케이스는 두 원이 두 점에서 만날 때이다.  
두 원이 두 점에서 만나므로 2를 출력한다.  
<br> 
두 원이 두 점에서 만날 때를 수식으로 표현한다면,  
\|r1-r2\| < xy < r1 + r2  
에 해당한다.  
<br> 
```python
    else:
        xy = math.sqrt((x2-x1)**2 + (y2-y1)**2)
        rr = r1 + r2 
        if xy == rr or xy == (r2 - r1) or xy == (r1 - r2):
            print(1)       
        elif xy < (r2 - r1) or xy < (r1 - r2):
            print(0)
        elif xy > rr:
            print(0)
        else:
            print(2)
```
0을 출력하는 것은 elif 2개와 앞서 두 원의 중심이 같을 때 else 1개에 해당하고  
2를 출력할 때의 조건이 명확하므로(\|r1-r2\| < xy < r1 + r2)  
<br> 
지금처럼  
if (중심 같을 때)  
&nbsp;&nbsp;&nbsp;&nbsp;if (두 원 일치. -1)  
&nbsp;&nbsp;&nbsp;&nbsp;else (동심원. 0)  
else (중심 같지 않을 때)  
&nbsp;&nbsp;&nbsp;&nbsp;if (외접 또는 내접. 1)  
&nbsp;&nbsp;&nbsp;&nbsp;elif (한 원이 다른 원 내부에 존재. 0)  
&nbsp;&nbsp;&nbsp;&nbsp;elif (한 원이 다른 원 외부에 존재. 0)  
&nbsp;&nbsp;&nbsp;&nbsp;else (두 원이 두 점에서 만남. 2)  
<br> 
이렇게 구성하는 것이 아니라  
<br> 
if (중심 같고 두 원 일치. -1)  
elif (외접 또는 내접. 1)  
elif (두 원이 두 점에서 만남. 2)  
else (나머지. 0)  
<br> 
위와 같이 구성하는 편이 코드가 더 간단하다.  
조건이 명확하고 한 케이스로 나타낼 수 있는 것을 elif로 두고,  
조건이 여러 개인데 결과가 같은 것을 else로 두는 편이 묶어서 처리할 수 있다.  
<br> 
<br> 
* * *
문제 조건을 충족했다.  
<br> 
<br> 
* * *
