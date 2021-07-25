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
6단계 작성 기간 : 2021년 7월 25일 ~ 2021년 7월 
<br>
<br>
# 6단계, 함수
[백준 단계별로 풀어보기 6단계](https://www.acmicpc.net/step/6)  
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
