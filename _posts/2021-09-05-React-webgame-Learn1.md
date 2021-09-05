---
title:  "[React] React를 사용하여 Web웹 게임 구현하기"
excerpt: "React를 사용하여 간단한 웹게임 예제들을 다뤄보는 POST"

categories:
  - Front-End, Learn, 입문
tags:
  - [React, webpack, 입문]

toc: true
toc_sticky: true
 
date: 2021-09-05
last_modified_at: 2021-09-05
---

## create-react-app을 사용하지 않는 이유
- react의 기본원리를 이해하기 위해서
- create-react-app이 무엇을 해주는지 하기 위해
- webpack을 __제대로__ 사용하기 위해서

## 초기 세팅해주기
#### jsx 확장자를 쓰는 이유 
jsx문법을 사용하는 React전용 타입 이라는 것을 확실히 인지시켜줄 수 있다는 이점이 있다.

## 웹팩 설정
#### entry부분 주의점
만일 client.jsx를 불러오는데 그 파일안에서 자체적으로 import해오는 파일은 entry에 따로 추가해주지 않아도 된다.