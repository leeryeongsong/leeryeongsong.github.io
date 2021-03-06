---
title:  "[7단계] 파이썬3으로 백준 단계별로 풀어보기- 문자열"
excerpt: "7단계 11654번, 11720번, 10809번, 2675번, 1157번, 1152번, 2908번, 5622번, 2941번, 1316번"
toc: true
toc_sticky: true
toc_label: "백준 단계별로 풀어보기 7단계"
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
  - 문자열
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
7단계 작성 기간 : 2021년 7월 27일 ~ 2021년 7월 31일
<br>
<br>
# 7단계, 문자열
[백준 단계별로 풀어보기 7단계](https://www.acmicpc.net/step/7)  
백준 사이트의 "단계별로 풀어보기" 문제 중 난이도 7단계 문제입니다.  
7단계에는 예제가 10개 있습니다.  
아래 소제목 이름은  
**(예제 n단계), (문제 번호), (문제 제목), (알고리즘 분류) 순서**입니다.  
<br>


### 예제 1단계, 11654번, "아스키 코드", 구현
[백준 11654번 문제](https://www.acmicpc.net/problem/11654)  
**해결책**  
```python
X = input()
print(ord(X))
```
알파벳 소문자, 대문자, 숫자 0-9 중 하나를 입력받아 X에 저장한다.  
이때, input() 함수는 입력받은 모든 데이터를 **문자열**로 취급한다.  
```python
X = input()
```
<br> 
<br> 
* * *
ord() 함수는 문자열 데이터를 아스키 코드로 변환하는 함수이다.  
```python
print(ord(X))
```
<br> 
<br> 
* * *
이 문제에서 다루지 않았지만   
chr() 함수는 아스키 코드를 문자열로 변환하는 함수이다.   
<br>
<br> 
### 예제 2단계, 11720번, "숫자의 합", 수학, 문자열, 사칙연산  
[백준 11720번 문제](https://www.acmicpc.net/problem/11720)  
**해결책**  
```python
N = int(input())
Num = input()
Num_list = list(map(int,Num))
print(sum(Num_list))
```
<br>
<br>
숫자의 개수를 입력받아 N에 저장한다.    
```python
N = int(input())
```
<br>
<br>
* * *
숫자 N개를 공백 없이 input()으로 입력 받아, 문자열 데이터로 Num에 저장한다.  
(input()은 입력받은 데이터를 모두 문자열로 취급한다.)  
```python
Num = input()
```
<br>
<br>
* * *
map() 함수를 이용하여 문자열 Num의 각 요소를 int형으로 변환하고,  
이를 list() 함수를 이용하여 리스트 자료형으로 변환하여,  
마지막으로 Num_list에 저장한다.  
```python
Num_list = list(map(int,Num))
```
이 과정으로 문자열로 입력받은 긴 숫자의 각 자리수가 쪼개져서   
정수형으로, 리스트 자료형 안에 저장되었다.  
예) 문자열 '1234567' -> \[1, 2, 3, 4, 5, 6, 7\]  
<br>
<br>
* * *
리스트 Num_list의 합을 sum() 함수로 구하여 출력한다.  
```python
print(sum(Num_list))
```

문제 조건을 충족했다.  
<br>
<br>

* * *
위 코드는 N을 입력받고 사용하지 않았다.
처음에 입력받은 N을 사용하려면, 다음의 방식을 쓸 수 있다.  
마지막 줄에  
```python
print(sum(Num_list))
```
를  
```python
print(sum(Num_list[:N]))
```
으로 바꾸면  
리스트 인덱스 0부터 인덱스 N-1까지의 합을 구하게 된다.  

<br>
<br>
### 예제 3단계, 10809번, "알파벳 찾기", 구현, 문자열
[백준 10809번 문제](https://www.acmicpc.net/problem/10809)  
**해결책**  
```python
S = input()

for i in range(97, 123):
    if chr(i) in S:
        for j in range(len(S)):
            if chr(i)==S[j]:
                print(j, end = ' ')
                break
    else:
        print(-1, end = ' ')
```
<br>
<br>
알파벳 소문자로 이루어진 단어를 입력받아 S에 저장한다.   
```python
S = input()
```
<br>
<br>
* * *
소문자 a부터 z까지 각각의 알파벳이 S에 포함되어 있으면  
처음 등장하는 위치를 출력하고  
해당 알파벳이 S에 포함되어 있지 않다면 -1를 출력해야 한다.  
<br>
<br>
* * *
**반복되는 함수를 수행하는 범위가 소문자 a부터 z까지 지정되어 있으므로 for문을 사용**한다.  
소문자 a의 아스키 코드는 97이고   
소문자 z의 아스키 코드는 122이며,   
함수 chr()으로 아스키 코드를 문자열로 변환하면...   
```python
for i in range(97, 123):
```
i가 97일 때 chr(i)는 chr(97), 즉 a를 의미하고,  
i가 98일 때 chr(i)는 chr(98), b를 가리킨다.   
for문의 마지막에는  
i가 122으로, chr(122)는 z를 의미한다.  
<br>
위와 같이 아스키 코드를 이용하면, 숫자 범위로 문자 범위를 지정하여 반복문을 수행할 수 있다.  
<br>
<br>
* * *
**문자 chr(i)가 문자열 S에 있다면(if), 처음 등장하는 위치를 출력하는 함수를 만들자.**  
```python
    if chr(i) in S:
```
for-range 문으로, 문자열 S의 길이만큼 for문을 반복하고  
i는 0부터 1씩 증가하므로  
문자열 왼쪽 끝(인덱스0)부터 오른쪽으로 문자열을 훑어간다.   
<br>
<br>
* * *
if문으로 chr(i)와 S\[j\]의 문자가 동일(==)할 때,  
S\[j\]의 인덱스인 j를 출력하고 break로 for문을 끝낸다.  
```python
        for j in range(len(S)):
            if chr(i)==S[j]:
                print(j, end = ' ')
                break
```
**j를 출력할 때, 다음 문자와 띄어쓰기로 구분**되어야 하므로  
print() 함수 소괄호 안에 end = ' '를 추가한다.  
<br>
평소 사용하는 파이썬 print() 함수는  
```python
print( , end = '/n') 
```
end = '/n'이 생략되어 있고, /n으로 인해 줄바꿈을 하고 있는 것이다.  
end = ''의 '' 작은따옴표 자리에 *출력하고 싶은 내용 바로 뒤에 붙일 문자*를 설정할 수 있다.  
<br>
또한,  
**인덱스 j를 출력하고 break로 for문을 끝내야  
chr(i)가 처음 등장하는 위치만 출력**할 수 있다.  
<br>
break로 for문을 끝내지 않는다면  
chr(i)가 등장하는 모든 인덱스가 출력된다.  
<br>
<br>
* * *
**문자 chr(i)가 문자열 S에 있지 않다면(else, S에 없다면)**  
-1을 출력하고,  
줄바꿈이 아니라 띄어쓰기로 다음 문자와 구분되어야 하므로  
print() 함수 소괄호 안에 end = ' '를 추가한다.  
```python
    else:
        print(-1, end = ' ')
```
<br>
<br>
* * *
문제 조건을 모두 만족했다.  
<br>
<br> 
### 예제 4단계, 2675번, "문자열 반복", 구현, 문자열
[백준 2675번 문제](https://www.acmicpc.net/problem/2675)  
**해결책**  
```python
T = int(input())
for i in range(T):
    P = ''
    R, S = input().split()
    R = int(R)
    for j in range(len(S)):
        P = P + S[j]*R
    print(P)
```
<br>
<br>
테스트 케이스의 개수를 입력받아 T에 저장한다.  
```python
T = int(input())
```
<br>
<br>
* * *
각 테스트 케이스에 동일한 함수를 반복하므로 for문을 사용하고  
range(T)로, **for문을 T번 반복**한다.   
```python
for i in range(T):
```
<br>
<br>
* * *
**새로 만들 문자열 P를 빈 문자열로 초기화**한다.  
```python
    P = ''
```
이전의 테스트 케이스에서 만든 P가 남아있기 때문에,  
for문의 초반에 P를 초기화해야한다.  
<br>
<br>
* * *
**R와 S에 입력받은 문자를 저장**하는데, 
띄어쓰기를 기준으로 나눠서 R와 S에 저장하므로 split()를 덧붙인다.  
```python
    R, S = input().split()
```
input() 함수로 인해 R와 S는 문자열 str형으로 저장되었다.   
<br>
<br>
* * *
**R은 반복 횟수이므로 int() 함수를 사용하여 문자열에서 정수형으로 변환**한다.  
S는 그대로 문자열로 쓰일 것이므로 변환하지 않는다.  
```python
    R = int(R)
```
<br>
<br>
* * *
**새로운 P를 만들어야 한다.**  
문자열 S의 각 문자를 R번 반복하면 문자열 P가 된다.  
문자열에서 인덱스로 각 요소에 접근할 수 있지만, =로 새로운 값을 할당하거나 추가할 수 없으므로,  
새로운 P를 만들어야하며, +연산자로 문자열 P에 새로운 문자열을 이어붙이는 방식을 사용한다.  
<br> 
for문에 range(len(S))로 지정하면,  
j는 인덱스 0부터 문자열 S의 마지막 인덱스 숫자까지 1씩 증가한다.  
문자열 P에 S\[j\]\*R를 더하면  
인덱스 j의 문자 S\[j\]가 R번 반복되어, P의 오른쪽 끝에 추가된다.  
```python
    for j in range(len(S)):
        P = P + S[j]*R
```
<br>
<br>
* * *
for문이 끝나고  
문자열 P를 출력하면  
테스트 케이스 하나에 대해 요구하는 새로운 문자열 P를 출력한 것이다.  
```python
    print(P)
```
<br>
<br>
* * *
이후 과정으로  
다음 테스트 케이스를 입력받고, P를 출력할 것이다.  
<br>
<br>
* * *
문제 조건을 모두 충족했다.  
<br>
<br> 
### 예제 5단계, 1157번, "단어 공부", 구현, 문자열
[백준 1157번 문제](https://www.acmicpc.net/problem/1157)  
에러가 나온 코드도 작성했기에, '해결책'이 아니라 '코드(숫자)'로 소제목을 작성했다.  
**코드1**  
```python
# 메모리 31156KB 시간 392ms
words= input()
words_list = [0 for i in range(26)]
for i in words:
    if ord(i) <= 90:
        words_list[ord(i)-65] +=1
    else:
        words_list[ord(i)-97] +=1
words_list_max = max(words_list)
if words_list.count(words_list_max) == 1:
    words_list_max_index = words_list.index(words_list_max)
    print(chr(words_list_max_index+65))
else:
    print('?')
```
<br>
<br>
코드1에서는 대소문자를 구분하여 처리하고, 아스키 코드를 적극 활용했다.  
<br>
<br>
* * *
문자열을 입력받아 words에 저장하고,   
알파벳이 입력된 횟수를 저장하기 위한 리스트 words_list를 0으로 초기화했다.  
```python
words= input()
words_list = [0 for i in range(26)]
```
<br>
<br>
* * *
문자열 중 가장 많이 사용된 알파벳을 알고 싶은데, 대소문자 구분이 없다고 한다.   
<br>
**알파벳 ABC 순서대로 리스트 words_list에 각 알파벳의 입력 횟수를 저장**하자.  
대문자 A를 인식했을 때 리스트 words_list\[0]에 입력 횟수를 \+1 추가,  
소문자 a를 인식했을 때도 리스트 words_list\[0]에 입력 횟수를 \+1 추가하는 방식을 사용해보자.  
<br>
대문자 A의 아스키 코드는 65이고, 이후 알파벳 대문자는 순서대로 아스키 코드가 1씩 증가한다.  
소문자 a의 아스키 코드는 97이고, 이후 알파벳 소문자는 순서대로 아스키 코드가 1씩 증가한다.  
<br>
for문으로 words의 각 요소 i에 대해,  
if문으로  
문자열 i의 아스키 코드(ord(i))가 90이하라면(if) 알파벳 대문자므로, (아스키 코드-65)를 인덱스로 갖는 리스트 원소에 +1을 추가하여 저장한다.  
문자열 i의 아스키 코드(ord(i))가 90이하가 아니라면(else, 91이상) 알파벳 소문자이므로, (아스키 코드-97)를 인덱스로 갖는 리스트 원소에 +1을 추가하여 저장한다.  
```python
for i in words:
    if ord(i) <= 90:
        words_list[ord(i)-65] +=1
    else:
        words_list[ord(i)-97] +=1
```
이제 알파벳 ABC 순서대로, 각 알파벳의 입력 횟수를 리스트 words_list에 저장했다.  
<br>
<br>
* * *
**리스트 words_list의 최댓값**을 구하자.  
리스트 words_list의 최댓값을 max() 함수로 구하여 변수 words_list_max에 대입한다.  
```python
words_list_max = max(words_list)
```
<br>
<br>
* * *
**가장 많이 사용된 알파벳이 1개로 유일하다면(if)**,  
words_list_max와 같은 값을 갖는 원소의 개수가 1개와 같다.  
count() 메소드를 사용하면 소괄호 안의 자료가 리스트 안에 존재하는 개수를 알 수 있다.  
```python
if words_list.count(words_list_max) == 1:
```
<br>
<br>
* * *
**가장 많이 사용된 알파벳**의 입력 횟수는 알고 있지만(words_list_max)  
해당 알파벳이 **무엇인지**는 아직 모르고 있다.  
이를 찾아내기 위해  
words_list_max 값을 갖고 있는 원소의 인덱스를 index() 메소드로 구하여 변수 words_list_max_index에 저장했다.  
words_list_max_index에 65를 더하여, chr()로 아스키코드를 문자열로 바꾸면,   
가장 많이 사용된 알파벳이 대문자로 출력된다.  
```python
    words_list_max_index = words_list.index(words_list_max)
    print(chr(words_list_max_index+65))
```
<br>
<br>
* * *
예)  
문제에서 제시된 예제 입력 2은 다음과 같다.  
zZa  
words_list는 다음과 같다.  
\[1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 2\]  
words_list_max는 2이고,  
2를 갖고 있는 원소의 인덱스는   
words_list_max_index, 25이다.  
위 리스트는 알파벳 순서대로 입력 횟수가 저장된 것이므로  
인덱스 25의 원소에는 26번째 알파벳 Z가 입력된 횟수가 저장된다.  
인덱스 25에 65를 더하면 90이고, 이는 알파벳 Z의 아스키 코드와 같다.  
90을 함수 chr()에 대입하면, chr(90), Z가 나온다.  

<br>
<br>
* * *
**가장 많이 사용된 알파벳이 1개가 아니라면(else, 2개 이상)**  
문제 조건에 맞춰 ?를 출력한다.  
```python
else:
    print('?')
```

<br>
<br>
* * *
**코드2**  
```python
# 메모리 31156KB 시간 284ms
words= input().upper()
words_list = [0 for i in range(26)]
for i in words:
    words_list[ord(i)-65] +=1
words_list_max = max(words_list)
if words_list.count(words_list_max) == 1:
    words_list_max_index = words_list.index(words_list_max)
    print(chr(words_list_max_index+65))
else:
    print('?')
```
<br>
<br>
코드 2에서는  
코드 1에 **str.upper() 메소드를 적용**했다.  
<br>
<br>
* * *
upper() 메소드는 문자열의 **모든 알파벳을 대문자로 바꾼 문자열을 반환**한다.  
소괄호에 입력한 문자열이 바뀌는 게 아니라,  
대문자로 바뀐 문자열이 새로 생성된다.  
<br>
<br>
* * *
유사한 메소드로  
lower() 메소드는 문자열의 모든 알파벳을 소문자로 바꾼 문자열을 반환한다.  
upper() 메소드와 마찬가지로, 새로운 문자열이 생성되는 것이다.   
<br>
<br>
* * *
아래에 같이  
```python
words= input().upper()
```
input() 함수에 .(dot)을 찍고 이어서 upper() 메소드를 작성하면,  
input()으로 문자열을 입력받고 이어서 upper() 메소드로 새로운 문자열을 반환하고, 이 새로운 문자열을 words에 대입한다.   
<br>
<br>
* * *
이후 과정은  
코드1과 비교했을 때  
**if문으로 알파벳 대문자와 소문자를 구분하는 과정이 사라졌다.**  
모든 알파벳이 대문자이기 때문이다.  

<br>
<br>
* * *
**코드3(시간 초과)**  
```python
words= input().upper()
words_list = [0 for i in range(26)]
for i in words:
    words_list[ord(i)-65] = words.count(i)
words_list_max = max(words_list)
if words_list.count(words_list_max) == 1:
    words_list_max_index = words_list.index(words_list_max)
    print(chr(words_list_max_index+65))
else:
    print('?')
```
<br>
<br>
코드2에 **알파벳 입력 횟수를 저장할 때 count() 메소드를 적용했다(시간 초과).**  
```python
for i in words:
    words_list[ord(i)-65] = words.count(i)
```
for문으로 입력받은 words의 각 요소에 대해  
리스트의 요소에 알파벳 입력 횟수를 1씩 더하는 것이 아니라,  
count()로 words 중 해당 알파벳의 개수를 대입했는데...  
<br>
**for문의 i 범위 지정이 넓어서(i가 중복되어서) 시간 초과가 발생한 것 같다.**  
<br>
<br>
* * *
예시로  
aaaAAAbb를 입력하면 upper() 메소드를 거쳐  
AAAAAABB로 저장되고,  
for문으로 AAAAAABB의 각 요소에 대해 반복문을 진행하기 때문에,   
첫 번째 요소 A에 대해, words_list\[ord(A)-65]에 words.count(A)를 저장하고    
두 번째 요소 A에 대해, words_list\[ord(A)-65]에 words.count(A)를 저장하고   
세 번째 요소 A에 대해, words_list\[ord(A)-65]에 words.count(A)를 저장하고  
네 번째 요소 A에 대해, words_list\[ord(A)-65]에 words.count(A)를 저장하고  
...
이렇게 중복되는 과정을 거친다.  
<br>
이를 해결하기 위해 다음 코드4에서 set 자료형을 적용했다.  
<br>
<br>
* * *
**코드4(런타임 에러(TypeError))**  
```python
words= input().upper()
words_set = set(words)
print(words_set)
words_fre = []

for i in words_set:
    words_fre.append(words.count(i))

if words_fre.count(max(words_fre)) == 1:
    print(words_set[words_fre.index(max(words_fre))])//여기에서 TypeError 발생
else:
    print('?')
```
<br>
<br>
**for문의 i를 set 자료형에서 가져오면**  
set 자료형은 중복을 허용하지 않기에  
코드3에서 문제 되었던...같은 일을 반복하는 과정을 피할 수 있다!  
<br>
이때,  
**for문의 i는 set 자료형에서 가져오지만  
i의 개수를 구할 때는 기존의 문자열 words에서 가져올 것!**  
i의 개수를 set 자료형에서 가져온다면 1만 리스트에 저장된다.   
```python
for i in words_set:
    words_fre.append(words.count(i))
```
<br>
<br>
* * *
문제는  
**런타임 에러(TypeError)!!!!**    
set 자료형을 적용한 것은 좋은데,  
**set 자료형은 순서가 없으므로 인덱스로 접근할 수 없다**는 것을...간과했다.   
```python
    print(words_set[words_fre.index(max(words_fre))])//여기에서 TypeError 발생
```
<br>
혹시나 다음에도 같은 일을 저지를 수 있으니... 이렇게 시행착오도 기록한다.  
<br>
<br>
* * *
위 문제는 다음 코드5에서 해결했다.  

<br>
<br>
* * *
**코드5**  
```python
# 메모리 31156KB, 시간 120ms
words= input().upper()
words_set_list = list(set(words))
words_fre = []
for i in words_set_list:
    words_fre.append(words.count(i))
if words_fre.count(max(words_fre)) == 1:
    print(words_set_list[words_fre.index(max(words_fre))])
else:
    print('?')
```
<br>
<br>
위의 런타임 에러(TypeError)는  
**set 자료형을 list 자료형으로 바꾸면 해결되는 간단한 문제!**  
```python
words_set_list = list(set(words))
```
<br>
<br>
* * *
set 자료형에 인덱스로 접근했던 부분도  
아래와 같이 수정했다.  
```python
    print(words_set_list[words_fre.index(max(words_fre))])
```
<br>
<br>
* * *
앞의 코드1, 2에 비교했을 때  
코드 시간이 크게 감소했다!!  

<br>
<br>
* * *
**코드6**  
```python
# 메모리 31156KB, 시간 120ms
words= input().upper()
words_set_list = list(set(words))
words_fre = dict()
for i in words_set_list:
    words_fre[i] = words.count(i)
max_words_value = max(words_fre.values())
max_words = [key for key, value in words_fre.items() if value == max_words_value]
if len(max_words) == 1:
    print(max_words[0])
else:
    print('?')
```
<br>
<br>
코드5에서,  
**알파벳의 입력 빈도를 저장할 때 dictioinary 자료형으로 저장**하고 싶어서 작성했다.  
<br>
<br>
* * *
**dict() 함수로 빈 딕셔너리를 선언**한다.  
```python
words_fre = dict()
```
<br>
<br>
* * *
**알파벳의 입력 횟수를 딕셔너리에 저장하자.**   
for문으로 words_set_list에서 i를 가져와서,  
i를 딕셔너리 words_fre의 key로, words.count(i)를 딕셔너리 words_fre의 value 값으로 추가한다.  
```python
for i in words_set_list:
    words_fre[i] = words.count(i)
```
<br>
<br>
* * *
딕셔너리 words_fre의 **value 중 최댓값**을 구하기 위해,  
values() 메소드로 딕셔너리의 value 값에 접근하고  
max() 함수로 value 값 중 최대값을 구해,  
변수 max_words_value에 대입했다.  
```python
max_words_value = max(words_fre.values())
```
<br>
<br>
* * *
**최대 value는 알았지만, 그의 key값은 아직 모른다.  
key 값을 찾아내기 위해**    
리스트 컴프리헨션을 적용한 다음 코드를 사용했다.  
```python
max_words = [key for key, value in words_fre.items() if value == max_words_value]
```
참고 : 리스트 컴프리헨션으로 최대 value에 대한 key 찾는 법 알려준 링크 [[Python] dictionary max value에 대한 key 찾기](https://bio-info.tistory.com/40)  
<br>
items() 메소드로 딕셔너리 words_fre의 key, value 쌍에 접근한 다음,  
if로 value가 max_words_value와 동일한 사례에 대해,  
key 값을 가져와서 리스트 형태로 저장한다.  
<br>
<br>
* * *
이 리스트의 길이가 1과 같으면 리스트\[0] 출력(= 가장 많이 사용된 알파벳이 1개로 유일),  
이 리스트의 길이가 1과 같지 않다면 ? 출력한다.  
```python
if len(max_words) == 1:
    print(max_words[0])
else:
    print('?')
```
<br>
<br>
* * *
최대 value에 대한 key를 출력하는 방법에는  
아래 링크에서 알려준 것처럼 다양한 방법이 있지만,  
<br>
참고 : 매우 다양한 방법을 알려준 링크 [[python] 사전에서 최대 값을 가진 키를 얻습니까?](http://daplus.net/python-%EC%82%AC%EC%A0%84%EC%97%90%EC%84%9C-%EC%B5%9C%EB%8C%80-%EA%B0%92%EC%9D%84-%EA%B0%80%EC%A7%84-%ED%82%A4%EB%A5%BC-%EC%96%BB%EC%8A%B5%EB%8B%88%EA%B9%8C/)  
<br>
다른 방법들은 value가 최대인 key가 1개만 존재할 때 유용하고,  
이 문제처럼 value가 최대인 key가 여러 개 존재할 수 있을 때는 리스트 컴프리헨션이 사용하기 적절했다.  
<br> 
<br>
참고 : 리스트 컴프리헨션에 대한 내용을 알려준 일크  
[22.5 리스트 표현식 사용하기](https://dojang.io/mod/page/view.php?id=2285)  
[2.6 리스트 컴프리헨션](https://wikidocs.net/84393)  
[1) 리스트 컴프리헨션](https://wikidocs.net/22805)  


<br> 
<br> 
### 예제 6단계, 1152번, "문자열 반복", 구현, 문자열
[백준 1152번 문제](https://www.acmicpc.net/problem/1152)  
**해결책**  
```python
words_list = input().split()
print(len(words_list))
```
<br>
<br>
입력받은 문자열에서, 띄어쓰기를 기준으로 단어의 개수를 출력해야 한다.  
이 경우, 파이썬의 split() 메소드를 사용하면 간단하게 해결할 수 있다.  
split() 메소드는 소괄호 안에 입력된 문자를 기준으로 문자열을 나눠준다.  
소괄호 안에 입력된 것이 없으면, 공백을 기준으로 문자열을 나눈다.  
```python
words_list = input().split()
```
input().split()으로 input()과 split()을 .으로 이어서 입력하면,  
왼쪽부터 함수 또는 메소드를 사용하여,  
문자열을 입력받고, 입력받은 문자열을 공백을 기준으로 나누고 리스트 형태로 저장한다.  
<br>
<br>
* * *
만약 파이썬이 아니라 다른 언어로 사용하는데 split() 메소드와 같은 함수가 없을 경우,  
띄어쓰기를 인식할 때마다 단어의 개수에 +1을 더해야 한다.  
그리고 문자열의 앞과 뒤에 공백이 포함될 수 있으므로,  
앞과 뒤에 공백이 인식되면 단어의 개수에 -1을 빼야 한다.  
<br> 
<br> 
### 예제 7단계, 2908번, "상수", 구현
[백준 2908번 문제](https://www.acmicpc.net/problem/2908)  
**해결책1**  
```python
# 메모리 29200KB 시간 72ms 
def rev(x):
    rev_x = x[::-1]
    return int(rev_x)

A, B = input().split()
print(max(rev(A), rev(B)))
```
<br>
<br>
숫자(문자열)를 거꾸로 반환하는 함수 rev(x)를 정의한다.  
<br>
해결책1에서는 slicing(또는 slice) 방법을 사용했다.  
<br>
<br>
* * *
slicing은 시퀀스 자료형(연속적인 객체)의 일부를 잘라내어, 새로운 객체를 생성한다.  
\[start:stop\[:step]] 형식으로 작성하고,  
시퀀스 자료형의 '인덱스 start'부터 '인덱스 stop-1'까지의 데이터를 잘라온다.  
이때, step은 가져오는 인덱스의 증가폭을 의미한다.   
step을 생략하면 인덱스가 1씩 증가하며 데이터를 가져오고,  
step에 -1을 작성하면 역순으로(인덱스가 1씩 감소하며) 데이터를 가져온다.   
<br>
<br>
* * *
해결책1에서 사용한 x\[::-1]은  
start와 stop에 작성한 것이 없어, 처음부터 끝까지 모든 데이터를 가져온다.  
step에 -1을 작성하여 역순으로 데이터를 가져온다.  
```python
    rev_x = x[::-1]
```
<br>
<br>
* * *
문제에서 입력받은 값 2개는 숫자이고, 이후 대소 비교를 해야하므로 int형으로 변환하여 반환한다.  
```python
    return int(rev_x)
```
<br>
<br>
* * *
함수 rev(x) 정의가 끝났다.  
<br>
숫자 2개를 입력받아서 A와 B에 띄어쓰기를 기준으로 나눠서 저장한다.  
숫자를 입력받지만 문자열 자료형으로 둔다.  
이후 과정에서 rev(x) 함수로 숫자를 거꾸로 바꿔야 하는데  
rev(x) 함수에서 사용한 slicing은 시퀀스 자료형에 사용되므로,   
숫자를 시퀀스 자료형인 문자열로 두는 것이다.  
```python
A, B = input().split()
```
<br>
<br>
* * *
A와 B를 각각 rev(x) 함수에 대입하여 int형, 거꾸로 바뀐 숫자로 바꾸고, 이를 max() 함수로 최대값을 찾아 print로 출력한다.  
```python
print(max(rev(A), rev(B)))
```
<br>
<br>
문제 조건을 충족했다.  
<br>
<br>
* * *
**해결책2**  
```python
# 메모리 29200KB 시간 72ms 
def rev(x):
    rev_x = ''.join(reversed(x))
    return int(rev_x)

A, B = input().split()
print(max(rev(A), rev(B)))
```
<br>
<br>
해결책2는 rev(x) 정의 과정에서 slicing이 아니라 reversed() 함수를 사용했다.  
reversed() 함수는 바뀐 데이터를 반환하지 않으므로,  
''.join()과 함께 사용해야 한다.  
<br>
<br>
* * *
**해결책3**  
```python
# 메모리 29200KB 시간 72ms 
def rev(x):
    rev_x = ''
    for i in x:
        rev_x = i + rev_x
    return int(rev_x)

A, B = input().split()
print(max(rev(A), rev(B)))
```
<br>
<br>
해결책3에서는 rev(x)를 정의할 때 for문을 사용했다.  
x의 각 요소를 for문의 i로 가져오고,  
이를 새로운 문자열 rev_x의 앞 부분에 더한다.  
```python
    rev_x = ''
    for i in x:
        rev_x = i + rev_x
```
<br> 
<br> 
### 예제 8단계, 5622번, "다이얼", 구현
[백준 5622번 문제](https://www.acmicpc.net/problem/5622)  
**해결책1**  
```python
# 메모리 29200KB 시간 72ms 코드 길이 373B
words = input()
sec = 0

for i in words:
    if i in 'ABC':
        sec += 3
    elif i in 'DEF':
        sec += 4
    elif i in 'GHI':
        sec += 5
    elif i in 'JKL':
        sec += 6
    elif i in 'MNO':
        sec += 7
    elif i in 'PQRS':
        sec += 8
    elif i in 'TUV':
        sec += 9        
    elif i in 'WXYZ':
        sec += 10

print(sec)
```
<br>
<br>
알파벳 대문자로 이루어진 단어를 입력받아 words에 저장한다.  
변수 sec에 0을 저장한다.   
```python
words = input()
sec = 0
```
<br>
<br>
* * *
words의 각 요소를 for문의 i로 가져오고  
if-elif문으로 i가 특정 문자열에 존재한다면, 각 문자열에 해당하는 시간을 sec에 더한다.  
```python
for i in words:
    if i in 'ABC':
        sec += 3
    elif i in 'DEF':
        sec += 4
    elif i in 'GHI':
        sec += 5
    elif i in 'JKL':
        sec += 6
    elif i in 'MNO':
        sec += 7
    elif i in 'PQRS':
        sec += 8
    elif i in 'TUV':
        sec += 9        
    elif i in 'WXYZ':
        sec += 10
```
<br>
<br>
* * *
for문이 끝나고, sec를 출력한다.  
```python
print(sec)
```
<br>
문제 조건을 충족했다.  
<br>
<br>
* * *
**해결책2**  
```python
# 메모리 29200KB 시간 72ms 코드 길이 194B
words = input()
sec = 0
ABC = ['ABC', 'DEF', 'GHI', 'JKL','MNO', 'PQRS', 'TUV', 'WXYZ']

for i in words:
    for j in range(8):
        if i in ABC[j]:
            sec += 3+j
        
print(sec)
```
<br>
<br>
알파벳 대문자로 이루어진 단어를 입력받아 words에 저장한다.  
변수 sec에 0을 저장한다.   
```python
words = input()
sec = 0
```
<br>
<br>
* * *
리스트 ABC에 문자열 자료를 저장한다.  
해결책1에서 if-elif문의 사례를 나누는 기준이 되었던 문자열을 리스트 ABC에 저장했다.  
```python
ABC = ['ABC', 'DEF', 'GHI', 'JKL','MNO', 'PQRS', 'TUV', 'WXYZ']
```
<br>
<br>
* * *
words의 각 요소를 for문의 i로 가져오고  
각 i에 대해 다른 for문을 8번 진행한다.  
i가 리스트 ABC\[i]에 존재하면 sec에 3+j를 더한다.  
```python
for i in words:
    for j in range(8):
        if i in ABC[j]:
            sec += 3+j
```
<br>
<br>
* * *
마지막으로 sec를 출력한다.  
```python
print(sec)
```
<br>
문제 조건을 충족했다.  
<br> 
<br> 
### 예제 9단계, 2941번, "크로아티아 알파벳", 구현, 문자열
[백준 2941번 문제](https://www.acmicpc.net/problem/2941)  
**시행착오**  
```python
# 특수 조합의 개수를 측정하고 삭제했더니, 문제 발생
# 예제 nljj에서 lj를 없애면 nj가 남는데, nj가 새로운 크로아티아 알파벳으로 인식된다.
words = input()
count = 0

count += words.count('c=')
words = words.replace('c=','')

count += words.count('c-')
words = words.replace('c-','')

count += words.count('dz=')
words = words.replace('dz=','')

count += words.count('d-')
words = words.replace('d-','')

count += words.count('lj')
words = words.replace('lj','')

count += words.count('nj')
words = words.replace('nj','')

count += words.count('s=')
words = words.replace('s=','')

count += words.count('z=')
words = words.replace('z=','')

count += len(words)

print(count)
```
<br>
<br>
(c=, c-, dz=, d-, lj, nj, s=, z=)  
2~3개의 알파벳 또는 기호로 이루어진 특수 조합을 크로아티아 한 글자로 인식해야 한다.  
위 특수 조합에 해당하지 않는 알파벳은 한 글자로 인식해야 한다.  
<br>
<br>
* * *
처음에 작성한 코드는   
특수 조합이 문자열 안에 몇 개 있는지 계산하고, 해당 특수 조합을 문자열에서 삭제하는 방법을 사용했다.  
```python
count += words.count('c=')
words = words.replace('c=','')
```
str.count('문자열', start, end) 메소드는 str 문자열 안에서 '문자열'이 포함된 개수를 반환한다. start와 end에 메소드 실행 범위를 인덱스로 지정할 수 있고, 범위 지정을 생략할 수 있다. 범위 지정 시 end는 범위에 포함되지 않는다.  
<br>
str.replace(old, new\[, count]) 메소드는 str 문자열 안에서 old(문자열)를 new(문자열)로 바꾼 후 새로운 문자열을 반환한다.  
count는 왼쪽부터, 바꿀 횟수를 지정할 때 입력한다.  
new에 ''만을 입력하면 replace() 메소드는 문자열1을 삭제하는 역할을 수행한다.  
<br>
삭제하는 방식을 선택한 이유는  
dz=의 개수를 계산하고 그대로 두면, 이후 z=의 개수를 계산할 때 중복으로 인식될 것을 방지하기 위함이다.  
또한 모든 특수 조합을 삭제하면 마지막에 남은 알파벳을 한 글자씩 개수를 측정하기 위해서였다.  
<br>
<br>
* * *
그런데 삭제 방법을 사용했더니 문제가 발생했다.  
특수 조합을 삭제한 이후, 해당 특수 조합의 앞뒤 문자가 붙여져서 새로운 특수 조합이 만들어졌다.  
<br>
문제에서 제시된 예제 입력3 nljj에서 특수 조합은 lj만 존재하므로 정상적으로는 문자 3개로 인식해야 한다.  
<br>
그런데 위 코드를 적용하면  
특수 조합 lj가 인식되어 count가 1 증가하고, lj가 삭제되어 nj가 남는다.  
특수 조합 nj가 인식되어 count가 1 증가하고, nj가 삭제되어 남은 문자열이 없다.  
결과적으로 nljj를 문자 2개로 인식한다.  
<br>
<br>
* * *
위 문제를 해결하기 위해서는  
특수 조합을 삭제하는 것이 아니라, 다른 기호로 대체하는 방법을 사용해야 한다.  
<br>
<br>
* * *
**해결책**  
```python
croatia = ['c=', 'c-', 'dz=', 'd-', 'lj', 'nj', 's=', 'z=']
words = input()

for i in croatia:
    words = words.replace(i,'*')

print(len(words))
```
<br>
<br>
'시행착오' 코드를 수정해야 하는데 길이가 길고 반복되는 부분이 많아서 for문으로 변경했다.  
<br>
특수 조합을 리스트 croatia에 저장했다.  
이때, 'dz='가 'z='보다 앞쪽에 위치해야 'dz='를 다른 문자로 변경하고 'z='를 검사한다.  
문자열을 입력받아 words에 저장했다.  
```python
croatia = ['c=', 'c-', 'dz=', 'd-', 'lj', 'nj', 's=', 'z=']
words = input()
```
<br>
<br>
* * *
croatia의 각 요소를 for문의 i로 가져와서,   
words에 i가 있으면 기호 \*로 변경한다.  
즉, 각 특수 조합을 문자 1개(\* 1개)로 변경한다.  
<br> 
이로써 'dz='와 'z='를 중복 카운트하는 문제를 해결했고  
전체 문자 개수를 계산할 때 문자열 길이를 계산하면 된다.  
특수 조합을 삭제하는 방법이 아니라서 '시행착오' 코드에서 새롭게 발생한 문제가 생기지 않는다.  
```python
for i in croatia:
    words = words.replace(i,'*')
```
replace() 메소드에 대한 설명은 '시행착오' 코드 설명에 작성했다.  
<br>
<br>
* * *
for문이 끝나고  
words의 길이를 출력하면 풀이가 끝난다.  
```python
print(len(words))
```
<br> 
<br> 
### 예제 10단계, 1316번, "그룹 단어 체커", 구현, 문자열
[백준 1316번 문제](https://www.acmicpc.net/problem/1316)  
**해결책**  
```python
N = int(input())
count = N

for i in range(N):
    abc = []
    words=input()
    for j in range(len(words)):
        if words[j] not in abc:
            abc.append(words[j])
        else:
            if words[j-1]==words[j]:
                continue
            else:
                count -=1
                break

print(count)
```
<br>
<br>
단어 안에 모든 문자에 대해, 각 문자가 연속해서 나타나야 그룹 문자이다.  
앞에 등장한 문자가 이웃하여 등장하는 것은 괜찮지만, 다른 문자가 등장한 이후 동떨어져서 등장하면 그룹 문자가 아니다.  
리스트 abc를 빈 리스트로 초기화한다.  
새로운 문자가 사용되면 리스트 abc에 저장하고,  
새로운 문자가 아니라면(리스트 abc에 이미 있는 문자라면)  
직전의 문자와 동일한지 검사하여,  
동일하다면 넘어가고 동일하지 않다면 그룹 문자가 아니라고 판명하겠다.  
<br>
<br>
* * *
단어의 개수를 입력받아 N에 저장한다.  
그룹 단어의 개수 count를 N으로 초기화한다.  
검사하는 단어가 그룹 단어가 아닐 때마다 count에 1을 뺄 것이다.  
```python
N = int(input())
count = N
```
<br>
<br>
* * *
단어 N개를 검사해야 하므로  
for문을 N번 시행한다.  
리스트 abc를 빈 리스트로 초기화한다.  
리스트 abc를 초기화하지 않는다면, 다음 단어를 검사할 때 abc에 이미 자료가 들어있어 영향을 준다.  
단어를 입력받아 words에 저장한다.  
```python
for i in range(N):
    abc = []
    words=input()
```
<br>
<br>
* * *
words의 길이만큼 for문을 시행한다.  
words\[j]가 리스트 abc에 없다면(if, 새로운 문자 사용)  
리스트 abc에 저장하고 다음으로 넘어간다(j 1추가)  
<br>
words\[j]가 리스트 abc에 있다면(else, 이미 사용했던 문자)  
바로 직전 문자 words\[j-1]와 words\[j]가 동일한지 확인한다(if문).  
동일하다면(if, 연속된 문자 사용 중), 그룹 문자에 해당하므로 다음 j로 넘어간다.  
동일하지 않다면(else, 이전에 사용한 문자가 동떨어져서 사용됨) 그룹 문자가 아니므로  
for문을 break로 끝내고 count에 1을 뺀다.  
<br>
단어가 그룹 단어에 해당하면 count 변화 없이, 다음 단어로 넘어간다.   
```python
    for j in range(len(words)):
        if words[j] not in abc:
            abc.append(words[j])
        else:
            if words[j-1]==words[j]:
                continue
            else:
                count -=1
                break
```
<br>
<br>
* * *
모든 단어에 대해 그룹 단어 검사를 끝내면  
그룹 단어 개수 count를 출력한다.  
<br>
<br>
문제 조건을 충족했다.  
<br> 
<br> 
