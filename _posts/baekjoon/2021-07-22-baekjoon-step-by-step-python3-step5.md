---
title:  "[5단계] 파이썬3으로 백준 단계별로 풀어보기- 1차원 배열"
excerpt: "5단계 10818번, 2562번, 2577번, 3052번, 1546번, 8958번, 4344번"
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
### 예제 5단계, 1546번, "평균", 수학, 사칙연산 
[백준 1546번 문제](https://www.acmicpc.net/problem/1546)  
**해결책1**  
```python
N = int(input())
score = list(map(int, input().split()))
new_score = [0 for i in range(N)]
# new_score = []이라고 하면, 리스트에 원소가 없는 상태에서 score[0] =1처럼 원소를 지정할 수 없으므로(IndexError: list assignment index out of range), 0을 N개 대입한다. 
M = max(score)

for i in range(N):
    new_score[i] = (score[i]/M)*100
average = sum(new_score)/N
print(average)

```
N에 시험 본 과목의 개수를 입력받는다.  
리스트 score에 세준이의 현재 성적을 공백을 기준으로 나누어 입력받는다.  
이후 새롭게 계산할 성적을 입력받을 리스트, new_score을 0으로 초기화한다.  
<br>
만약, new_score = [] 이렇게 빈 리스트로 선언하면  
이후 과정에서 new_score[0] = 1처럼 특정 인덱스에 원소를 지정할 수 없다.  
이를 해결하려면  
1) 리스트 길이를 지정하고 0으로 초기화하거나   
2) inset() 또는 append() 메소드를 사용하기  
해결책1은 1)의 방법을 사용했고  
아래 해결책2는 2)의 방법을 사용했다.  
<br>
문제로 돌아와서, 현재 성적 중 최댓값을 M에 대입한다.  
for-range문으로 과목 개수 만큼, for문을 반복한다.  
새로 계산한 과목 점수를 new_score[i]에 대입한다.  
새로 계산한 과목 점수(new_score)의 평균을 구하고, 이를 출력한다.  
<br>  

**해결책2**  
```python
N = int(input())
score = list(map(int, input().split()))
new_score = []
# new_score = []이라고 했으므로, 아래에 new_score.append(score[i]/M*100) 식을 사용했다.  
M = max(score)

for i in range(N):
    new_score.append(score[i]/M*100)
average = sum(new_score)/N
print(average)
```
문자열.append(추가할 원소) 메소드를 사용했다.  
문자열.insert(인덱스 번호, 추가할 원소) 메소드를 사용해도 된다.  

