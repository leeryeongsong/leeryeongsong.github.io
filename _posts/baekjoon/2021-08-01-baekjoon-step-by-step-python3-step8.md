---
title:  "[8단계] 파이썬3으로 백준 단계별로 풀어보기- 기본 수학 1"
excerpt: "8단계 1712번, 2292번, 1193번, 2869"
toc: true
toc_sticky: true
toc_label: "백준 단계별로 풀어보기 8단계"
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
8단계 작성 기간 : 2021년 8월 1일 ~ 2021년 8월 
<br>
<br>
# 8단계, 기본 수학 1
[백준 단계별로 풀어보기 8단계](https://www.acmicpc.net/step/8)  
백준 사이트의 "단계별로 풀어보기" 문제 중 난이도 8단계 문제입니다.  
8단계에는 예제가 9개 있습니다.  
아래 소제목 이름은  
**(예제 n단계), (문제 번호), (문제 제목), (알고리즘 분류) 순서**입니다.  
<br>


### 예제 1단계, 1712번, "손익분기점", 수학, 사칙연산  
[백준 1712번 문제](https://www.acmicpc.net/problem/1712)  
**해결책**  
```python
# 성공. 메모리 29200KB 시간 72ms 
A, B, C = map(int, input().split())

if B>=C:
    print(-1)
else:
    print(A//(C-B)+1)
```
<br> 
<br>


<br> 
<br> 
* * *

<br> 
<br> 
* * *
**시행착오**  
```python
# 시간초과
A, B, C = map(int, input().split())
count = 1

if B>=C:
    print(-1)
else:
    cost = A + B
    earn = C
    while cost >= earn:
        count += 1
        cost += B
        earn += C
    print(count)
```

<br>
<br> 
### 예제 2단계, 2292번, "벌집", 수학,  
[백준 2292번 문제](https://www.acmicpc.net/problem/2292)  
**해결책**  
```python
N = int(input())

move = 1
endRoom = 1
gap = 0

while endRoom<N:
    move += 1
    gap += 6
    endRoom += gap

print(move)
```
<br> 
<br> 


<br> 
<br> 
* * *

<br> 
<br> 
* * *

<br>
<br>
### 예제 3단계, 1193번, "분수찾기", 수학, 구현  
[백준 1193번 문제](https://www.acmicpc.net/problem/1193)  
**해결책**  
```python
X = int(input())

end_num = 1
gap = 1
count = 1

while end_num<X:
    count += 1
    gap += 1
    end_num += gap

order = X - (end_num - gap) -1
if count % 2 == 0:
    print(f"{1+order}/{count-order}")
else:
    print(f"{count-order}/{1+order}")
```
<br> 
<br> 


<br> 
<br> 
* * *

<br> 
<br> 
* * *

<br>
<br>
### 예제 4단계, 2869번, "달팽이는 올라가고 싶다", 수학,  
[백준 2869번 문제](https://www.acmicpc.net/problem/2869)  
**시행착오(시간초과)**  
```python
# 값이 커지면 시간 오래 걸림
A, B, V =map(int, input().split())
R = 0
day = 0

while R < V:
    day += 1
    R += A
    if R >= V:
        break
    R -= B

print(day)
```
<br> 
<br> 


<br> 
<br> 
* * *
**해결책**  
```python
import math

A, B, V =map(int, input().split())

print(math.ceil((V-A)/(A-B))+1)
```
<br> 
<br> 

<br> 
<br> 
* * *

<br>
<br>
