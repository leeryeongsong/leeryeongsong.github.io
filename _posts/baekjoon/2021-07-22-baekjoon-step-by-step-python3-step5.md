---
title:  "[5단계] 파이썬3으로 백준 단계별로 풀어보기- 1차원 배열"
excerpt: "5단계 10818번, 2562번"
toc: true
toc_sticky: true
toc_label: "백준 단계별로 풀어보기 5단계"
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
5단계 작성 기간 : 2021년 7월 22일 ~ 2021년 7월 
<br>
<br>
# 5단계, 1차원 배열  
[백준 단계별로 풀어보기 5단계](https://www.acmicpc.net/step/5)  
백준 사이트의 "단계별로 풀어보기" 문제 중 난이도 5단계 문제입니다.  
5단계에는 예제가 7개 있습니다.  
아래 소제목 이름은  
**(예제 n단계), (문제 번호), (문제 제목), (알고리즘 분류) 순서**입니다.  
<br>


### 예제 1단계, 10818번, "최소, 최대", 수학, 구현  
[백준 10818번 문제](https://www.acmicpc.net/problem/10818)  
**해결책**  
```python
N = int(input())
n = [0 for i in range(N)]
n = list(map(int, input().split()))
print(min(n), max(n))
```
정수의 개수 N을 입력받는다.  
리스트 n의 길이를 N으로 지정하고, 0으로 초기화한다.(필수는 아님)  
n에 공백으로 구분된 숫자 N개를 대입한다.  
최솟값, 최댓값을 구하는 함수인 min()과 max()를 이용하여 리스트n의 최솟값 최댓값을 공백으로 구분해 출력한다.  
<br>
<br>
### 예제 2단계, 2562번, "최댓값", 구현  
[백준 2562번 문제](https://www.acmicpc.net/problem/2562)  
**해결책**  
```python
N = []
Max = 0
MaxNum = 0
for i in range(9):
  N.append(int(input()))
for i in range(9):
  if Max==0 or Max<=N[i]:
    Max = N[i]
    MaxNum = i+1
  else:
    continue
print(Max)
print(MaxNum)
```
빈 리스트 N을 선언한다.  
Max와 MaxNum(최댓값 위치)를 0으로 선언한다.  
for문을 사용하여 순서대로 9개의 숫자를 int형으로 입력받고  
append()함수로 리스트 N의 마지막 순서에 추가한다.  
for문을 사용하여 숫자와 Max를 9번 비교한다.  
Max가 0이거나 Max보다 숫자가 크면 Max에 숫자를 대입하고 MaxNum에 i+1을 대입한다.  
그렇지 않다면(else, Max가 숫자보다 크면) continue를 이용하여 for문 다음 순서로 넘어간다.  
for문이 끝나고  
첫째 줄에 Max,  
둘째 줄에 MaxNum을 출력한다.  
<br>
<br>
