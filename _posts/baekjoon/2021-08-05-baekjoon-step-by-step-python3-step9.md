---
title:  "[9단계] 파이썬3으로 백준 단계별로 풀어보기- 기본 수학 2"
excerpt: "9단계 1978번"
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
