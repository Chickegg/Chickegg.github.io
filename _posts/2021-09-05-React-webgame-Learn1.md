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