<br>
<br>
### 예제 6단계, 8958번, "OX퀴즈", 구현, 문자열  
[백준 8958번 문제](https://www.acmicpc.net/problem/8958)  
**해결책**  
```python
N = int(input())

for i in range(N):
    score = 0
    sum = 0
    test = input()
    test_list = list(test)
    for j in range(len(test_list)):
        if test_list[j] == "O":
            score += 1
        else: 
            score = 0
        sum += score    
    print(sum)
```
테스트 케이스의 개수를 N에 입력받는다.  
<br>
테스트 개수 N번 만큼 for문을 반복한다.  
score는 문제의 점수를 대입할 변수이고 sum은 해당 테스트 케이스의 점수를 합해서 저장할 변수이다.  
for문의 초반부에 score와 sum을 0으로 초기화한다.  
OX퀴즈 결과를 문자열로 입력받아서 test에 대입한다.  
test 문자열을 리스트 자료형으로 변환하여, test_list라고 이름붙인다.  
<br>
test_list의 길이만큼(= 문제 개수만큼) 두번째 for문을 반복한다.  
문제의 점수(score)는 그 문제까지 연속된 O의 개수이다.  
문제를 맞을 때마다 score에 1을 더하고, 문제를 틀리면 이전까지의 '연속된 O의 개수' 기록이 깨지므로 score를 0으로 초기화한다.   
그리고 각 문제의 점수를 sum 변수에 더하면 된다.  
즉,  
test_list의 j번째 원소가 "O"라면(if), score에 1을 더하고 if-else문을 빠져나와 sum에 score를 더한다.  
test_list의 j번째 원소가 "O"이 아니라면(="X"라면, else), score를 0으로 초기화하고 if-else문을 빠져나와 sum에 score를 더한다.  
<br>
for문을 test_list의 원소 개수만큼 반복하여 test_list의 마지막 원소까지 sum을 구하면,  
두번째 for문을 끝내고 sum을 출력한다.  
이제 입력받은 테스트 케이스 한 줄에 대한 점수를 출력했다.  
<br>
다음 OX퀴즈 결과도 입력받고, 동일한 과정을 거친다.  
<br>
이렇게 총 N번 반복하여(첫 번째 for문) 각 테스트 케이스의 점수를 모두 출력하면 된다.  
<br>
<br>
### 예제 7단계, 4344번, "최소, 최대", 수학, 구현  
[백준 4344번 문제](https://www.acmicpc.net/problem/4344)  
**해결책**  
```python
C = int(input())

for i in range(C):
    over_average_list = []
    N = list(map(int, input().split()))
    average = sum(N[1:])/N[0]
    for j in range(1, N[0]+1):
        if N[j]>average:
            over_average_list.append(N[j])
    over_average_student=len(over_average_list)/N[0]*100
    print(f"{over_average_student:.3f}%") # 문자열 포매팅 방법 f-string으로 소수점 자리수 조절하기
    # print("{:.3f}%".format(over_average_student)) # 문자열 포매팅 방법 str.format으로 소수점 자리수 조절하기
    # print(f"{round(over_average_student, 3)}%") # 이 문제에서는 round() 함수 사용 불가. 40.000%가 아니라 40.0%으로 결과 나온다.
```
테스트 케이스의 개수 C를 입력받는다.   
각 테스트 케이스에 동일한 연산과정을 적용하기 위해, for문 아래 함수를 C번 진행한다.   
<br>  
먼저 리스트 over_average_list를 초기화한다.  
리스트 over_average_list는 평균 점수보다 높은 점수 자료를 저장하는 변수이다.  
만약 for문 초기에 over_average_list를 초기화하지 않는다면,  
이전 테스트 케이스에서 사용한 over_average_list 자료가 그대로 남아서  
학생 수가 누적되는 결과가 나온다.   
<br>
예)  
문제에서 제시된 예제 입력1을 그대로 입력한다고 하자.  
첫번째 테스트 케이스에서  
5 50 50 70 80 100   
을 입력하면  
평균은 70점,  
over_average_list는 [80, 100]이 된다.  
<br>
**for문 초기에 over_average_list를 초기화하지 않는다면**,  
두번째 테스트 케이스  
7 100 95 90 80 70 60 50   
을 입력했을 때,   
평균 77.85714285714286점,  
over_aver_list는 [80, 100, 100, 95, 90, 80] (**오답**),   
평균을 넘는 학생의 비율은 85.714%이 된다(**오답**).    
<br>
**for문 초기에 over_average_list를 초기화하면**  
정상적으로  
over_aver_list는 [100, 95, 90, 80] (**정답**),  
평균을 넘는 학생의 비율은 57.143%이 된다(**정답**).  
<br>
다음 과정으로 넘어가면,  
리스트 N에 테스트 케이스 자료를 공백을 기준으로 입력받는다.   
N[0]에는 테스트 케이스의 학생 수를 입력받고,    
N[1]부터 끝까지, 테스트 케이스의 학생 점수를 입력받는다.   
점수의 평균값을 구할 때는    
sum() 함수와 리스트의 슬라이싱을 활용한다.  
sum() 함수는 여러 함수의 합계를 가져오는 함수이다.   
리스트를 슬라이싱하면, 리스트의 원하는 구간을 정해서 잘라낼 수 있다.    
리스트[숫자a:숫자b] : 리스트의 인덱스 숫자a부터 인덱스 숫자b-1까지 리스트를 가져온다.  
리스트[:숫자b] : 리스트의 처음(인덱스 0)부터 인덱스 숫자b-1까지 리스트를 가져온다.  
리스트[숫자a:] : 리스트의 인덱스 숫자a부터 리스트 끝까지 리스트를 가져온다.  
이를 활용하면  
평균값 = N[1]부터 리스트 N 끝까지의 값의 합/학생 수 N[0]  
average = sum(N[1:])/N[0] 이다.  
<br>
점수의 평균을 구했으니,    
평균을 넘는 학생의 점수를 리스트에 저장하는 단계로 넘어가자.  
for-range를 사용하여  
첫번째 학생 N[1]부터 마지막 학생의 자료까지 범위를 지정한다.  
마지막 학생은 N[0]번 째 학생일 것이고, 인덱스 N[0]에 해당하므로  
range() 함수에 입력할 때는 끝값으로 N[0]+1을 작성해야 한다.  
range(1, N[0]+1)  
<br>
예)  
문제에서 제시한 예제 입력1을 그대로 입력한다고 하자.  
첫 번째 테스트 케이스  
5 50 50 70 80 100  
N[0]에는 5가 저장되어 있다.  
마지막 학생은 5번째 학생이고, 인덱스 5에 해당하므로  
range() 함수에서 끝값이 6에 해당한다.  
<br>
for-range의 범위를 결정하였으니  
for문의 내용을 살펴보자.  
if문으로 N[j]가 평균 점수보다 높으면  
리스트 over_average_list의 마지막 순서에 값을 추가한다.  
<br>
for-range문을 끝내면  
변수 over_average_student에 평균을 넘긴 학생의 비율(%)을 저장한다.  
평균을 넘긴 학생의 비율은 평균을 넘긴 학생의 수를 학생의 수로 나누고 100을 곱하면 나온다.  
평균을 넘긴 학생의 수는 over_average_list의 길이이므로   
리스트의 길이를 구하는 len() 함수를 사용하여  
len(over_average_list)로 나타내면 된다.  
학생의 수는 N[0]이므로  
정리하면  
over_average_student=len(over_average_list)/N[0]\*100  
<br>
마지막으로 평균을 넘긴 학생의 비율을 반올림하여 소수점 셋째자리까지 출력해야한다.  
<br>
**소수점 자리수를 반올림하여 제한하는 방식**은 세가지가 있다.  
1) 문자열 포매팅 방법 f-string  
2) 문자열 포매팅 방법 str.format  
3) round 함수 (이 문제에서 적합하지 않음)  
<br>
**1) 문자열 포매팅 방법 f-string**  
f-string은 백준 단계별로 풀어보기 3단계 중 예제 7단계와 8단계에서 처음 사용해봤다.  
문자열 중간에 특정 값을 넣고 싶을 때 f-string 방법을 사용한다.  
넣고 싶은 값에 소수점 자리수가 필요 없으면    
print(f"문자열 {변수} 문자열")  
위와 같이 중괄호 안에 변수를 입력하면 되고  
<br>
이 문제처럼   
넣고 싶은 값에 소수점 자리수를 제한해야 한다면  
{변수:.Nf}  
방식을 사용한다.  

