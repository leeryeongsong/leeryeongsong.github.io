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
### 예제 3단계, 2577번, "숫자의 개수", 수학, 문자열, 구현  
[백준 2577번 문제](https://www.acmicpc.net/problem/2577)  
**해결책**  
```python
A = int(input())
B = int(input())
C = int(input())
ABC = str(A*B*C)

for i in range(10):
  print(ABC.count(str(i)))
```
A, B, C에 각각 숫자를 입력받는다.  
ABC 곱을 구하고 문자열 형태로 변환하여 ABC에 대입한다.  
for-range문으로 아래 과정을 10번 반복한다.  
문자열.count() 메소드는 문자열 안에서 괄호 안의 문자가 몇 개 있는지 알려주는 메소드이다.  
이때 괄호 안에 있는 문자는 문자열 형태여야 하므로, i가 아니라 str(i)를 괄호 안에 작성했다.    
str(i)을 작성하면 0부터 9까지 숫자가 문자열 형태로 메소드에 활용된다.  
str(i)이 아니라 "i"를 작성한다면 문자 i가 메소드에 사용되므로, 문제 조건에 맞지 않는다.  
<br>
<br>
### 예제 4단계, 3052번, "나머지", 수학, 사칙연산   
[백준 3052번 문제](https://www.acmicpc.net/problem/3052)  
**해결책1**  
```python
a = []
for i in range(10):
  a.append(int(input()))
  a[i] = a[i]%42

a_set = set(a)
print(len(a_set))
```
빈 리스트 a를 선언한다.
for-range문으로 아래 함수를 10번 반복한다.  
입력받은 숫자를 리스트 a 마지막 순서에 int 자료형으로 추가하고(a[i]에 대입됨),  
a[i]에 a[i]를 42로 나눈 나머지를 대입한다.  
for-range문이 끝나고, 리스트 a를 set 자료형으로 변환한 것을 a_set에 대입한다.  
set 자료형은 중복을 허용하지 않고, 순서가 없는 자료형이다.  
중복을 허용하지 않으므로 리스트 자료형을 set 자료형으로 변환하면, 리스트 요소의 중복을 쉽게 제거할 수 있다.  
리스트 요소의 중복을 제거한다면 서로 다른 값만 남게 된다.
따라서 마지막 단계로 a_set의 길이를 구하면, 문제에서 요구하는 '서로 다른 값의 개수'를 알 수 있다.

단, set을 사용하면 순서가 없어지므로, 순서를 지켜야하는 경우에는 반복문을 사용하면 된다.  
<br>

**해결책2**   
```python
a = []
new_a = []

for i in range(10):
  a.append(int(input()))
  a[i] = a[i]%42

for j in a:
  if j not in new_a:
    new_a.append(j)

print(len(new_a))
```
순서를 지켜야하는 경우, 반복문을 사용하는 방법이다.  
리스트 a의 모든 요소를 확인하면서, 해당 요소가 리스트 new_a에 없다면, 리스트 new_a의 마지막 순서에 요소를 추가한다.  
리스트 a가 [1, 1, 2, 1, 3, 4, 5, 1, 7, 8]라면,  
첫 번째로 나오는 1을 제외한 1이 모두 제거되는 것과 결과가 같다.  
리스트 new_a는 [1, 2, 3, 4, 5, 7, 8]이 된다.   
<br>
<br>
