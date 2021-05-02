---
title:  "[Java] Queue 사용법"
excerpt: "예시코드와 함께 java에서 Queue를 어떻게 사용하는지 알아봅니다."

categories:
  - Java
tags:
  - TIL

comments: true
last_modified_at: 2021-04-28T00:00:00-23:59
---

java의 Queue class의 대표적인 method들을 정리하면 다음과 같다.

```java
// 라이브러리 import
import java.util.LinkedList;
import java.util.Queue;

// LinkedList를 활용하여 Queue 초기화 (Create)
Queue<Integer> q = new LinkedList<>(); // Integer 말고도 다른 DataType Generic으로 사용가능

// 삽입 (Update)
q.add(1); // 삽입에 성공시 true, 실패하였을 경우 Exception 반환 
q.offer(2); // 삽입에 성공시 true, 실패하였을 경우 false 반환 

// 참조 (Read)
queue.peek(); // Queue의 첫번째 값 참조

// 반환 (Read and Delete)
q.poll(); // Queue의 첫번째 값을 반환. 비어있다면 null 반환

// 제거 (Delete)
q.remove(); // Queue의 첫번째 값 제거
q.clear(); // Queue의 값 전체 초기화

// 사이즈 확인
q.size()
```



여기서 offer()와 add()가 기능이 중복된다.

물론 Exception을 발생시켜 프로그램을 중단 시켜야하는 경우도 있겠지만. 

알고리즘 문제풀이에 한해서는 offer의 false 값을 받아서 처리하는 것이 더욱 간편할 것으로 보인다.