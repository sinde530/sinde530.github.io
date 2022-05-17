---
emoji: 📫
title: jest 사용해보기
date: '2022-05-17 14:57:00'
author: Crong
tags: Jest, React, javascript,
categories: Jest, React,
---

## Testing 이란 무엇인가

`소프트웨어 테스트` 를 말한다.

제품이 예상하는 대로 동작 하는지 확인하는것.

## 테스트 피라미드

> E2E Test = UI 테스트,사용자 테스트
> Integration Test = 통합 테스트(모듈들,클래스들)
> Unit Test = 단위 테스트(함수,모듈,클래스)

## TDD

TDD(Test-driven development ( 테스트 주도 개발 )
개발(코드 작성)전 테스트 코드를 먼저 작성

### TDD를 작성해야 하는 이유

- 구현 < 인터페이스 => 코드의 퀄리티 향상
- 사용자 입장에서 코드를 작성
- 모든 요구 사항(목표)에 대해 점검
- 시스템 전반적인 설계 향상
- 개발 집중력 향상

## Jest 알아보기

[JEST 공식문서](https://jestjs.io/)

자바스크립트 환경에서 테스팅을 할수있는 프레임워크이다.
테스팅 라이브러리중에서 가장 간편하고 심플한 라이브러리라고 할수있음.
바벨을 이용하거나 타입스크립트,앵귤러,뷰 UI프레임워크에서도 사용이 가능.

## JEST 필요한 용어

expect : expect 기능은 값을 테스트할때 주로 쓰인다
toBe : 정확하게 이 값이여야한다.
it = 3인칭 주어라 볼수있음
beforeEach = 각각 테스트코드들이 실행하기 전에 실행됨
afterEach = 함수가 수행이 된다음에 호출이 됨.

```toc

```
