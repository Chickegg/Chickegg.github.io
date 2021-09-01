---
title:  "[Git hub] 협업 방법
excerpt: "Git hub로 협업하기 위한 방법을 정리한 POST"

categories:
  - Front-End, Github
tags:
  - [Github, commit, branch, merge, conflict]

toc: true
toc_sticky: true
 
date: 2021-08-31
last_modified_at: 2021-08-31
---

## 순서
- 코드를 작성해서 코드리뷰를 부탁하고 develop브랜치에다가 merge를 하는 상황
- 요구사항을 issues에 남긴다. (사진등의 파일로 해주면 좋다.)
- 라벨을 남긴다. 팀원과 협의 해야한다. 
- Assignees 작업의 대상자가 담겨있어야 한다.

## 개발단계
- git에서 branch를 바꿔준다. 같은곳을 바라보지 않고 있으면 pull을 한번해서 원격, 로컬이 같은 곳을 바라보게 해준다.  
- branch 규칙에따라 이동해준다.
- 로컬에서 테스트 후 동작이 잘 된다면 코드를 커밋을 하여 스테이징 상태로 만들어준다.
- pull request에 올려서 코드리뷰를 받아야 한다.
-git push --set-upstream origin feat/[branchname]

- git hub에서 compare버튼을 누르면 PR을 작성하면 된다.
- 작업내용과 설명이 적혀져 있어야 한다.
- Reviewer에 우리팀원들을 선택한다.

- 이슈와 연관된 pull request라는 것을 알려주기 위해서 open, close중 완료가 되면 close로 바꿔준다.  
- closes [#1] #1은 이슈번호이다.
- linked issue로 자동으로 정해진다.

## 리뷰달기
- 마음에 들지 않는 코드가 나왔으면 pus눌러서 command를 달아주면 된다.
- Approve를 일정수준이상 받았다면 merge를 눌러준다. (완료)


## conflict상황
2명의 작업자가 같은 컴포넌트를 수정하는 작업을 한다면?
- gcob work1이라고 해준다. classname을 하나 추가한다고 생각하면 된다. 추가하는 작업 필요
- conflict 가 난 이유 내가 지정할 때의 상태와 현재 상태가 다르기 때문

## conflict 해결 방법
- 에디터를 이용한 방법 코드자체를 직접 건들이는 방식 2가지중 옳지않은 것을 지운다. [권장 X]

- 커맨드라인을 통해 해결하는 방법
develop로 체크아웃을 하고 pull을 해준다. work2와 devlop를 merge를 하면 conflict가 날것이다.

### 3가지 옵션
- Current Change: 선택지 1
- Incoming Change 선택지 2
- Both Change : 선택지 1,2 둘다
멀 남길지 정하고 파일저장을 누르고 add해주고 merge commint을 날리면 merge가 이루어진다.
- git push를 통해서 conflict가 해결된 상황을 work로 push를 해준다.


