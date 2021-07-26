---
title:  "[6단계] 파이썬3으로 백준 단계별로 풀어보기- 함수"
excerpt: "6단계 15596번"
toc: true
toc_sticky: true
toc_label: "백준 단계별로 풀어보기 6단계"
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
  - 브루트포스알고리즘
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
6단계 작성 기간 : 2021년 7월 25일 ~ 2021년 7월 26일
<br>
<br>
# 6단계, 함수
[백준 단계별로 풀어보기 6단계](https://www.acmicpc.net/step/5)  
백준 사이트의 "단계별로 풀어보기" 문제 중 난이도 6단계 문제입니다.  
6단계에는 예제가 3개 있습니다.  
아래 소제목 이름은  
**(예제 n단계), (문제 번호), (문제 제목), (알고리즘 분류) 순서**입니다.  
<br>


### 예제 1단계, 15596번, "정수 N개의 합", 수학, 구현, 사칙연산  
[백준 15596번 문제](https://www.acmicpc.net/problem/15596)  
**해결책**  
```python
def solve(a):
    ans = int(sum(a))
    return ans

"""
def solve(a:list) -> int:
    ans = sum(a)
    return ans
"""
```

파이썬에서 사용사 지정 함수를 정의하려면  
```python
def 함수이름(매개변수):
    <수행할 명령>
    <수행할 명령>
    return 반환값
```
위와 같이 작성한다.  

정수 n개가 리스트 a로 주어지면   
정수 n개의 합을 구하기 위해  
sum(a)을 int 자료형으로 변환하여 ans에 대입하고  
ans을 반환하는 함수를 작성한다.  

파이썬 3.6부터 매개변수의 자료형과 반환값의 자료형을 미리 지정할 수 있다.  
이를 정적 타입 선언이라고 한다.  
아래와 같이 활용할 수 있다.  
```python
def solve(a:list) -> int:
```
매개변수 a가 list 자료형이고, 반환값이 int 자료형이라는 뜻이다.  
반환값이 int형이라고 미리 지정하였으므로,  
sum(a)을 int 자료형으로 변환하는 과정이 필요하지 않다.  

정적 타입 선언을 사용하면 특정 오류를 미리 자동적으로 잡아낼 수 있다고 한다.  
더 자세한 내용은 다음 내용으로 공부하고 있다.  
[Python 3.6에서 정적 타입 선언 사용하기](https://blog.naver.com/PostView.nhn?blogId=passion053&logNo=221070020739&categoryNo=27&parentCategoryNo=26&viewDate=&currentPage=1&postListTopCurrentPage=1&from=postView)

<br>
<br>
### 예제 2단계, 4673번, "셀프 넘버", 수학, 구현  
[백준 4673번 문제](https://www.acmicpc.net/problem/4673)  
**해결책**  
```python
# set을 사용하여 풀이. 시간이 더 짧게 나온다.
# 메모리 29968KB 시간 92ms 코드 길이 216B
def d(n):
    n_list = list(map(int, str(n)))
    dn = n + sum(n_list)
    return dn

dn_set = set()

for i in range(1, 10001):
    dn_set.add(d(i))

for j in range(1, 10001):
    if j not in dn_set:
        print(j)

"""
# list를 사용하여 풀이. 시간이 더 길게 나온다.
# 메모리 29452KB 시간 1144ms 코드 길이 251B
def d(n):
    n_list = list(map(int, str(n)))
    dn = n + sum(n_list)
    return dn

dn_list = []

for i in range(1, 10001):
    if d(i) not in dn_list:
        dn_list.append(d(i))

for j in range(1, 10001):
    if j not in dn_list:
        print(j)
"""
```
<br>
문제를 읽고, d(n)의 n에 1부터 대입해봤다.
|n|d(n)|d(d(n))|
|---|---|---|
|1|2|4|
|2|4|8|
|2|6|12|
|4|8|16|
|5|10|11|
|6|12|15|
|7|14|19|
|8|16|23|
|9|18|27|
|10|11|13|
|11|13|17|
|12|15|21|
<br>
n을 d(n)의 생성자라고 부르고  
생성자가 없는 숫자를 셀프 넘버라고 부르며  
셀프 넘버에는 1, 3, 5, 7, 9, 20 등이 있다.  
<br>
위의 표와 함께 살펴보면  
자연수 중 d(n)의 여집합이 셀프 넘버에 해당하며  
n, d(n), d(d(n)), d(d(d(n)),...과 같이 무한 수열을 만들 수 있으나,  
모든 d(n)은 n에 포함되므로,   
셀프 넘버를 찾기 위해 d(d(n)) 등을 살펴볼 필요는 없다.  
<br>
따라서 10000 이하 자연수 n에 대한 d(n)를 모두 구하고  
10000이하 자연수 중 d(n)의 여집합을 구하면 그것이 셀프 넘버이다.  
<br>
<br>
문제 풀이로 들어가자.  
<br>
함수 d(n)를 정의하여 문제를 풀이한다.  
<br>
문제에서 주어진 d(n)은 다음과 같다.  
d(n)= n+(n의 각 자리수 합)  
<br>
**n의 각 자리수를 구하려면 숫자 n을 쪼개야 하므로**,  
```python
n_list = list(map(int, str(n)))  
```
위와 같은 코드를 작성한다.  
<br>
str(n)은 숫자 n을 문자열로 변환하는 역할이고,  
int는 정수형으로 변환하는 역할이다.  
map은 다음과 같이 작성하고,  
```python
map(함수, 반복 가능한 객체)
```
반복 가능한 객체의 요소를 지정된 함수로 처리하는 함수이다.  
>반복 가능한 객체의 예시로는 문자열, 리스트, 딕셔너리, 세트가 있으며,  
>요소가 여러 개 들어있고, 한 번에 하나씩 꺼낼 수 있는 객체이다.  
>[39.1 반복 가능한 객체 알아보기](https://dojang.io/mod/page/view.php?id=2405)  
<br>
따라서 map(int, str(n))은   
문자열 n의 각 요소를 int 자료형으로 변환하는 역할을 수행한다.  
<br>
그리고 n_list =list(map(int, str(n)))는  
문자열 n의 각 요소를 int 자료형으로 변환한 결과를, 리스트 자료형으로 n_list에 대입한다.  
<br>
위의 방법으로 숫자 n을 쪼개는 것까지 완료했다.  
<br>
dn은 n과 n의 각 자리수의 합이므로   
```python
dn = n + sum(n_list)
```
sum() 함수로 리스트 n_list의 모든 요소를 더하고, n을 더하여 dn을 완성한다.  
계산한 dn을 return으로 반환하면  
함수 d(n)의 정의는 끝났다.  
<br>
<br>
10000 이하의 dn을 저장할 dn_set을 빈 set으로 선언한다.  
생성자 n이 여러 개인 d(n)이 존재하므로, d(n)의 중복을 피하기 위해 set 자료형을 선택한다.   
<br>
for문으로 i를 1부터 10000까지 1씩 증가하면서 진행한다.  
i는 생성자에 해당하는 변수이다.  
d(i)를 dn_set에 추가한다.  
set 자료형에 원소를 추가할 때는 set.add() 메소드를 사용한다.  
for문이 끝나면  
10000 이하의 모든 d(n)을 dn_set에 저장한 것이다.  
<br>
셀프 넘버, 즉 10000 이하의 자연수 중 d(n)의 여집합을 구하자.  
이때 셀프 넘버를 작은 숫자부터 차례대로 출력하기 위해 for문을 사용한다.  
for문으로 j에 1부터 10000까지 1씩 증가하며 대입한다.  
j가 dn_set에 존재하지 않으면, 이는 셀프 넘버이므로 출력한다.  
for문이 끝나면  
10000 이하의 셀프 넘버를 한 줄에 하나씩 출력하는 것을 완료한 것이다.  
<br>
<br>
주석 처리한 아래쪽 소스 코드는  
set 자료형이 대신 list 자료형을 사용한 코드이다.  
set 자료형을 사용했을 때가 더 코드 진행 소요 시간이 짧게 나왔다.  
<br>
list를 사용할 때는   
빈 리스트를 선언할 때 대괄호 \[\]를 사용했고,  
list에 원소를 추가할 때 list.append() 메소드를 사용했다.  
그리고 list은 원소의 중복을 허용하므로  
if문을 사용하여 d(i)가 리스트 dn_list에 없을 때, dn_list에 추가했다.  
그 외에는 내용이 동일하다.  
<br>
<br>
dn을 모은 자료형에, 중복되는 dn이 있어도  
셀프 넘버는 dn의 여집합이므로  
셀프 넘버를 구하는 문제 해결에는 이상이 없다.  
<br>
<br>
### 예제 3단계, 1065번, "한수", 브루트포스 알고리즘  
[백준 1065번 문제](https://www.acmicpc.net/problem/1065)  
**해결책**  
```python

def is_it_hansu(x):
    x_list = list(map(int, str(x)))
    if len(x_list) <=2:
        return True
    else:
        d = x_list[1]-x_list[0]
        for i in range(2, len(x_list)):
            if d == x_list[i]-x_list[i-1]:
                continue
            else:
                return False
        return True

N = int(input())
hansu_list = []

for i in range(1, N+1):
    if is_it_hansu(i)==True:
        hansu_list.append(i)
    else:
        continue
print(len(hansu_list))
```
<br>
x가 한수인지 판별하는 함수를 만들고,  
숫자 N이 주어졌을 때,  
x가 한수인지 판별하는 함수를 활용하여  
N 이하의 한수를 모두 구하고, 그 개수를 출력하자.  
<br>
x가 한수인지 판별하는 함수의 이름은 is_it_hansu이다.
숫자 x를 쪼개서 x_list에 저장하는 방법은 위의 예제 2단계 문제에서 다뤘다.
<br>
if문으로  
x_list의 길이가 2 이하일 때,  
즉, x가 한 자리수 또는 두 자리수 숫자일 때는  
모두 한수이므로 True를 반환한다.  
양의 정수 x의 각 자리가 등차수열을 이루어야 한수인데,  
한 자리수 또는 두 자리수 숫자는 모든 숫자가 등차수열을 만족하므로 True이다.  
<br>
x_list의 길이가 2 이하가 아닐 때(else),  
즉, x가 세 자리수 이상일 때는  
등차 수열의 공차 d에 x_list\[1\]-x_list\[0\]을 대입하고,  
for문과 if문으로  
2이상의 모든 인덱스에 대해  
인접한 두 숫자(인덱스 i와 i-1)의 차이가 d와 같으면(if) continue로 넘어가고,  
d와 다르면(else) x는 한수가 아니므로 False를 반환한다.  
for문과 if의 중간에 False로 끝나지 않고, 모든 i에 대해 continue 진행했으면  
x는 한수이므로 True를 반환한다.  
<br>
이제 x가 한수인지 판별하는 함수를 정의했다.  
<br>
<br>
N을 입력받고  
N 이하의 한수를 구하자.  
한수를 저장할 리스트 hansu_list를 빈 리스트로 선언했다.  
<br>
for문으로  
i에 1부터 N까지 1씩 증가하며 대입하고,  
i가 한수인지 is_it_hansu(i)로 판별한다.  
if문으로  
is_it_hansu(i)가 True이면(if) i를 hansu_list에 추가한다.  
is_it_hansu(i)가 True가 아니면(else, False), continue로 넘어간다.  
<br>
for문을 끝내면  
N 이하의 한수를 모두 구하여 hansu_list에 저장한 것이다.  
<br>
hansu_list의 길이를 출력하면 문제 조건을 모두 충족한다.  
<br>
<br>
이 문제의 알고리즘에 "브루트포스 알고리즘" 항목이 있다.  
브루트포스 알고리즘이 무엇인지 찾아보니,
모든 경우의 수를 모두 탐색하면서 요구조건에 충족되는 결과만을 가져오는 방식을 의미한다고 한다.
아래의 글이 잘 설명하고 있다.
[알고리즘 기법[전체 탐색] - 브루트 포스(brute force)](https://hcr3066.tistory.com/26)
