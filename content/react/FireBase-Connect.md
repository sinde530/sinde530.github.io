---
emoji: πΏ
title: νμ΄μ΄λ² μ΄μ€ μμλ‘κ·ΈμΈ μ¬μ©νκΈ°
date: '2022-05-12 16:57:00'
author: Crong
tags: React FireBase
categories: React FireBase
---

## νμ΄μ΄λ² μ΄μ€ μ¬μ©κΈ°

νμ΄μ΄λ² μ΄μ€ λ‘κ·ΈμΈ ν νλ‘μ νΈλ₯Ό νλ μμ±νλ€.

> μ λλ¦¬ν±μ€ μ¬μ©νμ§ μμΌλ©΄ μ²΄ν¬ μν΄λ λ¨.

<br>

λ°μμλ </>λͺ¨μ ν΄λ¦­νλ€.

![](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F7ed61a96-5f05-4456-acc0-32c39fa76db4%2FUntitled.png?table=block&id=71681741-a542-4b88-89dd-e383b925b421&spaceId=f08f49e0-d5e2-4c6e-9785-524d05da8a03&width=2000&userId=00f35be7-f598-4c28-bec1-5ca4b2e59847&cache=v2)

<br>

![](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fea341961-70ab-4a00-985d-8e25e8297ebe%2FUntitled.png?table=block&id=ee4bd618-7e98-4814-8fd7-c18c9e54ce89&spaceId=f08f49e0-d5e2-4c6e-9785-524d05da8a03&width=2000&userId=00f35be7-f598-4c28-bec1-5ca4b2e59847&cache=v2)

νμ΄μ΄λ² μ΄μ€ νΈμ€νμ νμ§μμ μ²΄ν¬λ₯Ό μνκ³  λμ΄κ°λ€.

![](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F1cc3cee2-b684-42f6-a56f-fdbab52f4296%2FUntitled.png?table=block&id=99952e6b-d8a0-42bc-a2e4-b0e6148214e2&spaceId=f08f49e0-d5e2-4c6e-9785-524d05da8a03&width=2000&userId=00f35be7-f598-4c28-bec1-5ca4b2e59847&cache=v2)

<br>

### μ΄ κ΅¬λ¬Έλ€μ λ³΅μ¬ν΄λμ

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

## `Authentication` λ‘ λμ΄κ° μΆκ°ν  λΆλΆλ€μ μΆκ°νμ.

![](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F9a4882c4-a651-4b79-b132-8b1666a86ca6%2FUntitled.png?table=block&id=3ee3ba7c-531c-45a9-b121-4ab4e565ec5d&spaceId=f08f49e0-d5e2-4c6e-9785-524d05da8a03&width=2000&userId=00f35be7-f598-4c28-bec1-5ca4b2e59847&cache=v2)

<br>

### λ‘κ·ΈμΈ μ κ³΅μμ²΄ μΆκ°μ μ½λλ‘ λμ΄κ°λ€.

## λ¦¬μ‘νΈ μ½λ μμ±

```javascript
yarn create react-app someThing
```

### npm μ¬μ©μ

```javascript
npm install firebase
```

### yarn μ¬μ©μ

```javascript
yarn add firebase
```

### src folderμ λ€μ΄κ° `firebase.js`νμΌμ λ§λ  ν μ μ λ³΅μ¬ν΄λμ λ΄μ©λ€μ λ£λλ€.

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

κ·Έ νμ μμ μ΄ μ΄λ»κ² μ¬μ©ν μ§ κ΅¬ννλ©° λ‘κ·ΈμΈμ μμ±ν  μ½λλ₯Ό λ§λ€λ©΄ λλ€.

<br>
<br>

```toc

```
