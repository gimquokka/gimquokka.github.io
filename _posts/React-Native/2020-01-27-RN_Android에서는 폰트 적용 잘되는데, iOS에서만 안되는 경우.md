---
title:  "[React Native] Android에서는 폰트 적용이 잘되는데, iOS에서만 안되는 경우"
excerpt: "React Native 사용시 Android에서는 폰트 적용이 잘되는데, iOS에서만 안되는 경우에 해결책을 소개합니다."

categories:
  - React-Native
tags:
  - Troubleshooting

comments: true
last_modified_at: 2021-10-11T22:00:00-00:00
---

### 문제상황

[**RN(Reacct Native)에서 커스텀 폰트 사용하기**
*앱을 개발하다보면 특정 폰트를 적용할 경우가 발생합니다. 이 블로그에서는 RN(React Native)에 어떻게 특정 폰트를 적용하고 사용하는지 설명하려고 합니다. 저는 보통 구글의 Noto Sans 폰트를…*dev-yakuza.github.io](https://dev-yakuza.github.io/ko/react-native/react-native-custom-font/)

[**5. 리액트 네이티브 ( React Native ) : 폰트 설정**
*리액트 네이티브에서 폰트 설정하는 방법을 알아보겠습니다. 보통 Expo SDK를 사용하거나 React Nati...*blog.naver.com](https://blog.naver.com/PostView.nhn?blogId=gi_balja&logNo=221292933731&categoryNo=28&parentCategoryNo=0&viewDate=&currentPage=1&postListTopCurrentPage=1&from=postView)

RN의 폰트를 변경하기 위하여 글을 찾아보았습니다. 

위에 다른 개발자분들께서 폰트 적용하는 법을 참고하였고, 이에 따라 폰트 변경 중 위 블로글 Android는 폰트 반영이 되는데, iOS만 안되는 문제가 발생하였습니다.

<br/>

### 해결방법

폰트 파일명이 NoteSanR.ttf, NoteSanT.ttf 이렇게 돼 있어서 그대로 적용하였던 것이 문제였습니다. 

iOS 같은 경우 Xcode의 info.plist에 NoteSanR 이렇게 등록이 되어도 NoteSan-Regular과 같은 형식으로만 인식되는 경우가 있습니다. 

따라서 파일명을 NoteSan-Regular과 같은 형식으로 변경 후 등록하니 iOS도 폰트 반영이 잘 되었습니다.

<br/>

### 첨언

위 문제를 키워드 잡고 구글링한 결과 StackOverflow에서 가장 추천이 높은 답변이 Xcode의 binary~? ,~copy? 에서 ~ttf 파일을 새로 등록하라는 것이어서 그렇게 했다가 아주 크게 혼이 났습니다… 

git에서 이전 버전으로 복구해도 파일명이 같아 Xcode의 설정값이 변경되지 않고, 문제가 어디서 생긴 것인지도 몰라 시간을 많이 잡아먹었는데요. 

‘역시 RN 개발하면서 잘 모르는 Native 부분을 함부로 만지지 않는 것이 좋구나…’ 하고 많이 느꼈습니다.

<br/>

부족한 글 읽어주셔서 감사합니다.🙏