소수점 3자리까지 출력하려면  
{변수:.3f}  
를 입력하면 된다.  
<br>
**2) 문자열 포매팅 방법 str.format**  
f-string처럼 문자열 포매팅 방식이다.  
넣고 싶은 값에 소수점 자리수가 필요 없으면,  
값이 1개일 때  
print("문자열 {0}".format(변수))  
값이 2개 이상일 때  
print("문자열 {0} 문자열 {1} {2} 문자열".format(변수1, 변수2, 변수3))  
f-string은 중괄호 안에 변수를 직접 입력하지만,   
str.format은 중괄호 안에 인덱스를 입력한다.  
중괄호 안에 입력한 것이 없으면 format() 괄호 안의 변수를 순서대로 중괄호에 대입한다.  
<br>
넣고 싶은 값에 소수점 자리수를 제한해야 한다면  
{인덱스숫자:.Nf}  
방식을 사용한다.  
<br>
소수점 3자리까지 출력하려면  
{인덱스숫자:.3f}  
를 입력한다.  
<br>
**3) round 함수 (이 문제에서 적합하지 않음)**
round 함수는 반올림하는 함수가 맞고  
검색해보면 소수점 자리수 제한할 때 사용한다고 다른 사람들이 글을 써놨다.  
<br>
다른 사람이 소개한 글처럼  
round(반올림하려는 수[, 소수점 자리수])  
print(f"{round(over_average_student, 3)}%")으로 작성하고  
문제에서 제시한 예제입력1을 입력하면  
40.000%이 나와야하는 값이  
40.0%으로 나온다.  
<br>
문제에서 요구하는 조건을 충족하지 않으므로  
앞의 1), 2) 방식을 따라야한다.  
<br>
<br>
더 알아보니  
round() 함수는 끝자리가 0이면 표현되지 않는다는 글이 있고,  
round(반올림하려는 수[, 소수점 자리수])  
은 정확하지 않은 설명이다.  
<br>
파이썬 공식 문서를 살펴보면  
[파이썬 공식 문서](https://docs.python.org/ko/3/library/functions.html#round)
>round(number[, ndigits])  
>>number 를 소수점 다음에 ndigits 정밀도로 반올림한 값을 돌려줍니다. ndigits 가 생략되거나 None 이면, 입력에 가장 가까운 정수를 돌려줍니다. <br>
>>round() 를 지원하는 내장형의 경우, 값은 10의 -ndigits 거듭제곱의 가장 가까운 배수로 반올림됩니다; 두 배수가 똑같이 가깝다면, 반올림은 짝수를 선택합니다 (예를 들어, round(0.5) 와 round(-0.5) 는 모두 0 이고, round(1.5) 는 2 입니다). 모든 정숫값은 ndigits 에 유효합니다 (양수, 0 또는 음수). ndigits 가 생략되거나 None 이면, 반환 값은 정수입니다. 그렇지 않으면 반환 값은 number 와 같은 형입니다.  
<br>
>>일반적인 파이썬 객체 number 의 경우, round 는 number.__round__ 에 위임합니다.  
<br>
>>>참고 float에 대한 round() 의 동작은 예상과 다를 수 있습니다: 예를 들어, round(2.675, 2) 는 2.68 대신에 2.67 을 제공합니다. 이것은 버그가 아닙니다: 대부분의 십진 소수가 float로 정확히 표현될 수 없다는 사실로부터 오는 결과입니다. 자세한 정보는 부동 소수점 산술: 문제점 및 한계 를 보세요.  
<br>
round(반올림하려는 수[, 소수점 자리수])가 아니라  
round(반올림하려는 수[, 정밀도])이다.  
정밀도 3을 작성하면  
10^(-3) = 0.001의 가장 가까운 배수로 반올림한다.  
<br>
또한 round()의 동작은 사람들이 일반적으로 생각하는 통계적인 반올림이 아니라,  
Round half to even(또는 onvergent rounding, statistician's rounding, Dutch rounding, Gaussian rounding, odd–even rounding,[6] or bankers' rounding으로 불린다.)이라는 반올림 방법을 따른다.  
"10의 -ndigits 거듭제곱의 가장 가까운 배수로 반올림되는데, 두 배수가 똑같이 가깝다면 반올림은 짝수를 선택한다."   
<br>
float에 대한 round() 동작이 예상과 다르다는 내용도 있다.  
<br>
round()를 사용할 때는 이러한 점들을 신경써야할 것이다.   
<br>
<br>
글을 마무리하자면,  
round() 함수를 사용하면 40.000%를 40.0%으로 반환하는 문제점이 있으므로  
f-string이나 str.format 방식을 사용하여  
평균을 넘는 학생의 비율을 출력하면  
문제 조건을 충족할 수 있다.  

<br>
<br>
