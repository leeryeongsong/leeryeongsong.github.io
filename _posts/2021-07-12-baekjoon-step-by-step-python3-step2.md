---
title:  "[2단계] 파이썬3으로 백준 단계별로 풀어보기- if문"
excerpt: "2단계 1330번, 9498번, 2753번, 14681번, 2884번"
toc: true
toc_sticky: true
toc_label: "백준 단계별로 풀어보기 2단계"
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
  - 
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
2단계 작성 기간 : 2021년 7월 12일 ~ 2021년 7월 14
<br>
<br>
# 2단계, 입출력과 사칙연산
[백준 단계별로 풀어보기 2단계](https://www.acmicpc.net/step/2)  
백준 사이트의 "단계별로 풀어보기" 문제 중 난이도 2단계 문제입니다.  
2단계에는 예제가 5개 있습니다.  
아래 소제목 이름은  
**(예제 n단계), (문제 번호), (문제 제목), (알고리즘 분류) 순서**입니다.  
<br>
<br>

### 예제 1단계, 1330번, "두 수 비교하기", 수학, 구현, 사칙연산
[백준 1330번 문제](https://www.acmicpc.net/problem/1330)  
**해결책**  
```python
A, B = map(int, input().split())

if A>B:
  print(">")
elif A<B:
  print("<")
else:
  print("==")
```
A가 B보다 크면(if) > 출력  
if 조건이 틀리고, A<B이면(elif) < 출력  
위 조건 모두 틀리면(else) == 출력
<br>
<br>

### 예제 2단계, 9498번, "시험 성적", 구현
[백준 9498번 문제](https://www.acmicpc.net/problem/9498)  
**해결책**  
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
Score>=90이면(if) A출력  
위의 if 조건에 틀리고(Score<90), Score>=80이면(elif)...80<=Score<90, B출력  
위의 조건들 모두 틀리고(Score<80), Score>=70이면(elif)...70<=Score<80, C출력  
위의 조건들 모두 틀리고(Score<70), Score>=60이면(elif)...60<=Score<70, D출력  
위의 조건들 모두 틀리면(Score<60, else) F 출력
<br>
<br>

### 예제 3단계, 2753번, "윤년", 수학, 구현
[백준 2753번 문제](https://www.acmicpc.net/problem/2753)  
**해결책**  
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
<br>
<br>

### 예제 4단계, 14681번, "사분면 고르기", 수학, 구현, 
[백준 14681번 문제](https://www.acmicpc.net/problem/14681)  
**해결책**  
```python
x = int(input())
y = int(input())
if x>0:
  if y>0:
    print("1")
  else:
    print("4")
else:
  if y>0:
    print("2")
  else:
    print("3")
```
x가 양수일 때(if), 다시 if-else문으로 y양수이면(if) 제1사분면, 아니면(else) 제4사분면  
x가 양수가 아닐 때(else), 다시 if-else문으로 y양수이면(if) 제2사분면, 아니면(else) 제3사분면  
<br>
<br>

### 예제 5단계, 2884번, "알람 시계", 수학, 사칙연산
[백준 2884번 문제](https://www.acmicpc.net/problem/2884)  
**해결책**  
```python
H, M = map(int, input().split())
if M>=45:
  print(H, M-45)
elif H==0:
  print("23", M+15)
else:
  print(H-1, M+15)
```
입력 받은 시간('시'와 '분')에서 45분 앞당긴 값을 출력해야 한다.  
입력 받은 '분'이 45 이상이면(if) '시'은 그대로, '분'에서 45을 빼고 출력.  
if의 조건이 false, 즉, 입력 받은 '분'이 45 미만이면, '시'에서 1을 빼고 분은 \+60\-45이므로 \+15.  
그런데 '시'가 0일 때는 1을 뺐을 때 23시어야 하므로, 소수의 사례인 이것을 elif문에 넣는다.  
정리하면, if의 조건이 false('분'<45)이고 '시'가 0일 때(elif), 23시, '분'\+15 출력.  
위 조건에 모두 false('분'<45이고 '시'!=0, else)일 때, '시'\-1, '분'\+15 출력.  

간단한 조건으로 특정할 수 있는 소수의 사례는 else보다 elif에 넣는 것이 깔끔하다. else에는 조건 넣는 게 아니라, 위의 조건들 모두 false이기 때문.  
