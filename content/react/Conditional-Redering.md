---
emoji: ⏰
title: React 조건부 렌더링
date: '2022-05-01 20:10:00'
author: Crong
tags: React
categories: React
---

## 조건부 렌더링 (Conditional Rendering)

=> 조건부 렌더링이란 특정 조건에 따라 다른 결과물을 렌더링 하는 것을 의미한다. <br>
예를 들어, App 컴포넌트에서 Hello 컴포넌트를 사용할 때 isLoggedin이라는 Props를 설정해 보겠다.

```javascript
import React from 'react';
import Hello from './Hello';

function App() {
  return (
    <>
      <Hello name="Crong" isLoggedIn={true} />
    </>
  );
}
export default App;
```

=> 여기서 true는 JavaScript 값이기에 중괄호로 감싸준다.

간단하게 Props를 destructuring 하여 name을 사용한다면 아래와 같이 사용이 가능하다.

```javascript
import React from 'react';

function Hello({ name, isLoggedIn }) {
  return (
    <>
      <p> 안녕하세요 {name} </p>
    </>
  );
}
export default Hello;
// 안녕하세요 Crong
```

### 삼항연산자를 사용해보자.

로그인이 되었을때 즉 {isLoggedIn=true}일 경우, "로그인 완료" 라는 문구를 추가적으로 보여주고, false일 경우엔 null이 되어 아무런 문구도 추가적으로 띄우지 않게 해보자.

```javascript
import React from 'react';

function Hello({ name, isLoggedIn }) {
  return (
    <>
      {isLoggedIn ? '로그인 완료' : null} 안녕하세요 {name}
    </>
  );
}
export default Hello;

// { 조건 ? 조건이 true일 경우 결과}
// { 조건 : 조건이 flase일 경우 결과}

// 로그인 완료 안녕하세요 Crong
```

현재는 {isLoggedIn = true} 이기 때문에 문구가 추가된것을 확인할 수 있다.

하지만 위와같이 내용이 달라지는게 아니라 보여주거나,안보여거나 하는 상황에서는 `&&`연산자를 사용하는것이 더 간편하다. 추가적으로 name에 대해 조건을 추가 해보자.

```javascript
import React from 'react';

function Hello({ name, isLoggedIn }) {
  return (
    <>
      {isLoggedIn && '로그인 완료'} 안녕하세요 {isLoggedIn ? name : 'guest'}
    </>
  );
}
```

App.js로 돌아가 {isLoggedIn = false}로 변경하고 값을 확인하면

```javascript
// 안녕하세요 guest
```

{isLoggedIn = false이기 때문에 앞에 문구는 추가되지 않고, name 대신 `guest`라는 문구가 출력된다.

삼항연산자를 이용하여 컴포넌트 또한 조건부 렌더링이 가능하다.

로그인이 되었을 경우, UserPage 컴포넌트를 보여주고 리고은일 경우 GuestPage 컴포넌트를 보여주자.

```javascript
import React from 'react';
import UserPage from './UserPage';
import GuestPage from './GuestPage';

function Hello({ name, isLoggedIn }) {
  return <>{isLoggedIn ? <UserPage name={name} /> : <GuestPage />}</>;
}

export default Hello;
```

## 로그인일 경우 컴포넌트

```javascript
import React from 'react';

function UserPage({ name }) {
  return <>로그인 완료 안녕하세여 {name}</>;
}
export default UserPage;
```

## 비로그인일 경우 컴포넌트

```javascript
import React from 'react';

function GuestPage() {
  return <>안녕하세여 guest</>;
}
export default GuestPage;
```

### 로그인이 되었을 경우

```javascript
로그인 완료 안녕하세요 Crong
```

### 비로그인이 되었을 경우

```javascript
안녕하세요 guest
```

추가적으로 props의 값을 생략하면 `true` 가 된다.

```toc

```

<br>
<br>
