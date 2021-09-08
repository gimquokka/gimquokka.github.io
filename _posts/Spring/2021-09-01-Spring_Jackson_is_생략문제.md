---
title:  "[Spring] Response json에서 boolean의 is가 생략되는 문제"
excerpt: "Response json에서 boolean의 is가 생략되는 문제를 해결합니다."

categories:
  - Spring
tags:
  - Troubleshooting
  - Jackson

comments: true
last_modified_at: 2021-09-01T00:00:00-23:59
toc: true
toc_sticky: true
---

# 문제

Spring Boot에서 Dto로 Response를 반환 시 primitive boolean type의 변수의 변수명이 is~로 시작하면 is가 생략되는 재미있는? 문제가 있었습니다. Spring Boot에서는 Response 시 자바 객체를  jackson library를 이용하여 json으로 매핑하여 반환하기 때문에 정확히는 jackson의 특징일 것 입니다.



<img width="618" alt="todhome-backend-v0 1 – FiltermapVo java 2021-09-01 17-15-17" src="https://user-images.githubusercontent.com/60743304/131636875-475f2602-ccb7-4340-91d7-82bd91145d2c.png">



# 해결

구글링 결과 JsonProperty annotation을 이용하여 json 매핑 될 key 값을 강제지정 해주면 된다고 하여 시도해보았습니다. 

그 결과 JsonProperty 값과 원래 변수 값이 모두 출력되는 더욱 놀라운 문제가 발생하였습니다....ㅎ

![todhome-backend-v0 1 – FiltermapVo java 2021-09-01 17-16-40](https://user-images.githubusercontent.com/60743304/131637058-30d5880e-ee56-45bc-8025-235fde6f158b.png)



이후 간단히 Wrapper type을 이용하여 primitive type의 boolean을 Boolean Class type으로 수정함으로서 문제를 해결할 수 있었습니다.

<img width="511" alt="todhome-backend-v0 1 – FiltermapVo java 2021-09-01 17-12-40" src="https://user-images.githubusercontent.com/60743304/131636684-c7f58b92-a9ce-425d-97a9-2cb99dc8b71e.png">



대단한 문제는 아니지만 처음 마주치면 버그를 잡기 힘든? 재미있는 문제인 것 같아 공유하게 되었습니다.