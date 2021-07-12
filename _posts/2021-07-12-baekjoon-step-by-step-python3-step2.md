---
title:  "[2단계] 파이썬3으로 백준 단계별로 풀어보기- if문"
excerpt: "2단계 1330번"

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
2단계 작성 기간 : 2021년 7월 12일 ~ 
<br>
<br>
# 2단계, 입출력과 사칙연산
[백준 단계별로 풀어보기 2단계](https://www.acmicpc.net/step/2)  
백준 사이트의 "단계별로 풀어보기" 문제 중 난이도 2단계 문제입니다.  
2단계에는 예제가 5개 있습니다.  
아래 소제목 이름은  
**(예제 n단계), (문제 번호), (문제 제목), (알고리즘 분류) 순서**입니다.  
<br>


### 예제 1단계, 1330번, "두 수 비교하기", 수학, 구현, 사칙연산
[백준 1330번 문제](https://www.acmicpc.net/problem/1330)
#### 해결책 
```python
A, B = map(int, input().split())

if A>B:
  print(">")
elif A<B:
  print("<")
else:
  print("==")
```
