---
title:  "[2단계] 파이썬3으로 백준 단계별로 풀어보기- if문"
excerpt: "2단계 1330번, 9498번, 2753번"

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





### 예제 2단계, 9498번, "시험 성적", 구현
[백준 9498번 문제](https://www.acmicpc.net/problem/9498)
#### 해결책 
```python
Score = int(input())
if Score>=90:
  print("A")
elif Score>=80:
  print("B")
elif Score>=70:
  print("C")
elif Score>=60:
  print("D")
else:
  print("F")
```
elif문을 여러 번 사용하여 점수 구간에 따라 성적을 출력한다.


### 예제 3단계, 2753번, "윤년", 수학, 구현
[백준 2753번 문제](https://www.acmicpc.net/problem/2753)
#### 해결책 
```python
Year = int(input())
if Year%4==0:
  if Year%100==0:
    if Year%400==0:
      print("1")
    else: 
      print("0")
  else:
    print("1")    
else:
  print("0")
```
4의 배수가 아니면 평년이므로 0 출력  
4의 배수가 맞고, 100의 배수가 아니면 윤년이므로 1 출력  
4의 배수가 맞고, 100의 배수이면, 400의 배수인가 확인. 맞으면 윤년이므로 1 출력, 아니면 평년이므로 0 출력
