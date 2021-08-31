---
title:  "[React] Mini market"
excerpt: "React , Express, mongoDB를 사용한 물건을 사고파는 마켓 프로젝트 입니다."

categories:
  - Front-End, Project
tags:
  - [React, Express, mongoDB]

toc: true
toc_sticky: true
 
date: 2021-08-31
last_modified_at: 2021-08-31
---

## mini market project 란?
물건의 이름, 사진, 가격 등의 정보 입력하여 상품을 등록해 이용자들간 거래 할 수 있는 market 프로젝트 입니다.  

### programming stack
__Front-End__: JavaScript, React(library)  
__Back-End:__ Node.js, Express(framework)  
__Database:__ mongoDB(NoSQL)

### 1. 메인 화면
[메인이미지]("./_image/mini-market/main_image_1.png")


### 디렉토리 구성
- __components__ : 여러페이지에서 사용될 component들 [js, css]  
- __pages__ :components들을 이용하여 만들어진 page들 [js, css]  
- __styles__: global적으로 사용될 css file들 [ css ]  

## 진행현황

### 구현해야할 부분
- 상품 게시물을 클릭했을 경우 해당 상품 게시물과 상세페이지를 rendering 해주는 부분
- Login pages
- 카테고리 pages
- 검색 pages 
- etc

### 구현한 부분[미완성]
#### Pages 
- __Main.js:__ 메인화면을 렌더링 해주는 Component 

####  Components
- __Board:__  상품을 등록하였을 때 사용자들이 볼 수 있는 게시물
- __Header:__ market name이 들어가 있는 상단에 위치한 Title 역활을 하는 부분
- __Footer:__ 홈, 검색, 카테고리, 로그인 버튼들이 위치한 부분

#### 사용된 기술
__Javascript:__ (import, export), const, map, function, array function(=>)  
__React:__ JSX, {}, Component, props, className,  