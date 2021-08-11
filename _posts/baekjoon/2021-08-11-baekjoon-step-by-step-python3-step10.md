---
title:  "[10단계] 파이썬3으로 백준 단계별로 풀어보기- 재귀"
excerpt: "10단계 10872번, 10870번"
toc: true
toc_sticky: true
toc_label: "백준 단계별로 풀어보기 10단계"
categories:
  - baekjoon
tags:
  - 백준
  - 백준단계별로풀어보기
  - Algorithm
  - 파이썬3
  - Python3
  - 수학
  - 구현
  - 다이나믹 프로그래밍

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
10단계 작성 기간 : 2021년 8월 11일 ~ 2021년 8월 
<br>
<br>
# 10단계, 재귀
[백준 단계별로 풀어보기 10단계](https://www.acmicpc.net/step/10)  
백준 사이트의 "단계별로 풀어보기" 문제 중 난이도 10단계 문제입니다.  
10단계에는 예제가 4개 있습니다.  
아래 소제목 이름은  
**(예제 n단계), (문제 번호), (문제 제목), (알고리즘 분류) 순서**입니다.  
<br>


### 예제 1단계, 10872번, "팩토리얼", 수학, 구현  
[백준 10872번 문제](https://www.acmicpc.net/problem/10872)  
**해결책**  
```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n-1)

N = int(input())
print(factorial(N))
```
<br> 
<br>
이 문제를 for문으로도 풀 수 있지만  
10단계 주제가 '재귀'라서,  
재귀를 이용해서 풀어봤다.  
<br>
재귀에 대해서 검색해봤다.  
왕초보를 위한 Python: 쉽게 풀어 쓴 기초 문법과 실습 [A.1 함수의 재귀(recursion)](https://wikidocs.net/66)  
파이썬 코딩 도장 [31.1 재귀호출 사용하기](https://dojang.io/mod/page/view.php?id=2352)  
<br>
함수 안에서 함수 자기 자신을 호출하는 방식이 재귀 호출이라고 한다.  
<br> 
1. 함수에서 매개변수 n을 사용하여 정의하고(def f(n):)  
return에 '매개변수가 n-1인 함수 자기자신'을 포함하는 방식이 있다(return n + f(n-1)).  
return에 매개변수 n-1 이외에도 n-2와 함께 사용하거나, n//2 도 가능하다.  
<br> 
2. 함수에서 매개변수 n을 사용해서 정의하고(def f(n):)  
if문으로 n을 확인하여, 특정 조건일 때 종료하거나 특정한 값을 반환한다(if n == 1: return 1)  
n을 감소하고 f(n)을 호출한다.  
n이 if에서 찾는 특정한 값이 될 때까지 감소하면서, 함수를 불러오는 방식이다.  
<br>
문제 풀이로 넘어가자.  
<br> 
<br> 
* * *
N이 주어지면 N!를 출력해야 한다.  
<br> 
팩토리얼은 N부터 N-1, N-2, N-3, ... , 3, 2, 1  
N부터 1이 될 때까지 1씩 감소하면서 이들을 모두 곱하는 규칙성이 있다.  
<br> 
N! = N\*(N-1)\*(N-2)\*...\*3\*2\*1  
<br> 
<br> 
* * *
N으로 이루어진 식과 N-1으로 이루어진 식의 조합을 만들면 해결하기 쉽다.  
<br> 
위의 경우에는  
N! = N\*(N-1)!  
f(N) = N\*f(N-1) 으로 볼 수 있다.  
<br> 
<br> 
* * *
factorial(n) 함수를 정의한다.  
```python
def factorial(n):
```
<br> 
<br> 
* * *
if문으로 종료 조건을 만든다.  
종료 조건을 만들지 않으면 함수가 무한히 호출되려다가 최대 재귀 깊이를 초과하여 RecursionError가 발생한다.  
```python
    if n == 0:
        return 1
```
n에 저장된 값이 0과 같으면(if문) 1을 반환한다.  
n이 0일 때 더이상 함수를 호출하지 않고, 1이라는 상수값을 호출하여 재귀함수를 멈춘다.  
호출하는 값은 초기값으로 주어진 것을 활용할 때가 많다.  
<br> 
<br> 
* * *
위에서 확인했듯이  
f(N) = N\*f(N-1) 형태로 만든다.  
우변을 return에 넣으면 된다.  
```python
    return n * factorial(n-1)
```
<br> 
<br> 
* * *
factorial 함수 정의가 끝났다.  
<br> 
<br> 
* * *
숫자 N을 입력받아 N에 저장한다.   
factorial(N)을 print()함수로 출력한다.  
```python
N = int(input())
print(factorial(N))
```
<br> 
<br> 
* * *
문제 조건을 충족했다.   
<br> 
<br> 
* * *
### 예제 2단계, 10870번, "피보나치 수 5", 수학, 다이나믹 프로그래밍  
[백준 10870번 문제](https://www.acmicpc.net/problem/10870)  
**해결책**  
```python
def fibonacci(n):
    if n == 1:
        return 1
    elif n == 0:
        return 0
    return fibonacci(n-1) + fibonacci(n-2)

n = int(input())
print(fibonacci(n))
```
<br> 
<br>
마찬가지로 재귀를 이용하자.  
<br>
이번에는 문제에서 n과 n-1, n-2가 관련된 식을 제시했다.  
f(n) = f(n-1) + f(n-2)  
이렇게 바로 제시해주면 쉽게 문제를 풀 수 있다.  
<br> 
<br> 
* * *
피보나치 수열 함수 fibonacci(n)을 정의하자.  
if문으로 종결조건 및 초기값을 설정해준다.  
피보나치 수열의 초기값은 n이 1일 때 1, n이 0일 때 0이다.  
초기값이 2개이니 이들을 if와 elif로 설정한다.  
```python
def fibonacci(n):
    if n == 1:
        return 1
    elif n == 0:
        return 0
```
<br> 
<br> 
* * *
예제 1단계와 마찬가지로 return에는  
f(n) = f(n-1) + f(n-2)  
이 식의 우변을 넣어준다.  
```python
    return fibonacci(n-1) + fibonacci(n-2)
```
<br> 
<br> 
* * *
피보나치 수열 함수 fibonacci(n) 정의가 끝났다.  
<br> 
<br> 
* * *
숫자 n을 입력받아 n에 저장한다.  
fibonacci(n)을 print() 함수로 출력한다.  
```python
n = int(input())
print(fibonacci(n))
```
<br> 
<br> 
* * *
문제 조건을 충족했다.  
<br> 
<br> 
* * *
