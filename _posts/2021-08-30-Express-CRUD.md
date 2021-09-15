---
title:  "라매개발자님의 최소한의 백엔드 지식[CRUD]"
excerpt: "라매개발자님의 프론트엔드 개발자가 최소한으로 알아야 할 백엔드 지식과 코드(API) 영상을 정리한 POST"

categories:
  - Back-End
tags:
  - [Back, Life Manager, Express , CRUD]

toc: true
toc_sticky: true
 
date: 2021-08-29
last_modified_at: 2021-08-29
---

## 0. Client는 요청 Server는 응답!
client가 server에게 필요한 자원들을 요청을 하게되면 서버는 우리에게 그 자원들을 전달해준다.  
이러한 자원들을 가지고 브라우저에서 화면은 렌더링해서 우리에게 보여주는 것이다.  
예를 들어 서버야 1번 id값을 가진 data를 나에게 보내줘 라고 요청을 하면 server는  
 그 조건에 맞는 data를 우리에게 담아준다.

단순한 text가 아니라면 sendFile()등을 통해서 File을 보내 줄 수도 있다.  
__render__ 을 사용하기 위해서는 __ejs__ ,__pug__ 등의 키워드로 검색을 해보라고 한다.

## 1. api를 호출하여 CRUD 기능 사용하기 

__C__ reate, __R__ ead, __U__ pdate, __D__ elete (공통된 핵심기능)  
[postman](https://www.postman.com/)이라는 Tool을 이용해서 api서버가 잘 동작하는지 확인할 수 있다.

### 1-1. __params를 이용하는 방법__ (/:뒤의 url은 title이 된다.)

    app.get('/database/:title', function (req, res) {
        const title = req.params.title;
        database.push({
            id: database.length,
            title,
        });
        res.send("값 추가 완료.")
    }
    
      
### 1-2 __req.body를 이용하는 방법__  
__Express__ 의 __bodyparser__ 를 이용하면 req.body를 사용할 수 있다.  
여기서 body란 data의 본문 전체라고 할 수 있다.

### 1-3 동일한 url에서 CRUD기능을 모두 구현하기 위한 방법
__http 메소드__ 를 통해서 api를 구분할 수 있다.  
__C__ reate는 __POST__  
__R__ ead는 __GET__  
__U__ pdata는 __PUT__, __PATCH__  
__D__ elete는 __DELETE__ 를  
 통해서 구분을 해준다면 동일한 url에서 다양한 기능이 작동하게 할 수 있을 것이다.