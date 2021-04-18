---
title:  "[Java] 왜 static variable은 static method에서 밖에 못쓸까?"
excerpt: "Java_Event_Timeline"

categories:
  - Java
tags:
  - TIL

comments: true
last_modified_at: 2020-08-09T22:00:00-00:00
---

질문: _왜  static method에서는 static variable만 쓸 수 있을까?_



  아래 그림에서 알 수 있듯이 

1. instance가 생성되기 전에 static method이 global space에 할당되기 때문에 
2. 이에 맞춰 할당되는static variable만이 static mehod에 사용이 가능하다. 
3. instance varialbe의 경우 instance 생성되어 heap 영역에 할당된 이후. 즉, static method 생성 이후에 생성되기 때문에 사용이 불가능한 것이다.

<img width="1177" alt="Java_Events_Timeline" src="https://user-images.githubusercontent.com/60743304/115131498-8defa080-a033-11eb-92e4-568e39a38eaa.png">

<small>FIG 1. Java이 Event Timeline</small>

​	위의 타임라인에 대한 간단한 설명을 하면 다음과 같다.

1. Compile time에는 우리가 작성한 Source Code를 JVM이 이해할 수 있도록 바꿔주는 작업을 수행함

2. Run Time에는 프로그램이 실행됨. 그리고 이와 동시에 compile로 얻은 Byte Code, 모든 class, static 관련 값들을 global space에 할당한다.

3. Object Time에는 instance가 생성시 heap에 값이 할당이 된다. 그리고 class의 변수들인 Member variable이 초기화 된다.

4. Method Time에는 method가 수행되면서 필요한 정보들이 Activation record (method 안의 local variables 정보들)이 stack 영역에 쌓이게 된다. 

   - 여기서 재미있는 점은 local variable은 member variable과 달리 primitive data type을 사용을 하여도 int => 0, boolean => false, char => ''\u0000'과 같이 초기화가 되지 않는다.

   - 개인적인 추측이지만 이는 method 호출시 stack에 activation record가 쌓였다가, 사라지는 빈도가 member variable 보다 월등히 높아서 이를 프로그램 작성자가 꼭 사용할 값만 명시적으로 선언하라는 의도라고 생각한다. 

   - 왜냐하면 컴퓨터 구조에서 알 수 있듯이 memory Input/Output에서 굉장히 큰 시간소비가 일어나기 때문에 최대한 불필요한 memory 할당을 줄이는 것이 성능향상을 위해 좋은 전략이기 때문이다.