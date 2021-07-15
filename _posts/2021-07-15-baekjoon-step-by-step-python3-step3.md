---
title:  "[3단계] 파이썬3으로 백준 단계별로 풀어보기- for문"
excerpt: "3단계 2739번, 10950번"

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
3단계 작성 기간 : 2021년 7월 15일 ~ 2021년 7월 
<br>
<br>
# 3단계, 입출력과 사칙연산
[백준 단계별로 풀어보기 3단계](https://www.acmicpc.net/step/3)  
백준 사이트의 "단계별로 풀어보기" 문제 중 난이도 3단계 문제입니다.  
3단계에는 예제가 11개 있습니다.  
아래 소제목 이름은  
**(예제 n단계), (문제 번호), (문제 제목), (알고리즘 분류) 순서**입니다.  
<br>


### 예제 1단계, 2739번, "구구단", 수학, 구현, 사칙연산
[백준 2739번 문제](https://www.acmicpc.net/problem/2739)
#### 해결책 
```python
N = int(input())
for i in range(1, 10):
  print(N, "*", i, "=", N*i )
```
구구단 단 수 입력받아서 N에 대입하고  
for문과 range() 이용해서 구구단 출력.  
range(1, 10)은 1부터 9까지 연속된 숫자를 시퀀스(범위)로 만드는 함수.  


### 예제 2단계, 10950번, "A+B\-3", 수학, 구현, 사칙연산
[백준 10950번 문제](https://www.acmicpc.net/problem/10950)
#### 해결책 
```python
T = int(input())
A = []
B = []
for i in range(T):
  a, b = map(int, input().split())
  A.append(a)
  B.append(b)
for j in range(T):
  print(int(A[j])+int(B[j]))
```
테스트 케이스의 개수 T를 입력받는다.
A와 B를 빈 리스트로 선언한다.
for-range()사용하여 숫자쌍 입력 받을 횟수 T번 설정,  
a, b 변수에 입력 받은 숫자쌍 대입.  
리스트 A, B 각각에 a, b에 대입된 숫자를, 리스트 가장 마지막 순서에 추가.  
(두 개의 리스트 각각에, 띄어쓰기로 구분된 숫자 하나씩 넣는 방법을 못 찾아서, 징검다리로 변수 a, b 이용)  
모든 숫자쌍을 T번 입력 받으면 다음 for-range()로 넘어간다.
A와 B 숫자쌍의 합을 T번 출력.  
