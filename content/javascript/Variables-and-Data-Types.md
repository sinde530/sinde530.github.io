---
emoji: 🪴
title: 변수와 자료형이란?
date: '2022-05-10 14:56:00'
author: Crong
tags: Javascript
categories: Javascript
---

## 1)자료형

내부적으로는 Primitive(기본형)과 Object(객체형)이 있으며 각각 다음과 같다.
<br>

Primitive

- Reference 타입
- 클래스 뿐만 아니라, 배열과 함수, 사용자 정의 클래스도 모두 Object.
- JSON(Java Script Object Notation)의 기본 구조.

<br>

## 2)변수 선언

- 변수이름은 대소문자를 구별한다.
- 여러 변수를 한번에 선언할 수 있음.
- 지역변수와 전역변수가 있음.
- 기본적으로 소문자로 시작되는 Camel Case 를 사용.

```javascript
var newMembers;
newMembers = 'Jone';
```

<br>

### var, let, const

> ES6 이전에는 `var`만 존재했으며 function-scoped 로 인해 다른 언들과 다른 문제가 있었음.

- `var`는 지역변수 개념으로 함수 범위에서 유효함.
- `var`를 선언하지 않으면 자동으로 전역변수가 됨.
- `let`과 `const`는 ES6 에서 등장한 block-sceoped 변수 선언.
- `let`은 값의 재할당이 가능하고 `const` 는 불가능(immutable).
- `const`로 선언된 배열이나 객체의 경우 새로운 객체로 재할당하는 것은 안되고, 배열값의 변경/추가, 객체의 필드 변경등은 가능.

var 를 이용한 변수선언 예시)

```javascript
var foo = 'foo1';
console.log(foo); // foo

if (true) {
  var foo = 'foo2';
  console.log(foo); // foo2
}

console.log(foo); // foo2
```

let과 const의 예시)

```javascript
let foo = 'foo1';
const bar = 'bar1';
console.log(foo); // foo1

if (true) {
  let foo = 'foo2';
  console.log(foo); // foo2
  console.log(bar); // bar1
}

console.log(foo); // foo1
bar = 'bar2'; // error
```

```toc

```

## hoisting

> 호이스팅은 끌어올리기라는 사전전 의미를 가지고 있으며, 자바스크립트에서 모든 변수 선언은 호이스트 되고 함수의 경우 선언형식은 호이스팅 되며 변수에 할당된 형태의 호이스팅 되지 않습니다.

```javascript
if (true) {
  console.log(foo); // undefined
  var foo = 'foo11';
  console.log(foo); // foo11
}
```

- 일반적인 언어인 경우 `foo` 변수는 첫번째 출력문에서 선언되기 전 상태로 에러가 발생해야 함.
- 자바스크립트는 `var foo` 가 호이스트 되어 변수는 선언되고 값이 할당되지 않은 상태가 됨.

```javascript
var myVar;
function myVar(){
    ...
}
console.log(typeof myVar);
```

- 위 예제에서는 myVar 라는 변수를 먼저 선언한 상태에서 동일 이름의 함수를 정의.
- 함수 선언이 호이스팅 되어 myVar 변수에 할당.

> 경우에 따라 호이스팅은 사소한 문제를 일으키지 않아 유용할수 있으나 복잡한 코드에서나 오류 가능성이 높으므로 변수 선언시에는 var,let,const 등을 명확히 구분해서 사용하는 것이 좋다.

### String 변수

일반적인 프로그램언어들은 문자열을 표현할때 `큰따옴표("")`를 사용하는데 반해 자바스크립트는 `"",''`를 모두 사용할 수 있다.

```javascript
var string;
string = 'java Script'; // 혹은 'Java Script'
```

```toc

```

<br>
<br>
