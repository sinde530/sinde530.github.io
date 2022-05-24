---
emoji: 📦
title: Redux란?
date: '2022-05-24 10:22:00'
author: Crong
tags: React Redux
categories: React Redux
---

# Redux

Redux로 상태 관리를 하는 이유와 이로 인해 얻어지는 이점은 다음 같다.

- 상태 관리는 사실 리액트의 관심사가 아니다.
- App은 상태가 어떻게 처리되는지 모르게 한다.
- App은 View가 어떻게 그려지는지만 관심을 갖게 한다.
- App은 상태 관리(store)와 View를 연결만 해준다.
- App은 상태 관리 로직이 어떻게 구현됐는지는 모른다.
- 상태 관리 로직 변경의 영향이 View로 전파되지 않는다.

<br>

## Redux 설치

```javascript
npm i redux react-redux
```

```javascript
yarn add redux react-redux
```

## Redux의 3가지 원칙

[3가지의 원칙 - 리덕스 공식 문서](https://redux.js.org/understanding/thinking-in-redux/three-principles)에서는 리덕스를 사용할 때 따라야 할 3가지 원칙을 제시한다.

- 전체 상태값을 하나의 객체에 저장한다.
- 상태값은 불변 객체이다.
- 상태값은 순수 함수에 의해서만 변경되어야 한다

## Action

- [Action](https://redux.js.org/tutorials/fundamentals/part-2-concepts-data-flow)

  상태값은 오직 액션 객체에 의해서만 변경되어야 한다.

- type: (string)
- payload(object): {taskTitle}

액션 객체에는 type,payload 속성으로 구성되는데 type은 어떤 액션인지 구별할 수 있는 문자열 값이며 payload 안에는 변경할 상태값(불변 객체)가 전달된다. Redux에서 상태값을 수정하는 유일한 방법은 액션 객체와 함게 dispatch 메소드를 호출하는 거다.

## Reducer

- [Reducers](https://redux.js.org/tutorials/fundamentals/part-3-state-actions-reducers)

리덕스에선 기존 상태를 다른 상태로 변경하는 함수를 리듀서(reducer)라고 한다. reducer의 구조는 다음과 같다.

```javascript
function reducer(state, action) {
  // ...

  return state;
}
```

reducer는 이전 상태값과 액션 객체를 입력으로 받아서 새로운 상태값을 만드는 순수함수이다. 순수 함수는 부수 효과(함수 외부의 상태를 변경시키는 것)를 발생시키지 않아야 한다.

## Store

- [Store](https://redux.js.org/tutorials/fundamentals/part-4-store)

store는 리덕스의 `상태값`을 갖는 객체이다. 액션의 발생은 store의 dispatch 메소드로 시작된다. 스토어는 액션이 발생하면 미들웨어 함수를 실행하고, reducer를 싱행해서 상태값을 새로운 값으로 변경한다. 첫 번째 원칙에서 말한 애플리케이션의 전체 상태값을 저장하고 하나의 객체가 바로 store이다.

## Provider

- [Provider](https://react-redux.js.org/api/provider)

React로 작성된 컴포넌트들을 Provier안에 넣으면 하위 컴포넌트들이 Provider를 통해 redux store에 접근이 가능해진다.

## react-redux hook

- [Hooks](https://react-redux.js.org/api/hooks#usedispatch)

Hook 등장 이전에는 `mapDispatchToProps`, `mapStateToProps`와 `connect` 라는 함수를 이용해서 많은 코드를 작성해야 했으나 Redux에서도 Hook을 제공하면서 상당히 깔끔한 코드를 작성할 수 있다. Redux Hook중 가장 중요한 Hook은 useDispatch 와 useSelector이 있다.

## React에서 Redux 사용하기

- [Usage With React](https://redux.js.org/tutorials/fundamentals/part-5-ui-react)

```toc

```
