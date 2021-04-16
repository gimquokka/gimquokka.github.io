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
3. instance varialbe의 경우 instance 생성되어 heap 영역에 할당되고 나서야, 즉, static method 생성 이후에 생성되기 때문에 사용이 불가능한 것이다.

![Java_Events_Timeline](./img/Java_Events_Timeline.png)

<small>FIG 1. Java이 Event Timeline</small>