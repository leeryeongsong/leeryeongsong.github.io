---
title:  "[1단계] 파이썬3으로 백준 단계별로 풀어보기- 입출력과 사칙연산"
excerpt: "1단계 2557번, 10718번, 10171번, 10172번, 1000번, 1001번, 10998번, 1008번, 10869번, 10430번, 2588번"
toc: true
toc_sticky: true
toc_label: "백준 단계별로 풀어보기 1단계"

categories:
  - baekjoon
tags:
  - 백준
  - Algorithm
  - 파이썬3
  - Python3
  - 구현
  - 입출력
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
1단계 작성 기간 : 2021년 7월 5일 ~ 
<br>
<br>
# 1단계, 입출력과 사칙연산
[백준 단계별로 풀어보기 1단계](https://www.acmicpc.net/step/1)  
백준 사이트의 "단계별로 풀어보기" 문제 중 난이도 1단계 문제입니다.  
1단계에는 예제가 11개 있습니다.  
아래 소제목 이름은  
**(예제 n단계), (문제 번호), (문제 제목), (알고리즘 분류) 순서**입니다.  
<br>

### 예제 1단계, 2557번, "Hello World", 구현
[백준 2557번 문제](https://www.acmicpc.net/problem/2557)  
**해결책**
```python
print("Hello World!")
```
출력 print() 함수를 이용하는 간단한 예제입니다.  
대소문자, 문자 개수 등 정확하게 출력해야 정답을 맞출 수 있습니다.  
문제 설명 또는 예제 출력1을 복사하여 소스 코드에 작성하는 것을 추천합니다.  
<br>  
<br>

### 예제 2단계, 10718번, "We love kriii", 구현
[백준 10718번 문제](https://www.acmicpc.net/problem/10718)   
**해결책** 
```python
print("강한친구 대한육군\n강한친구 대한육군")
```
예제 1단계 문제와 같이,  
출력 print() 함수를 이용하는 간단한 예제입니다.  
\n을 이용하면 줄 바꾸기가 가능합니다.  
한 줄씩 print() 함수를 사용해도 동일한 결과가 나옵니다.  
<br>
<br>

### 예제 3단계, 10171번, "고양이", 구현
[백준 10171번 문제](https://www.acmicpc.net/problem/10171)  
**해결책 1**
```python
print("\    /\ \n )  ( ')\n(  /  )\n \(__)|")
```
예제 2단계 문제와 비슷하다.  
예제 출력 1을 복사해서 print() 함수에 넣고,  
줄이 바뀌어야 하는 곳에는 \\n를 넣은 다음, 소스 코드를 한 줄로 만든다.  
<br>
이때, 고양이 오른쪽 귀에 해당하는 곳 /\에서, 이 역슬래시에 의해 \n이 제대로 작동되지 않는다(줄이 안 바뀌고 n이 출력된다).  
해결책으로 /\와 \n 사이에 띄어쓰기 한 칸을 넣어주면 된다.  
**해결책 2**
```python
print("""\    /\\
 )  ( ')
(  /  )
 \(__)|""")
```
여러 줄로 이루어진 문자열 출력의 경우, 문자열의 시작과 끝에 '''(작은따옴표 3개) 또는 """(큰따옴표 3개)를 붙여도 해결된다.  
문자열 안에 작은따옴표가 있으면 문자열 시작과 끝에 큰따옴표를 사용하고, 문자열 안에 큰따옴표가 있으면 문자열 시작과 끝에 작은따옴표를 사용한다.  
만약 작은따옴표 안에 작은따옴표를 쓰고 싶으면, 작은따옴표 앞에 역슬래시를 붙이면 된다.  
소스 코드에서 첫 번째 줄의 역슬래시를 출력하기 위해 역슬래시를 한 개 더 써줘야 한다.  
<br>
<br>

### 예제 4단계, 10172번, "개", 구현
[백준 10172번 문제](https://www.acmicpc.net/problem/10172)  
**해결책 1**
```python
print("|\_/|\n|q p|   /}\n( 0 )\"\"\"\ \n|\"^\"`    |\n||_/=\\\\__|")
```
예제 3단계의 해결책 1과 비슷하다. print() 한 줄로 만들기.  
줄 바뀌는 곳에 \n, 그리고 출력하고 싶은 모든 큰따옴표와 역슬래시 앞에 역슬래시 넣어주면 된다.  
즉, 역슬래시 2개를 연속해서 출력하고 싶으면 \\\\\\\\ 이렇게 4개를 작성할 것.
**해결책 2**
```python
print('''|\_/|
|q p|   /}
( 0 )"""\\
|"^"`    |
||_/=\\\\__|''')
```
예제 3단계의 해결책 2와 비슷하다. 여러 줄의 문자열 출력하기.  
문자열 안에 큰따옴표가 있으니까 문자열의 시작과 끝에 작은따옴표 3개를 붙인다.  
출력하고 싶은 모든 역슬래시 앞에 역슬래시 하나 작성하기.
<br>
<br>

### 예제 5단계, 1000번, "A\+B", 수학, 구현, 사칙연산
[백준 1000번 문제](https://www.acmicpc.net/problem/1000)  
**해결책 1**
```python
A, B = input().split()
A = int(A)
B = int(B)
print(A+B)
```
파이썬에서 한 줄에 두 개의 값을 입력받기  
변수1, 변수2 = input().split()  
split()의 ()안에 입력한 것이 없으므로, 공백을 기준으로 분리하여 변수1, 변수2에 입력한다.
<br>
input().split()으로 입력받은 값은 문자열이므로
숫자를 입력받기 위해서는,    
변수1 = int(변수1)  
이렇게 정수형으로 변환해야 한다.
**해결책 2**
```python
A, B = map(int, input().split())
print(A+B)
```
해결책 1처럼 input().split()으로 입력받고, 정수형으로 변환하는 과정이 번거로우면  
map()으로 한 줄에 해결할 수 있다.
<br>
<br>

### 예제 6단계, 1001번, "A\-B", 수학, 구현, 사칙연산
[백준 1001번 문제](https://www.acmicpc.net/problem/1001)  
**해결책 1**
```python
A, B = input().split()
A = int(A)
B = int(B)
print(A-B)
```
예제 5단계의 \+를 \-로 바꿔주면 된다.
**해결책 2**
```python
A, B = map(int, input().split())
print(A-B)
```
예제 5단계의 \+를 \-로 바꿔주면 된다.
<br>
<br>

### 예제 7단계, 10998번, "A×B", 수학, 구현, 사칙연산
[백준 10998번 문제](https://www.acmicpc.net/problem/10998)  
**해결책 1**
```python
A, B = input().split()
A = int(A)
B = int(B)
print(A*B)
```
**해결책 2**
```python
A, B = map(int, input().split())
print(A*B)
```
<br>
<br>

### 예제 8단계, 1008번, "A/B", 수학, 구현, 사칙연산
[백준 1008번 문제](https://www.acmicpc.net/problem/1008)  
**해결책 1**
```python
A, B = input().split()
A = int(A)
B = int(B)
print(A/B)
```
**해결책 2**
```python
A, B = map(int, input().split())
print(A/B)
```
<br>
<br>

### 예제 9단계, 10869번, "사칙연산", 수학, 구현, 사칙연산
[백준 10869번 문제](https://www.acmicpc.net/problem/10869)  
**해결책 1**
```python
A, B = map(int, input().split())
print(A+B)
print(A-B)
print(A*B)
print(int(A/B))
print(A%B)
```
A/B를 출력할 때 int()으로 자료형을 안 바꾸면, 틀렸습니다!라고 한다.  
자료형 안 바꾸면 소숫점 아래 결과까지 나오는데,  
예제 출력 1을 보니 출력 결과 정수형을 원했던 것...
예제 출력을 잘 살펴보자!!!
**해결책 2**
```python
A, B = map(int, input().split())
print(A+B)
print(A-B)
print(A*B)
print(A//B)
print(A%B)
```
파이썬에는 사칙연산에서 //가 몫을 의미한다.
<br>
<br>

### 예제 10단계, 10430번, "나머지", 수학, 구현, 사칙연산
[백준 10430번 문제](https://www.acmicpc.net/problem/10430)  
**해결책**
```python
A, B, C = map(int, input().split())
print((A+B)%C)
print(((A%C) + (B%C))%C)
print((A*B)%C)
print(((A%C)*(B%C))%C)
```
<br>
<br>

### 예제 11단계, 2588번, "곱셈", 수학, 사칙연산
[백준 2588번 문제](https://www.acmicpc.net/problem/2588)  
**해결책**
```python
A = int(input())
B = input()
BB = []
for i in str(B):
  BB.append(i)
print(A*int(BB[2]))
print(A*int(BB[1]))
print(A*int(BB[0]))
print(A*int(BB[2])+10*A*int(BB[1])+100*A*int(BB[0]))
```




