---
title:  "[Querydsl] '~MySQL server version for the right syntax~'에러해결하기"

excerpt: "Querydsl 사용 중 겪은 mysql 버전관련 에러해결 과정을 소개합니다."

categories:
  - Spring Data
tags:
  - Querydsl
  - MySQL
  - Troubleshooting

comments: true
last_modified_at: 2021-09-08T00:00:00-23:59
toc: false
toc_sticky: false
---

*Google Cloud Platform* (GCP)의 SQL을 이용하여 [맞춤분양필터](https://toadhome.onelink.me/JJLY/3fc8cf8e) 앱 서비스의 Mysql DB sever를 운영하고 있습니다.

완전 동일한 Querydsl 코드임에도 불구하고 개발서버에서만 ~~(저만 모르는)~~에러가 발생하였습니다.

> java.sql.SQLSyntaxErrorException: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'double precision)*1.3 between 33.05785 and 66.1157



에러가 뜨면 우선 에러 메세지를 봐야겠죠. 

`~MySQL server version~ ` 에러 문구보고 서버의 MySQL 버전은 확인해본 결과 개발서버는 5.x, 프로덕션은 8.x의 서버로 배포되어 있었습니다. 

테스트용으로 쓰는 개발 서버가 프로덕션과 환경이 다르다니... 바보같은 실수가 아닐수 없습니다.



왜? 위와 같은 문제가 생기는지 MySQL 메뉴얼을 더 자세히 알아본 결과

> - **Additional target types for casts.** The functions [`CAST()`](https://dev.mysql.com/doc/refman/8.0/en/cast-functions.html#function_cast) and [`CONVERT()`](https://dev.mysql.com/doc/refman/8.0/en/cast-functions.html#function_convert) now support conversions to types [`DOUBLE`](https://dev.mysql.com/doc/refman/8.0/en/floating-point-types.html), [`FLOAT`](https://dev.mysql.com/doc/refman/8.0/en/floating-point-types.html), and [`REAL`](https://dev.mysql.com/doc/refman/8.0/en/floating-point-types.html). Added in MySQL 8.0.17. See [Section 12.11, “Cast Functions and Operators”](https://dev.mysql.com/doc/refman/8.0/en/cast-functions.html). 

와 같은 MySQL 8.0에서의 CHANGLOG를 찾을수 있었습니다. 



Querydsl 코드에서 "054.1230A"와 같은 청약주택의 주택형의 평수 값 54.1230 활용하기 위해 아래와 같은 로직을 추가한 부분이 Mysql 5.x에서는 지원이 안되었던 것입니다.

```java
Qhouse
.주택형
.castToNum(Double.class)
// 추가 로직 수행
```



매물정보를 불러오는 복잡한 필터쿼리를 Querydsl 기반으로 처리하다보니 ANSI SQL을 벗어난 구문도 작성해볼 기회가 생긴 것 같습니다 :)



필터링이 핵심인 앱의 Backend 개발을 하다보니 강의나 블로그의 예제를 벗어나 Querydsl을 하드하게 사용해보았는데요.

이후에는 Querydsl을 이용한 복잡한 동적쿼리 처리 경험에 대하여 포스팅하겠습니다.



부족한 글 끝까지 읽어주셔서 감사합니다.🙏



## 참조

- [**MySQL 8.0 Reference Manual**](https://dev.mysql.com/doc/refman/8.0/en/mysql-nutshell.html)
