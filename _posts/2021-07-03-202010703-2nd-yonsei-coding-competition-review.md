---
title:  "20210703 2021 연세대학교 미래캠퍼스 제2회 슬기로운 코딩생활 참가 후기"
excerpt: "대회 진행 방식, 푼 문제, 대회 결과, 배운 점과 느낀 점, 앞으로 공부할 방향"

categories:
  - Competition
tags:
  - Competition
  - Algorithm
---

2021년 7월 3일 오전 10시부터 낮 12시까지, 2시간 동안 "2021 연세대학교 미래캠퍼스 제2회 슬기로운 코딩생활"에 참가했다.  

처음으로 코딩대회에 참가하는 거라, 대회 진행 방식도 궁금하고 문제 스타일도 너무너무 궁금했다!  
대회 전날, 메일로 대회 진행방식이 공지되었다.  



## 대회 진행 방식
백준 사이트(<https://www.acmicpc.net>)에서 온라인 진행!  
모든 문제는 언어 제한이 없고, 시간과 메모리는 모든 언어가 동일!  
(중요!) 메일로 전송한, 개인별 대회 계정으로 참가할 것!  
대회 링크는 <https://www.acmicpc.net/contest/view/661>  
스코어보드는 대회 시작 후 60분 동안만 공개된다. 이후로는 본인 점수만 확인 가능.  
등수 집계는 맞춘 문제 수 기준, 동점자는 페널티 적은 순으로 등수 매김.  
외부 에디터 사용 가능, 인터넷 검색 가능, 다른 사람과의 연락은 불가능.  
Zoom으로 접속해서 손과 모니터가 보이게 카메라 세팅 필수.  
대회 결과 발표는 대회 끝나고 30분 뒤, 낮 12시 30분에 있으니, 시상까지 Zoom 나가지 말 것!



## 대회 준비 과정
준비한 언어는 파이썬.  
외부 에디터는 Visual Studio Code.  
백준 사이트에 가입해서 가장 쉬운 문제 2개 풀어봄.  
코딩 대회는 처음 참가하지만, 1문제는 풀 수 있지 않을까?!  
문제 1개 맞추면 참가상을 준다고 했으니, 목표는 참가상이다!  



## 대회 참가!
대회 문제는 총 4개로, 생각보다 문제 수가 적었다.  
1개 맞추면 참가상 준다고 하길래, 한 8~9개 될까 예상했다.  

그리고 문제가 생각보다 길어서...잠시 놀랐다.  
문제 상황 설명이 800~1000자는 될까?  
꼼꼼하게 읽지 않으면 문제 조건 놓치기 쉬운 상황!  
실제로 본문의 문제 조건 하나를 놓쳐서, 예시 문제&답 틀린 것이 아니냐, 질문하는 학생이 있었다.  



### 문제
A.창영이와 버스  
B.창영이와 점프  
C.창영이와 커피  
D.창영이와 퇴근  

나는 A를 파이썬으로 풀어서 맞췄고, B를 풀다가 시간이 다 됐다.  
문제 내용은 며칠 뒤에 백준 사이트에서 공개되니, 공개되면 링크를 추가하겠다.  



### 내가 푼 A 풀이
```python
N, M = input().split()
N = int(N)
M = int(M)
BUS = [0 for _ in range(M)]
BUS = list(map(int, input().split()))
ASE = [0 for _ in range(N)]
for i in range(N):
    ASE[i]=list(map(int, input().split()))
COST = int(0)
for j in range(M-1):
    COST = COST + ASE[BUS[j]-1][BUS[j+1]-1]

print(COST)
```
A문제는 맞았다.  
2차원 리스트에 버스 환승 요금 입력해주고,  
창영이가 버스 사용한 순서대로 버스 환승 요금 더하면 되는 문제.  
i, j 값,,행렬 요소에 접근할 때 +1, -1 쓰는 게 헷갈려서 생각보다 시간이 오래 걸렸다. 1시간 소요.  
문제 중간에 print 함수로 값 확인해주니까 풀기 쉬워졌다.  
!!!!!!다음에도 문제 풀 때, 행렬 문제는 print 함수로 값 확인해주자!!!!!  



### B문제는 도전 중 시간 끝. 아직 미완이다.
```python
N, K = input().split()
N = int(N)
K = int(K)
L = [0 for _ in range(N)]
L = list(map(int, input().split()))
Superjump = 1
Block = int(1)
ReBlock = int(1)
MaxBlock = int(1)

print(L)

for k in range(0, N-2, 1) :
    for i in range(k, N-1, 1) :
        if L[i] <= K:
            Block = Block + 1
        else:
            if Superjump==1 :
                Block = Block + 1
                Superjump = 0
                print("슈퍼점프 사용")
                continue
            else:
                break
    if MaxBlock<=Block:
        MaxBlock = Block
    else:

print(Block)

for j in reversed(range(N-1)) :
        print("j", j)
        print(ReBlock)
        if L[j] <= K:
            ReBlock = ReBlock + 1
        else:
            if Superjump==1 :
                ReBlock = ReBlock + 1
                Superjump = 0
                print("슈퍼점프 사용")
                continue
            else:
                break

```

이 문제는 문제 상황도 복잡해서, 그림판에 그림 그려가면서 이해했다.  

창영이가 빨간 보도블록만 밟아서 점프하는데, 최대 몇 개의 보도블록을 밟을 수 있는가?  

이때 보도블록 사이 거리 각각 다르고(입력 받는 값),  
창영이 보폭도 정해져 있고(입력 받는 값),  
슈퍼점프라고, 블록 사이 거리가 보폭보다 넓어도 1번은 무조건 점프할 수 있고,  
꼭 왼쪽 처음부터 순서대로 보도블록 밟는 게 아니라 중간부터 시작할 수 있고,  
왼쪽이 아니라 오른쪽부터 보도블록 밟을 수 있고...  

왼쪽 처음부터 보도블록 밟아서 보도블록 최대로 밟은 개수 구하는 식은 만들었고,  
오른쪽 처음부터 보도블록 밟는 것도 만들었는데,  
중간부터 시작하는 걸 만드는 도중에 대회가 끝났다.   
하나하나 고려하는 게 아니라, 한 번에 고려할 수 있는 방법이 있었을까?  

위 코드 중간에 print 함수가 보이는데,   
풀이 과정에서 내가 쓰고 있는 코드가 내가 원하던 방향으로 실행되고 있나 확인하려고 넣어둔 것이다.  
지금은 지웠지만 i값이랑 Block값도 print로 확인했었다.  

문제가 백준 사이트에 공개되면 다시 도전하기!!



## 대회 결과
전공자, 비전공자 구분하여 시상하고, 총상금 500만 원!  
1등 1명(50만 원)  
2등 3명(30만 원)  
3등 11명(10만 원)  
\+ 일정 점수 달성 시 소정의 상품(참가상)  

1문제를 맞췄으니 참가상일 거라 예상했는데,  
비전공자 부문 3등 상을 수상했다(4명 공동 수상)!  

놀라운 건 비전공자 1등이 유일한 4문제 만점자였다!   
이분이 학교 에브리타임으로 대회 후기&코드 풀이, 블로그 포스팅, 유튜브 게시도 하셨다.  
C언어였나, C++이었나, 파이썬과는 달랐다.  
나도 이분처럼 문제 다 맞히고 싶다!!  
 


## 배운 점과 느낀 점
대회 참가하기 전에는  
파이썬 언어 공부와 알고리즘 문제 풀이를 따로 생각했었다.  

파이썬 언어 배우는 건 기본 함수들을 설명하는 기초 책이나 강의로 배우고,   
백준이나 코딩 테스트 문제들은 나한테는 아주 어려울 테니까, 나\~~중에(언제?ㅎㅎㅎ) 풀어봐야겠다고,,  

대기업 채용할 때 코딩 테스트를 보는데,  
엄청 어렵고 경쟁 치열하다더라!! 하는 이야기를 많이 들어서 그랬나, 알고리즘 문제를 좀 거리감 있게 느꼈다.


하지만 이번에 대회 준비하고, 참가하면서 느꼈던 건  



### 1. 알고리즘 문제는 쉬운 것부터 어려운 것까지 단계별로 많다.
어려운 코딩 테스트 이야기만 듣고 겁먹지 말자!  
쉬운 문제도 많다!  

특히, 백준 "단계별로 풀어보기"!  
단계가 1부터 50까지 세세하게 나누어져 있고, 각 단계를 누르면 또 예제가 단계별로 4~11문제 나와서 차근차근 학습할 수 있다.



### 2. 알고리즘 사고가 중요하다.
문제를 읽으면서 생각나는 대로 코드를 썼다가...  
조건 놓쳐서 계속해서 코드를 수정하고...  
코드도 복잡해지고 생각도 복잡해지고...  
시간 낭비가 많았다.

내가 생각한 문제 풀이 흐름은, 코드로 구현한 풀이 흐름과는 달랐다.   
평소 사고와는 달리, 알고리즘에 맞춰서 생각을 해야 한다.



### 3. 알고리즘 풀이와 언어 공부는 밀접한 연관, 같이 배워야 한다.
파이썬을 왜 공부하는가?  
언어 자체를 연구하려고?  
그건 소수의 사람이다.  
결국 원하는 문제 풀이, 원하는 프로그램을 구현하려고 배우는 것이다.  

파이썬 언어만 열심히 공부하고, 알고리즘 풀이를 뒤로 미루는 것은,  
비유하자면,  
영어 단어만 열심히 외우고, 문장 읽는 쓰는 것은 뒤로 미루는 것과 비슷하지 않을까?  

영어 단어도 외우면서 문단 읽고 쓰는 걸 공부하는 것처럼,  
파이썬 언어, 알고리즘 풀이 다 같이 공부하는 것이 적절한 학습법이라고 생각한다.


사실, 파이썬은 오늘이 처음이었다.  
"파이썬 입력받기"  
"파이썬 입력값 여러 개"  
"파이썬 2차원 리스트 입력"  
"파이썬 for문"  
"파이썬 for문 끝내기"  
...  
이런 검색어로 찾아가면서 문제를 풀었다. 아주 무모했지!

그런데, 이렇게 알고리즘 문제 풀면서 공부하니까  
해당 함수가 어떻게 쓰이는지 더 빠르게, 잘 이해할 수 있었다.  
그래서 알고리즘 문제를 풀면서 언어 공부하는 것이 더 효과적이라고 느꼈다.  

물론, 처음 코딩 배울 때는, 전체적으로 어떤 함수가 있는지 살펴보는 과정이 필요하다!  
하지만 한 번 정도 훑어본 사람이라면, 알고리즘 공부와 함께 언어 공부하는 것을 추천한다.  



### 4. 서로 다른 언어로 공부하는 사람들이 알고리즘 스터디를 꾸리는 게 가능할까?  
이건 비전공자 1등 학생의 풀이를 보면서 느꼈던 점인데,  
작성한 언어가 c언어인가? 생긴 게 파이썬이랑 많이 다르다!!!!!  

앞으로 GDSC Yonsei를 운영할 계획을 짜면서, 알고리즘 스터디도 진행할까 고려했는데,,,  
다른 언어로 공부하는 학생들이 같이 알고리즘 공부를 하는 게 가능할까...?의구심을 품게 되었다.  

알고리즘 문제 난이도가 많이 높아지면 접근 방법도 어려우니까, 그걸 공부하는 방식으로 가면 괜찮을까?  

그렇게 되면, 아직 초보자인 학생들은 해당하지 않는걸?  

초보자는 같은 언어끼리 스터디를 묶고,  
숙련자는 하나로 묶어서 스터디를 해야 하나?  

이건 좀 더 생각해 볼 문제인 것 같다.



## 앞으로의 공부 방향
위에서 말한 것처럼,  
알고리즘 공부하면서 파이썬 공부한다!  

백준 "단계별로 풀어보기"를 적극 활용할 것이다.  
여기 깃허브 블로그에도 풀이 코드& 추가 설명을 올리고,  
깃허브에도 풀이 코드를 올릴 계획이다.  

알고리즘 스터디 구성은, 좀 더 생각해야겠다.   
내가 좀 더 어려운 알고리즘을 공부해보면 어떻게 스터디 진행을 해야 할 지 알 수 있을 것 같다.