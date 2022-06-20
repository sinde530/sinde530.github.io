---
emoji: 🦭
title: webpack-dev-server 사용해보기
date: '2022-06-12 20:21:00'
author: Crong
tags: Webpack Javascript
categories: Webpack Javascript
---

# webpack-dev-server 사용하기

프론트에서 js모듈화를 진행하기 위해 `babel` 과 `webpack` 을 적용하였다.

ES6 문법을 브라우저에서도 사용하기 위해서 babel을 적용하고, 

그걸 하나로 모듈화를 해주기 위해 webpack을 적용하였다.

그 결과는 html View에서 webpack으로 뭉쳐진 bundle.js하나만 로드해주면 모든 것이 한방에 해결되는 편리함을 맛 볼수 있었다!

`webpack`에 대한 공부를 대충한 탓이 여태까지 그저 파일간의 의존성같은 부분을 해결해주는 정도로만 생각했지만 아주 많은 기능들이 있었다.

그중 하나가 바로 `webpack-dev-server` 이다.

이걸 알기 전 까지 webpack을 돌린 후에 html파일을 따로 vscode extention liveserver로 따로 html을 서버에 띄워 테스트를 하였다.

## webpack-dev-server란?

<b>webpack-dev-server</b>는 빠른 실시간 리로드 기능을 갖춘 개발 서버이다
- 디스크에 저장되지 않는 <b>메모리 컴파일</b>을 사용하기 때문에 속도가 빨라진다.
- webpack.config.js에도 devServer 옵션을 통해 옵션을 지정하여 사용이 가능하다.


## webpack-dev-server 동작원리
1. 서버 실행 시 소스파일들을 번들링하여 메모리에 저장소스 파일을 감시한다.
2. 소스 파일이 변경되면, 변경된 모듈만 새로 번들링함.
3. 변경된 모듈 정보를 브라우저에 전송한다.
4. 브라우저는 변경을 인지하고 새로고침되어도 변경사항이 반영된 페이지를 로드한다.

이미 webpack을 설치하면서 사용하고 있었기에 dev-server도 설치하였다.

```typescript
yarn add webpack webpack-cli webpack-dev-server
```

```typescript
// webpack.config.js

module.exports = {
  mode: 'development',
};
```

<br>

## 명렁어
> yarn webpack-dev-server

라고 치기엔 너무 귀찮으니 `package.json`파일에서 스크립트 작성을 해주자.

```typescript
// package.json

"scripts": {
    "dev": "webpack serve --mode development",
  },
```

> yarn dev
