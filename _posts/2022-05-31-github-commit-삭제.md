---
layout: post
title: github commit 변경/삭제
author: RobotOps
description: github에 잘못올린 commit을 변경 또는 삭제하는 방법
categories: [Dev, github]
tags: [git, github, commit, delete]
date: '2022-05-31 20:10:00 +0900'
---

> github을 사용하다가, 잘 못 올린 commit을 변경 또는 삭제하고 싶다. <br>
> 완벽이 필요한? 또는 public repository에 부족한 코딩실력이 들어날까봐, 실수로 올린 코드를 변경 또는 삭제하고 싶을때 사용하는 아주 유용한 방법<br>

# github commit 변경
- 변경하고 싶은 코드를 수정후 add하여 staging area로 보낸다.
```bash
$ git add XXX # XXX:변경한 파일 명
$ git add . # 변경한 모든 내용을 올리고 싶을 때
```
- staging한 내용을 local repository의 마지막 commit에 합친다.<br>
  이 때, 마지막 commit의 commit message를 수정하도록 편집기가 열린다. <br>
  message를 수정후 저장하고 나가면 마지막 commit에 변경점이 추가된다.
```bash
$ git commit --amend
```
- github에 변경된 local commit을 강제로(forced) push 한다
```bash
$ git push --force
```


# github commit 삭제
- 돌아가고 싶은 시점으로 local repository를 reset 한다. --hard 옵션은 해당 지점 이후의 변경내용을 삭제해준다
```bash
$ git reset --hard 3dc01a5a
```
- reset한 local repository를 remote repository(github)으로 강제(forced) push
```bash
$ git push -f origin master
```

## [주의사항]
- force 옵션은 에러가 나는 상황들을 무시하고 덮어씌우므로 항상 조심해서 사용해야 한다
- 특히, 다수가 같이 작업하는 github에 무심코 force옵션을 남발하는 경우, 다른사람이 올린 commit을 날려버릴 수도 있다