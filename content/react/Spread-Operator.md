---
emoji: ⏰
title: Spread Operator (스프레드 연산자)
date: '2022-05-01 17:17:00'
author: Crong
tags: React
categories: React
---

## 배열의 복제

배열을 복제하려 할때 기준 ES5 문법에서는 아래와 같이 반복문을 통해 일일이 값을 넣어줘야 한다.

```javascript
const array = [1, 2, 3, 4, 5];
const newArray = [];

for (let i = 0; i < array.length; i++) {
  newArray[i] = array[i];
}
```

위의 코드랑 로직을 ES6의 Spread Operator를 통해 간편하게 배열을 복제 할 수 있다.

```javascript
const array = [1, 2, 3, 4, 5];
const newArray = [...array];

console.log(newArray); // [1,2,3,4,5];
```

### ※ 이 배열 복제는 Reference 복사가 아니라, 값 복사로 newArray에서 변경을 해도 기존 array는 변경이 없다.

<br>

## 배열 병합

```javascript
const objA = [1, 2, 3];
const objB = [4, 5, 6];

const objC = [...objA, ...objB];

console.log(objC); // [1,2,3,4,5,6];
```

<br>

## 객체에서도 동일

```javascript
const objA = { a: 1, b: 2, c: 3 };
const objB = { ...objA };

console.log(objB); // {a: 1, b: 2, c: 3}
```

<br>

## 특정값만 변경하기

```javascript
const objA = { a: 1, b: 2, c: 3 };
const objB = { ...objA, b: 4 }; // objA 복제후, objB 속성만 덮어쓰기.

console.log(objB); // {a: 1,b: 4,c: 3};
```

위에 코드는 React에서 state 관리할때 불변성을 유지하며, 객체중 일부만 <b>Update</b>를 해야할때 쓰인다.

<br>
<br>
