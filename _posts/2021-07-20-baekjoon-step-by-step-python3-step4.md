---
title:  "[4단계] 파이썬3으로 백준 단계별로 풀어보기- while문"
excerpt: "4단계 10952번"
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
4단계 작성 기간 : 2021년 7월 20일 ~ 2021년 7월   
<br>
<br>
# 4단계, While문
[백준 단계별로 풀어보기 4단계](https://www.acmicpc.net/step/4)  
백준 사이트의 "단계별로 풀어보기" 문제 중 난이도 4단계 문제입니다.  
4단계에는 예제가 3개 있습니다.  
아래 소제목 이름은  
**(예제 n단계), (문제 번호), (문제 제목), (알고리즘 분류) 순서**입니다.  
<br>


### 예제 1단계, 10952번, "A+B=5", 수학, 구현, 사칙연산
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

