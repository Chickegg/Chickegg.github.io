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
last_modified_at: 2021-09-09
---

## 0.create-react-app을 사용하지 않는 이유
- react의 기본원리를 이해하기 위해서
- create-react-app이 무엇을 해주는지 하기 위해
- webpack을 __제대로__ 사용하기 위해서

## 1.초기 세팅해주기
#### jsx 확장자를 쓰는 이유 
jsx문법을 사용하는 React전용 타입 이라는 것을 확실히 인지시켜줄 수 있다는 이점이 있다.

## 2.웹팩 설정
#### entry부분 주의점
만일 client.jsx를 불러오는데 그 파일안에서 자체적으로 import해오는 파일은 entry에 따로 추가해주지 않아도 된다.

#### 2021-09-06 시점 webpack.config.js
```
const path = require('path');
const ReactRefreshWebpackPlugin = require('@pmmmwh/react-refresh-webpack-plugin');

module.exports = {
  name: 'number-baseball-dev',
  mode: 'development',
  devtool: 'inline-source-map',
  resolve: {
    extensions: ['.js', '.jsx'],
  },
  entry: {
    app: './client',
  },
  module: {
    rules: [{
      test: /\.jsx?$/,
      loader: 'babel-loader',
      options: {
        presets: [
          ['@babel/preset-env', {
            targets: {browsers: ['last 2 chrome versions']},
            debug: true,
          }],
          '@babel/preset-react',
        ],
        plugins: ['react-refresh/babel'],
      },
      exclude: path.join(__dirname, 'node_modules'),
    }],
  },
  plugins: [
    new ReactRefreshWebpackPlugin(),
  ],
  output: {
    path: path.join(__dirname, 'dist'),
    filename: '[name].js',
    publicPath: '/dist',
  },
  devServer: {
    devMiddleware: { publicPath: '/dist' },
    static: { directory: path.resolve(__dirname) },
    hot: true
  }
}
```

## React부분

### require와 import의 차이점
__require:__ Node의 module시스템 commonJS  
__import:__ ES2015
- export default로 한것은 import로 가져와야 한다.  __파일에서 1번만 사용가능__
- export const 변수명 은 { 변수명 } 으로 가져와야 한다. __여러번 사용가능__

__비교__ 
- module.exports 와 export default는 엄연히 다른 것이지만 현재 수준에서는 호환이 된다고 생각하면 편한다.


### class, hooks 
__class:__ state를 사용한다.조금 옛날의 코드라고 생각할 수 있다.  
__hooks:__ useState 등 hooks를 사용한다. 리액트에서는 hooks사용을 권장한다.

### state 주의점
- state 에서는 {a: 1} 처럼 이중삼중 객체배열구조를 쓰지 않는 것이 실수를 줄일 수 있는 방법이다. (자료구조를 간단히 한다.)

### [class] 성능최적화를 위한 shouldComponentUpdate

리액트는 생각만큼 똑똑하지 않아서 state의 변화가 생기지 않아도 렌더링을 하는 경향이 있다.  
우리는 그래서 component상단에 shouldComponentUpdate 메소드를 사용하여 state의 변화가 생겼을 때만  
렌더링을 시켜주는 명령을 입력하여 주어야 한다.
```
shouldComponentUpdate(nextProps, nextState, nextContext) {
  if (this.state.counter !== nextState.counter) {
    return ture; // state에 변화가 생겼다면 component를 재 렌더링 해준다.
  } 
  return false; 
}
```

### [class] 조금더 편하게 성능최적화 하기 PureComponent,
class를 사용할 경우 Component앞에 Pure를 붙여주게되면 알아서 랜더링 여부를 파악한다.
작동원리: state의 변경여부를 보고 판단을 한다.  
그러나 __단점__ 이 있다. __객체__ 나 __배열__ 같은 구조가 존재하는 경우 판단을 어려워 한다.  
예를 들어 기존의 배열에 push를 했을 경우 PureComponent는 알아차리지 못한다.  
그래서 우리는 앞서 설명한 것 처럼 배열을 [...(전개연산자)로 복사를 해준다음에 , 1]추가해 주어야 한다.
```
class Test extends PureComponent {

}
```
### [hooks] PureComponent와 같은 역활을 하는 memo 
Component를 memo(component)로 감싸주면 PureComponent와 같은 역활을 한다.
이때 자식들이 모두 PureComponent또는 memo를 적용을 했으면 부모도 같이 적용을 해줄 수 있다.
```
const Test = memo(() => {
  return (

  );
});
```
### s