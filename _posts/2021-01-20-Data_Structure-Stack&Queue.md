---
title: "자료구조 - Stack & Queue"
date: 2021-01-20 22:38:05 -0400
update: 2021-01-21 22:06:01 -0400
categories: JavaScript codestates Data_Structure 
---
(자료구조 스프린트 문제 푸느라 번 아웃이 되버렸다...)   

![datastructure](https://user-images.githubusercontent.com/70124288/105183301-5dea4b80-5b71-11eb-8970-0a884c076f2f.jpg)

자료구조... 정말로 내가 사람인 것인지 사람의 행세를 하는 컴퓨터인 것인지 고민을 하게 되는... 개인적으로 굉장히 어려운 개념인 것 같다. 자바스크립트를 공부하고 HA를 풀었을 때도 이정도로 머리가 터지고 진짜 체력이 방전되지도 않았고, immersive course를 진행하면서 처음으로 기절도 해봤다...(잠깐 머리 식힌다고 오후 8시쯤에 눕자마자 딥슬립...일어나도 피곤한 이 저질 몸...) 자료구조를 배우면서 솔직히 머릿속으로는 수백번도 더 물리를 만든 뉴턴을 욕했던 것 처럼 자료구조를 만든 사람을 욕했다...  
    
(자료구조를 배우는 나의 모습)
![고통받는 짤](https://user-images.githubusercontent.com/70124288/105184568-d4d41400-5b72-11eb-851f-fd711ea2a5ed.png)
   
(고통받는 나의 모습을 보는 선배들의 모습)
![톰크루즈 웃짤](https://user-images.githubusercontent.com/70124288/105184724-04831c00-5b73-11eb-95b3-3460931b0236.png)   
(야 너두? 야 나두!)
   
어쨋든 자료구조는 우리가 앞으로 코딩을 하게 되면서 반드시 알아둬야 필수 개념임과 동시에 효율적인 프로그램을 만들기 위해서 많이 사용되므로 어떤 원리로 작동하는지에 대한 이해도 필요하다. 우선적으로 기본 개념들에 대해서 먼저 설명을 하려고 한다.   

**[기본 개념]**    
 1) 자료란?   
문자, 소리, 숫자, 그림, 영상, 단어 등의 형태로 된 의미 단위를 말한다. 이러한 자료들을 의미있게 정리하면 정보가 된다.   
자료들을 컴퓨터에서 다루기 위해서는 인간의 언어를 컴퓨터의 언어로 번역해주는 컴파일러를 사용해야 한다.   

 2) 데이터 타입   
데이터 타입은 하나의 데이터를 어떻게 해설할 것인지를 정의한 것이다.   
(a) 컴퓨터에 0과 1로 저장되어 있는 데이터를 인간이 사용하는 여러가지 데이터들의 종류로 해석하기 위한 장치.   
(b) 같은 이진 데이터라도 인간이 해석하는 방식에 따라서 다른 데이터가 될 수 있다. (ex. 아스키 코드)   
(c) 원시 타입 : 정수, 실수, 문자, 논리   
(d) 사용자 정의 타입 : 구조체, 클래스, ...
   
 3) 자료구조란?   
여러 데이터들의 묶음을 어떻게 저장하고 사용할지, 또는 어떻게 유용하게 활용할 수 있는지를 정의한 것이다. (ex.배열, 스택, 트리, 해시, ...)   
자료구조는 특성한 상황에 문제를 해결하는데 특화되어 있다.   

기본개념들에 대해서 알아봤으니 이젠 자료구조가 어떤 상황에 쓰이고 어떠한 것들이 있는지 알아보도록 하자.
   
