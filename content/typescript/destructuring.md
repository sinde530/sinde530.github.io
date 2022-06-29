---
emoji: 🎐
title: TypeScript - 비구조화 할당(Destructuring)
date: '2022-06-20 09:39:00'
author: Crong
tags: TypeScript Destructuring
categories: TypeScript Javascript
---

![./typescript-logo.png](typescript-logo.png)

<br>

# Destructuring
- 비구조화 할당
```typescript
const Object = {
    name: 'Crong',
    age: 22,
    genger: 'male'
}
```

- 위의 객체에서 `name`, `age`, `gender`를 각각 분리해서 사용하고자 할 때 `destructuring`을 사용한다.

## JavaScript에서의 Destructuring
```javascript
const { name, age, gender } = Object;
```

## TypeScript에서의 Destructuring

### 잘못된 방법
```typescript
const { name: string, age: number, gender: string } = Object;
```

- 단순히 생각해서 이런 식으로 타입을 지정해주면 되지 않을까 싶었음
- 이렇게 할 경우 name, age, gender를 각각 string,number,string으로 명명하라는 코드가 됨.

### 쉬운 방법
```typescript
const { name, age, gender}: { name: string. age: number, gender: string } = Object;
```

- `{}`로 감싸진 전체에 대해서 타입을 지정해야 됨

### 권장하는 방법
```typescript
interface Props {
    name: string,
    age: number,
    gender: string
}

const { name, age, gender }: Props = Object;
```

- interface로 미리 타입을 정의하고 해당 interface를 타입으로 지정하는 방식이 있다.

<br>
<br>

```toc
```