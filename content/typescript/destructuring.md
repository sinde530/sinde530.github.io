---
emoji: ๐
title: TypeScript - ๋น๊ตฌ์กฐํ ํ ๋น(Destructuring)
date: '2022-06-20 09:39:00'
author: Crong
tags: TypeScript Destructuring
categories: TypeScript Javascript
---

![./typescript-logo.png](typescript-logo.png)

<br>

# Destructuring
- ๋น๊ตฌ์กฐํ ํ ๋น
```typescript
const Object = {
    name: 'Crong',
    age: 22,
    genger: 'male'
}
```

- ์์ ๊ฐ์ฒด์์ `name`, `age`, `gender`๋ฅผ ๊ฐ๊ฐ ๋ถ๋ฆฌํด์ ์ฌ์ฉํ๊ณ ์ ํ  ๋ `destructuring`์ ์ฌ์ฉํ๋ค.

## JavaScript์์์ Destructuring
```javascript
const { name, age, gender } = Object;
```

## TypeScript์์์ Destructuring

### ์๋ชป๋ ๋ฐฉ๋ฒ
```typescript
const { name: string, age: number, gender: string } = Object;
```

- ๋จ์ํ ์๊ฐํด์ ์ด๋ฐ ์์ผ๋ก ํ์์ ์ง์ ํด์ฃผ๋ฉด ๋์ง ์์๊น ์ถ์์
- ์ด๋ ๊ฒ ํ  ๊ฒฝ์ฐ name, age, gender๋ฅผ ๊ฐ๊ฐ string,number,string์ผ๋ก ๋ช๋ชํ๋ผ๋ ์ฝ๋๊ฐ ๋จ.

### ์ฌ์ด ๋ฐฉ๋ฒ
```typescript
const { name, age, gender}: { name: string. age: number, gender: string } = Object;
```

- `{}`๋ก ๊ฐ์ธ์ง ์ ์ฒด์ ๋ํด์ ํ์์ ์ง์ ํด์ผ ๋จ

### ๊ถ์ฅํ๋ ๋ฐฉ๋ฒ
```typescript
interface Props {
    name: string,
    age: number,
    gender: string
}

const { name, age, gender }: Props = Object;
```

- interface๋ก ๋ฏธ๋ฆฌ ํ์์ ์ ์ํ๊ณ  ํด๋น interface๋ฅผ ํ์์ผ๋ก ์ง์ ํ๋ ๋ฐฉ์์ด ์๋ค.

<br>
<br>

```toc
```