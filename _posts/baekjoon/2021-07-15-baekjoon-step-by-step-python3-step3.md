---
title:  "[3단계] 파이썬3으로 백준 단계별로 풀어보기- for문"
excerpt: "3단계 2739번, 10950번, 8393번, 15552번, 2741번, 2742번, 11021번, 11022번, 2438번, 2439번, 10871번"
toc: true
toc_sticky: true
toc_label: "백준 단계별로 풀어보기 3단계"
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
3단계 작성 기간 : 2021년 7월 15일 ~ 2021년 7월 20일
<br>
<br>
# 3단계, for
[백준 단계별로 풀어보기 3단계](https://www.acmicpc.net/step/3)  
백준 사이트의 "단계별로 풀어보기" 문제 중 난이도 3단계 문제입니다.  
3단계에는 예제가 11개 있습니다.  
아래 소제목 이름은  
**(예제 n단계), (문제 번호), (문제 제목), (알고리즘 분류) 순서**입니다.  
<br>


### 예제 1단계, 2739번, "구구단", 수학, 구현, 사칙연산
[백준 2739번 문제](https://www.acmicpc.net/problem/2739)  
**해결책**  
```python
N = int(input())
for i in range(1, 10):
  print(N, "*", i, "=", N*i )
```
구구단 단 수 입력받아서 N에 대입하고  
for문과 range() 이용해서 구구단 출력.  
range(1, 10)은 1부터 9까지 연속된 숫자를 시퀀스(범위)로 만드는 함수.  
<br>
<br>

### 예제 2단계, 10950번, "A+B\-3", 수학, 구현, 사칙연산
[백준 10950번 문제](https://www.acmicpc.net/problem/10950)  
**해결책**  
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
for-range()사용하여 숫자쌍 입력받을 횟수 T번 설정,  
a, b 변수에 입력받은 숫자쌍 대입.  
리스트 A, B 각각에 a, b에 대입된 숫자를, 리스트 가장 마지막 순서에 추가.  
(두 개의 리스트 각각에, 띄어쓰기로 구분된 숫자 하나씩 넣는 방법을 못 찾아서, 징검다리로 변수 a, b 이용)  
모든 숫자쌍을 T번 입력받으면 다음 for-range()로 넘어간다.  
A와 B 숫자쌍의 합을 T번 출력.  
<br>
<br>

### 예제 3단계, 8393번, "합", 수학, 구현
[백준 8393번 문제](https://www.acmicpc.net/problem/8393)  
**해결책**   
```python
n = int(input())
sum = 0
for i in range(1, n+1):
  sum += i
print(sum)
```
n 입력받고, sum =0 선언.   
for문과 range() 이용해서 1부터 n까지 합 구한다.  
range(1, n\+1)은 1부터 n까지 연속된 숫자를 시퀀스(범위)로 만드는 함수.  
<br>
<br>

### 예제 4단계, 15552번, "빠른 A\+B", 수학, 구현, 사칙연산
[백준 15552번 문제](https://www.acmicpc.net/problem/15552)  
**해결책**  
```python
import sys
T = int(input())
for i in range(T):
  a, b = map(int, sys.stdin.readline().split())
  print(a+b)
```
테스트 케이스의 개수 T를 입력받는다.  
평소처럼 input() 함수를 사용하면 시간 초과라고 뜬다.  
반복문으로 여러 줄을 입력받을 때 input()을 사용하면 시간 초과가 발생할 수 있다.  
input()대신 sys.stdin.readline()을 쓰기 위해 sys를 import 한다.  
for문을 활용하여 a, b값에 입력받은 두 값을 대입하고, print로 두 값의 합을 출력한다.  
<br>
<br>
### 예제 5단계, 2741번, "N찍기", 구현
[백준 2741번 문제](https://www.acmicpc.net/problem/2741)  
**해결책**  
```python
N = int(input())

for i in range(1, N+1):
  print(i)
```
N 입력받고, for-range()로 1부터 N까지 출력한다.
<br>
<br>

### 예제 6단계, 2742번, "기찍N", 구현
[백준 2742번 문제](https://www.acmicpc.net/problem/2742)  
**해결책**  
```python
N = int(input())

for i in range(N, 0, -1):
  print(i)
```
N 입력받고, for-range()로 N부터 1까지 출력한다.  
range()를 활용하여 역순으로 출력할 때는 증가 폭을 음수로 지정하면 된다.  
range(시작, 끝, 증가 폭)  
<br>
<br>
### 예제 6단계, 2742번, "기찍N", 구현
[백준 2742번 문제](https://www.acmicpc.net/problem/2742)  
**해결책**  
```python
N = int(input())

for i in range(N, 0, -1):
  print(i)
```
N 입력받고, for-range()로 N부터 1까지 출력한다.  
range()를 활용하여 역순으로 출력할 때는 증가 폭을 음수로 지정하면 된다.
range(시작, 끝, 증가 폭)  
<br>
<br>
### 예제 7단계, 11021번, "A+B-7", 수학, 구현, 사칙연산
[백준 11021번 문제](https://www.acmicpc.net/problem/11021)  
**해결책**  
```python
import sys
T = int(input())
for i in range(1, T+1):
  a, b = map(int, sys.stdin.readline().split())
  print("Case #{0}: {1}".format(i, a+b)) # 파이썬 문자열 포매팅 방법 중 format 함수 활용
  # print("Case #%d: %d" %(i, a+b)) # 파이썬 문자열 포매팅 방법 중 % 포메팅 활용
  # print(f"Case #{i}:", a+b) # 파이썬 문자열 포매팅 방법 중 f-string 활용
```
예제 4단계와 같이, 반복문으로 여러 줄을 입력받을 때 input()을 사용하면 시간초과가 발생할 수 있으므로 sys.stdin.readline()을 사용해야 하고, 이를 위해 sys를 import 한다.  
테스트 케이스의 개수 T를 입력받고,  
for-range()으로 T번 반복하며  
a, b에 입력받은 값을 대입한다.  
여기까지는 예제 4단계와 동일하다.  
<br>
문제는, 예제가 출력하길 원하는 형식이 "Case #x: A+B"인 것..  
지금까지 사용한 방식은 다음과 같다.  
print()와 쉼표를 활용하여 
```python
print("Case #", "i", ":", a+b)
```
이 경우, 출력 결과는 다음과 같다.
```python
Case # 1 : 3
```
이렇게 print()와 쉼표를 사용하면 #와 x사이, x와 :사이 띄어쓰기가 들어가게 된다.
<br>
다른 방법을 찾다 보니, 파이썬 문자열 포매팅이라는 것을 알게 되었다.   
파이썬 문자열 포매팅 방법에는 format 함수, % 포매팅, f-string이 있다.
각각의 방법을 활용해서 문제를 해결했다.
<br>
자세한 내용은 다른 블로거의 아래 포스팅을 참고했다.  
[[python] 파이썬 format 함수 (문자열 포매팅 방법 1)](https://blockdmask.tistory.com/424)  
[[python] 파이썬 % 서식 기호 (문자열 포매팅 방법 2)](https://blockdmask.tistory.com/428)  
[[python] 파이썬 f-string (문자열 포매팅 방법 3)](https://blockdmask.tistory.com/429)
<br>
<br>
### 예제 8단계, 11022번, "A+B-8", 수학, 구현, 사칙연산
[백준 11022번 문제](https://www.acmicpc.net/problem/11022)  
**해결책**  
```python
import sys

T = int(input())

for i in range(1, T+1):
  a, b = map(int, sys.stdin.readline().split())
  print("Case #{0}: {1} + {2} = {3}".format(i, a, b, a+b)) # 파이썬 문자열 포매팅 방법 중 format 함수 활용
  # print("Case #%d: %d + %d = %d" %(i, a, b, a+b)) # 파이썬 문자열 포매팅 방법 중 % 포메팅 활용
  # print(f"Case #{i}: {a} + {b} = {a+b}") # 파이썬 문자열 포매팅 방법 중 f-string 활용
```
예제 7단계와 출력 양식만 다르다.  
파이썬 문자열 포매팅 방법인 format 함수, % 포매팅, f-string 각각을 활용하여 문제를 해결했다.  
3가지 방식 중 f-string은 어떤 변수가 문자열 안에서 어디 위치에 들어가는지 바로 확인할 수 있어서 편했다.  
문자열이 길어질수록 f-string의 강점이 커질 것 같다.  
<br>
<br>
### 예제 9단계, 2438번, "별 찍기-1", 구현
[백준 2438번 문제](https://www.acmicpc.net/problem/2438)  
**해결책**  
```python
N = int(input())
for i in range(1, N+1):
  print(i*"*")
```
"문자열"에 \*(숫자)를 같이 붙이면 (숫자)만큼 문자열이 반복된다.  
이를 활용하여 i번째 줄에 별 i개씩 찍히도록, 총 N줄 출력했다.  
<br>
<br>
### 예제 10단계, 2439번, "별 찍기-2", 구현
[백준 2439번 문제](https://www.acmicpc.net/problem/2439)  
**해결책**  
```python
N = int(input())
for i in range(1, N+1):
  print(str(i*"*").rjust(N))
```
예제 9단계 문제에서 오른쪽 정렬을 하면 된다.  
문자열.rjust(전체 자리수[, "공백에 대신하여 채울 문자"]) 형태로 활용한다.  
공백에 대신하여 채울 문자는 "" 또는 '' 따옴표 안에 넣어야 하고, 문자 또는 숫자 1개만 작성할 수 있다. <br>  
유사하게, 왼쪽 정렬을 할 때는  
문자열.ljust(전체 자리수[, "공백에 대신하여 채울 문자"]) 형태로 활용한다.  
<br>
<br>
### 예제 11단계, 10871번, "X보다 작은 수", 수학, 구현
[백준 10871번 문제](https://www.acmicpc.net/problem/10871)  
**해결책**  
```python
N, X = map(int, input().split())
A = list(map(int, input().split()))
for i in range(N):
  if A[i]<X:
    print(A[i], end=' ')
```
여러 문자를 리스트에 int형으로 입력받으려면  
a = list(map(int, input().split()) 사용하기  
<br>
줄바꿈 없이 파이썬 출력하고 싶으면  
print(출력할 내용, end='')  
end='' 이용하기  
띄어쓰기를 넣고 싶으면 ''사이에 띄어쓰기 한 칸 넣기.  
파이썬의 기본 print()함수는 print(출력할 내용, end='\\n')인데,  
평소 end='\\n' 부분이 생략되어 보이는 것이라고 한다.  
<br>
띄어쓰기로 리스트 출력하라는 제시문을 보고 파이썬 Numpy가 생각났지만  
검색해보니 백준에서는 Numpy를 사용하지 못한다고 한다.  
Numpy 말고도, 파이썬을 처음 설치했을 때 기본적으로 깔려 있는 표준 라이브러리가 아니라면 백준에서 사용할 수 없다고 한다.  
<br>
<br>