**1.Stack**   
스택이란 한 쪽 끝에서만 자료를 넣고 뺄 수 있는 LIFO(Last In First Out) 형식의 자료 구조이다.   
<img width="407" alt="stack" src="https://user-images.githubusercontent.com/70124288/105186544-2d0c1580-5b75-11eb-9e85-d75238247c1b.png">   
좀더 이해하기 쉬운 예시를 들자면 바로 '내'가 좋아하는 프링글스가 있다.   
![프링글스](https://user-images.githubusercontent.com/70124288/105187090-bb809700-5b75-11eb-9e0b-76c7ae75817c.jpeg)   
프링글스를 보면 과자가 통에 층으로 쌓여있다. 만약 우리가 프링글스를 먹고 싶다고하면 어떻게 해야할까? 프링글스의 뚜껑을 열고 봉인을 풀고 가장 위에 있는 것 부터 차례대로 꺼내서 먹기 시작하면 된다. 이때, 가장 위에 담겨져 있는 프링글스는 포장전 가장 마지막으로 넣은 조각일 것이다.  
    
스택도 마찬가지다. 가장 마지막으로 담긴 데이터가 가장 먼저 빠져나가는 형식이다. 그렇기 때문에 만약 우리가 원하는 데이터를 얻고 싶으면, 그 데이터들 위에 있는 다른 데이터들을 다 꺼내고 나서야 얻을 수 있게 된다.   
그렇다면 도대체 왜 스택을 사용하는가? 그것은 바로 스택에서 데이터를 추가하거나 삭제하는 연산이 가능하기 때문이다.   
   
대표적인 예시로 재귀 알고리즘이 있다. 재귀함수는 함수에서 자신의 함수를 호출하는 함수인데, 이 재귀함수를 호출하는 경우에 임시 데이터를 스택에 넣어준다. 재귀함수가 돌고 난 이후 빠져나올 때는 스택에 넣어 두었던 임시 데이터들을 다 빼 줘야 하는데, 스택을 이용하면 이 일련의 과정들이 쉽게 이루어진다.   
   
스택에는 4가지 연산 메소드가 있는데 이해하는데 크게 어렵지 않기 때문에 간단히 적도록 한다.   
* pop() : 스택에서 가장 위에 있는 항목을 제거.   
* push(data) : 스택의 가장 윗 부분에 data를 추가.   
* peek() : 스택의 가장 위에 있는 data를 리턴.   
* isEmpty() : 스택이 비어있는지를 확인. 비어있으면 true를 리턴.   
   
   
**2.Queue**   
큐는 컴퓨터의 기본적인 자료 구조의 한 가지로, 먼저 집어넣은 데이터가 먼저 나오는 FIFO(Fist In First Out) 구조로 저장하는 형식이다.   
![queue](https://user-images.githubusercontent.com/70124288/105189146-01d6f580-5b78-11eb-8617-a7ee8109d9d9.png)   
쉬운 예시로 대기열을 생각하면된다. 우리가 놀이공원에 가서 원하는 놀이기구를 타기 위해서는 줄을 서야하고, 탈 차례가 되면 줄에 선 선착순으로 타게 된다. 또 다른 예시로는 프린터를 생각해보자. 어떤 문서를 프린터를 통해 출력한다고 하자. 그러면 문서의 첫 페이지부터 시작해서 마지막 페이지를 출력하는 순서로 작동한다.   
   
우선적으로 큐에서 사용하는 연산이 있는데 대표적인 것들만 적어보자.(코드를 어떻게 짜느냐에 따라서 연산 종류가 추가되거나 수정될 수 있기 때문)   
* enqueue(data) : data를 큐의 끝부분(마지막부분)에 추가. 새로 추가할 때마다 rear + 1.
* dequeue() : FIFO에 따라 큐의 맨 앞부분의 data를 제거. 제거할 때마다 front + 1.
* isEmpty() : 큐가 비어있는지 확인. rear === front로 판단.
* isFull() : 큐가 꽉 차있는지 확인. rear === n - 1로 판단.(n = 큐의 size)
* peek() : 큐의 맨 앞부분의 data를 확인.   
   
*(front : head의 data 위치를 가리키는 변수 / rear : tail의 data 위치를 가리키는 변수)   
      
위의 연산(method)들로 큐를 만들 때 2가지 종류의 큐를 만들 수 있다.   
1) 선형 큐   
선형 큐는 위에 있는 그림처럼 직선적인 구조를 가진 배열이다(Javascript의 array가 아니다).   
선형 큐 같은 경우에는 단점이 존재하는 데 추가 및 삭제를 반복하다 보면, 어느 순간 데이터를 더 이상 담을 수 없는 상황에 놓이게 된다. 그 이유는 큐의 사이즈만큼 저장할 수 있는 공간이 꽉 찼다고 인식을 했기 때문이다(이러한 error를 overflow라고 한다).   
그렇지만 데이터를 삭제하는 작업도 진행을 했으면 빈 공간이 있는데 왜 공간이 꽉 찼다고 인식을 하는 것일까? 위의 연산에서 설명한 front와 rear가 어떻게 되는지를 통해서 알 수 있다.   
추가와 삭제를 반복하면 front와 rear의 값은 계속 증가를 할 것이다(실제 데이터들의 위치를 이동시키지는 않는다). 하지만 큐의 마지막 공간에 다다르면 front와 rear는 더 이상 증가를 할 수 없게 되고 이 때문에 공간이 꽉 찼다고 인식한다.   
그렇다면 삭제하면서 빈 공간들은 어떻게 될까? 그냥 사용할 수 없는 빈 공간으로 남게 된다.   
그래서 이러한 단점을 보완하기 위해 만든 것이 바로 원형 큐이다.   
      
2) 원형 큐   
![원형 큐](https://user-images.githubusercontent.com/70124288/105370718-349bef00-5c47-11eb-887c-fa362b328f75.png)   
원형 큐는 그림과 같이 시작 지점과 끝 지점이 이어져있는 원 형태의 큐이다. 큐를 원형으로 코드를 구현함으로서 메모리 공간도 더 효율적으로 사용할 수 있다.   
하지만 원형 큐에도 선형 큐에서 처럼의 error 상황이 발생할 수 있다. 바로 꽉찬 상태에서 추가 연산을 했을 때 발생하는 overflow와 완전히 비어있는 상태에서 삭제 연산을 했을 때 발생하는 underflow가 있다.   
그렇기에 원형 큐로 코드를 짤 때는 2개의 error가 발생하지 않도록 처음부터 조건을 짜줘야한다(직접 검색해보면 어떻게 조건을 짜야하는지 많이 나와있다). 이러한 error만 발생하지 않게 해주면 선형 큐에 비해서 더 효율적으로 메모리를 사용할 수 있게 된다.   
그렇다고 무조건 선형 큐보다 원형 큐로 코드를 짜는게 좋다는 것은 아니다. 상황에 따라 다를 수 있는데 선형 큐는 원형 큐보다 코드를 구현하기가 쉽고, Javascript에서는 큐를 만들때 따로 사이즈를 정해주지 않기 때문에(메모리 할당 정책과 가비지 콜렉터에 대해서 검색) 굳이 원형 큐로 코드를 짤 필요가 없다(진짜 어떤 프로그램을 짜는지 상황마다 다르지만, 메모리 효율 측면에선 여전히 비추).   
    
        
이렇게 stack과 queue에 관해서 정리를 다 해봤다. 물론 이 개념을 알고 있다고 해서 직접 구현을 하는게 쉽지는 않다. 하지만 어떻게 돌아가는지 원리를 알고 있으면 시간이 오래 걸리더라도 고민하면서 차근차근 코드를 하나씩 짜다보면 어느샌가 stack과 queue를 구현하는 코드를 짠 자신을 발견하게 될 것이다. 