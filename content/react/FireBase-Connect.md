---
emoji: 🍿
title: 파이어베이스 소셜로그인 사용하기
date: '2022-05-12 16:57:00'
author: Crong
tags: React, FireBase
categories: React, FireBase
---

## 파이어베이스 사용기

파이어베이스 로그인 후 프로젝트를 하나 생성한다.

> 애널리틱스 사용하지 않으면 체크 안해도 됨.

<br>

밑에있는 </>모양 클릭한다.

![](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F7ed61a96-5f05-4456-acc0-32c39fa76db4%2FUntitled.png?table=block&id=71681741-a542-4b88-89dd-e383b925b421&spaceId=f08f49e0-d5e2-4c6e-9785-524d05da8a03&width=2000&userId=00f35be7-f598-4c28-bec1-5ca4b2e59847&cache=v2)

<br>

![](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fea341961-70ab-4a00-985d-8e25e8297ebe%2FUntitled.png?table=block&id=ee4bd618-7e98-4814-8fd7-c18c9e54ce89&spaceId=f08f49e0-d5e2-4c6e-9785-524d05da8a03&width=2000&userId=00f35be7-f598-4c28-bec1-5ca4b2e59847&cache=v2)

파이어베이스 호스팅을 하지않아 체크를 안하고 넘어간다.

![](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F1cc3cee2-b684-42f6-a56f-fdbab52f4296%2FUntitled.png?table=block&id=99952e6b-d8a0-42bc-a2e4-b0e6148214e2&spaceId=f08f49e0-d5e2-4c6e-9785-524d05da8a03&width=2000&userId=00f35be7-f598-4c28-bec1-5ca4b2e59847&cache=v2)

<br>

### 이 구문들을 복사해놓자

```javascript
// Import the functions you need from the SDKs you need
import { initializeApp } from 'firebase/app';
import { getAnalytics } from 'firebase/analytics';
// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
// For Firebase JS SDK v7.20.0 and later, measurementId is optional
const firebaseConfig = {
  apiKey: 'AIzaSyATJcybddzK1Kkqr98erjUhaq3iEiLlye0',
  authDomain: 'example-fa01a.firebaseapp.com',
  projectId: 'example-fa01a',
  storageBucket: 'example-fa01a.appspot.com',
  messagingSenderId: '946125928362',
  appId: '1:946125928362:web:2bdc886f782c05c6ca5dd3',
  measurementId: 'G-QPR8QBRSTD',
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
const analytics = getAnalytics(app);
```

<br>
<br>

## `Authentication` 로 넘어가 추가할 부분들을 추가하자.

![](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F9a4882c4-a651-4b79-b132-8b1666a86ca6%2FUntitled.png?table=block&id=3ee3ba7c-531c-45a9-b121-4ab4e565ec5d&spaceId=f08f49e0-d5e2-4c6e-9785-524d05da8a03&width=2000&userId=00f35be7-f598-4c28-bec1-5ca4b2e59847&cache=v2)

<br>

### 로그인 제공업체 추가시 코드로 넘어간다.

## 리액트 코드 작성

```javascript
yarn create react-app someThing
```

### npm 사용시

```javascript
npm install firebase
```

### yarn 사용시

```javascript
yarn add firebase
```

### src folder에 들어가 `firebase.js`파일을 만든 후 전에 복사해놓은 내용들을 넣는다.

```javascript
const firebaseConfig = {
  apiKey: '',
  authDomain: '',
  projectId: '',
  storageBucket: '',
  messagingSenderId: '',
  appId: '',
  measurementId: '',
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
const analytics = getAnalytics(app);
```

그 후엔 자신이 어떻게 사용할지 구현하며 로그인에 작성할 코드를 만들면 된다.

<br>
<br>

```toc

```
