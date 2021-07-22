---
title:  "[4단계] 파이썬3으로 백준 단계별로 풀어보기- while문"
excerpt: "4단계 10952번, 10951번, 1110번"
toc: true
toc_sticky: true
toc_label: "백준 단계별로 풀어보기 4단계"
categories:
  - baekjoon
tags:
  - 백준
  - 백준단계별로풀어보기
  - Algorithm
  - 파이썬3
  - Python3
  - 구현
  - 사칙연산
  - 수학
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
4단계 작성 기간 : 2021년 7월 20일 ~ 2021년 7월 21일   
<br>
<br>
# 4단계, While문
[백준 단계별로 풀어보기 4단계](https://www.acmicpc.net/step/4)  
백준 사이트의 "단계별로 풀어보기" 문제 중 난이도 4단계 문제입니다.  
4단계에는 예제가 3개 있습니다.  
아래 소제목 이름은  
**(예제 n단계), (문제 번호), (문제 제목), (알고리즘 분류) 순서**입니다.  
<br>


### 예제 1단계, 10952번, "A+B-5", 수학, 구현, 사칙연산
[백준 10952번 문제](https://www.acmicpc.net/problem/10952)  
**해결책**  
```python
while True:
  a, b = map(int, input().split())
  if a!=0 and b!=0:
    print(a+b)
  else:
    break
```
파이썬의 무한 루프를 while문으로 만들 수 있다.  
while문의 조건문이 True이므로 항상 참이 된다.  
그러므로 while문 안에 있는 문장들은 무한하게 수행될 것..  
입력받은 수 모두 0이 아닐 때 while문을 수행하고,  
조건에서 벗어나면 break로 while문을 끝낸다.  
<br>
<br>
### 예제 2단계, 10952번, "A+B-4", 수학, 구현, 사칙연산
[백준 10951번 문제](https://www.acmicpc.net/problem/10951)  
**해결책**  
```python
"""
while True:
  a, b = map(int, input().split())
  print(a+b)
 런타임 에러(EOFError)

while True:
  a, b = map(int, input().split())
  if 0<a<10 and 0<b<10: 
    print(a+b)
  else:
    break
 런타임 에러(EOFError)
"""

while True:
  try:
    a, b = map(int, input().split())
    print(a+b)
  except:
    break
```
위의 2가지 방법으로 코드를 작성하면 런타임 에러(EOFError)가 뜬다.  
에러를 해결하기 위해서 try except문을 사용했다.  
자세한 내용은 더 공부가 필요하다.    
<br>
<br>
### 예제 3단계, 1110번, "더하기 사이클", 수학, 구현
[백준 1110번 문제](https://www.acmicpc.net/problem/1110)  
**해결책**  
```python
N = int(input())
M = int
n = []
count = 0

if 0<=N<10:
  N = N*10

n = [N//10, N%10]

while N!=M:
  P = n[0]+n[1]  
  M = n[1]*10 + P%10
  n = [M//10, M%10]
  count+=1

print(count)
```
문제내용이 앞선 문제보다 길지만, 차근차근 풀면 된다.  
우선 N을 입력받는다.  
문제 조건처럼 N이 0 이상 10미만이면 0을 붙여 두 자리수로 만들기 위해, 10을 곱했다.    
<br>
N의 십의 자리수를 n\[0\]에, N의 일의 자리수를 n\[1\]에 대입했다.  
<br>
N의 십의 자리수를 구하려면 //(버림 나눗셈, floor division)를 이용한다.  
//은 나눗셈 후 소수점 이하를 버리는 연산자이다.  
왜 /(나눗셈)말고 //를 사용하냐면,  
26/10 = 2.6  
26//10 = 2  
30/10 = 3.0  
30//10 = 3  
//를 이용해야 십의 자리수만 정수형으로 구할 수 있기 때문이다.  
<br>
N의 일의 자리수를 구하려면 %를 사용한다.  
%는 나눗셈 후 나머지를 구하는 연산자이다.  
<br>
이제 while문을 시작한다.  
N과 M이 다르면 while문을 이어간다.
M은 더하기 사이클 과정에서 구하는 '새로운 수'이다.
<br>
다음 단계로 N의 각 자리의 수를 더해서 P에 대입한다.  
처음 입력받은 N의 일의 자리 수를 십의 자리수로 갖고, P의 일의 자리 수를 일의 자리수로 갖는 새로운 수를 M에 대입한다.  
새로운 수를 십의 자리수와 일의 자리수로 쪼개서 리스트 n에 넣는다.  
여기까지 '더하기 사이클'을 1번 진행한 것이고, '더하기 사이클을 진행한 횟수=더하기 사이클 길이'인 count에 1을 추가한다.  
N과 M이 다르면 while문을 반복하고,
N과 M이 같아지면 문제가 요구하는 더하기 사이클 길이인 count를 출력한다.

<br>
<br>
