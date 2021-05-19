---
title:  "[CS] git add, commit, push를 한 명령어로 끝내기"
excerpt: "매번 push 하기 위해 해야했던 git add, commit push를 한 명령어로 끝내봅시다!"

categories:
  - CS
tags:
  - TIL

comments: true
last_modified_at: 2021-05-19T00:00:00-23:59
---

# 발단

여러 사람이 함께 작업하는 공간이 아닌, 혼자만 사용하는 개인 repo에도 한 글자만 수정해도 최종적으로 github repo에 반영를 하기위해서는 git add . => git commit -m "msg" => git push를 모두 terminal에 작성해주어야 했다. 

이게 어느 순간 상당이 번거롭다고 느껴져 구글링 하던 중, 좋은 방법이 있어 이를 공유하고자 한다.



# 방법

방법은 간단한데 Mac OS의 경우 root path에서 .bash_profile에 (.bashrc 아님 주의)/ window OS의 경우 .bashrc 파일 안에 아래의 함수를 추가해주면 된다.

```shell
# Shortcut for
# git add . => git commit -m "$*" => git push origin master
function lazygit() {
    git add .
    git commit -a -m "$*"
    git push
}
```

그리고 변경 사항을 terminal에 반영해주기 위하여 terminal에서 아래의 명령어를 실행 시켜주면 끝!

```shell
source ~/.bash_profile
```

그러면 lazygit message 만 terminal에 입력하면 

git add . => git commit -m "message" => git push origin master를 한번에 수행해준다.



# 결과

![image](https://user-images.githubusercontent.com/60743304/118743400-44da7880-b88d-11eb-91fd-744c201e9ed5.png)

위 그림과 같이 lazygit add python team note라고 terminal에 입력하면 

git add . => git commit -m "add python team note" => git push origin master가

한 명령어로 순차적으로 수행되었음을 알 수 있다.



![image](https://user-images.githubusercontent.com/60743304/118743703-d0eca000-b88d-11eb-898b-626a0d21f30d.png)

실제로 remote repository에도 잘된 것을 확인할 수 있다.



<small>참조: https://stackoverflow.com/questions/19595067/git-add-commit-and-push-commands-in-one</small>