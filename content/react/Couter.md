---
emoji: ๐ฟ
title: useState๋ฅผ ์ฌ์ฉํ์ฌ ์ปดํฌ๋ํธ ์ํ๊ฐ ๊ด๋ฆฌํ๊ธฐ.
date: '2022-06-07 23:16:00'
author: Crong
tags: React
categories: React
---

# useState๋ฅผ ์ด์ฉํ์ฌ ์ปดํฌ๋ํธ ์ํ๊ฐ ๊ด๋ฆฌํ๊ธฐ.

์ปดํฌ๋ํธ๋ฅผ ๋ณด์ฌ์ค์ผ ํ๋ ๋ด์ฉ์ด ์ฌ์ฉ์ ์ธํฐ๋์์ ๋ฐ๋ผ ๋ฐ๋์ด์ผ ํ  ๋์ ์ด๋ป๊ฒ ๊ตฌํํ  ์ ์๋์ง์ ๋ํ์ฌ ์์๋ณด์. <br>
๋ฆฌ์กํธ 16.8 ์ด์  ๋ฒ์ ์์๋ ํจ์ํ ์ปดํฌ๋ํธ์์๋ ์ํ๋ฅผ ๊ด๋ฆฌํ  ์ ์์๋๋ฐ, `Hooks`๋ผ๋ ๊ธฐ๋ฅ์ด ๋์๋๋ฉด์ ํจ์ํ ์ปดํฌ๋ํธ์์๋ ์ํ๋ฅผ ๊ด๋ฆฌํ ์์๊ฒ ๋์๋ค. <br>
`useState` ๋ผ๋ ํจ์๋ฅผ ํธ์ถํ์ฌ, ๋ฒํผ์ ๋๋ฅด๋ฉด ์ซ์๊ฐ ๋ฐ๋๋ Counter ์ปดํฌ๋ํธ๋ฅผ ๋ง๋ค์ด๋ณผ๊ฒ์ด๋ค.

## Counter.jsx

```javascript
// Counter.jsx
import { useState } from 'react';

export default function Counter() {

  const Increase = () => {
    console.log('+1');
  };

  const Decrease = () => {
    console.log('-1')
  };

  return (
    <div>
      <h1>{number}</h1>
      <button onClick={Increase}>+ 1</button>
      <button onClick={Decrease}>- 1</button>
    </div>
  );
}

```

- App์ปดํฌ๋ํธ์์ Counter.jsx๋ฅผ ๋ ๋๋ง์ ํด๋ณด์.

```javascript
// App.jsx

import Counter from './components/Counter';

export default function App() {
  return (<Counter />);
}

```

<div align=center>

![img](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6353fd38-5007-4b8c-9b6a-bd38e17ad9d2/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220607%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220607T140617Z&X-Amz-Expires=86400&X-Amz-Signature=f9d82f4b31d58d9bfc08c58f5163d5bb38b79d3d752a2fdf205d4db3ab7e0432&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
</div>

์ด๋ฐ UI๊ฐ ๋ณด์ฌ์ง๋ฉด ์ฑ๊ณต์ ์ด๋ค.

<br>

```javascript
import React, { useState } from 'react';

์ด ์ฝ๋๋ ๋ฆฌ์กํธ ํจํค์ง์์ useState ๋ผ๋ ํจ์๋ฅผ ๋ถ๋ฌ์์ค๋ค.
const [number, setNumber] = useState(0);

const Increase = () => {
    setNumber(number + 1);
  };

const Decrease = () => {
    setNumber(number - 1);
  };
```

`useState` ๋ฅผ ์ฌ์ฉ ํ  ๋์๋ ์ํ์ ๊ธฐ๋ณธ๊ฐ์ ํ๋ผ๋ฏธํฐ๋ก ๋ฃ์ด์ ํธ์ถํด์ค๋ค. ์ด ํจ์๋ฅผ ํธ์ถํด์ฃผ๋ฉด ๋ฐฐ์ด์ด ๋ฐํ๋๋๋ฐ, ์ฌ๊ธฐ์ ์ฒซ๋ฒ์งธ ์์๋ ํ์ฌ ์ํ, ๋๋ฒ์งธ ์์๋ `Setter` ํจ์์ด๋ค.

```javascript
const Increase = () => {
    setNumber(number + 1);
  };

const Decrease = () => {
    setNumber(number - 1);
  };
```

`Setter` ํจ์๋ ํ๋ผ๋ฏธํฐ๋ก ์ ๋ฌ๋ฐ์ ๊ฐ์ ์ต์  ์ํ๋ก ์ค์ ํด์ค๋ค.
```javascript
<h1>{number}</h1>
```

h1ํ๊ทธ์๋ ์ด์  0์ด ์๋ `{number}` ๊ฐ์ ๋ณด์ฌ์ค์ผ ํ๋ค.

์ฝ๋๋ฅผ ๋ค ์์  ํ, ๋ฒํผ์ ๋๋ฌ๋ณด๋ฉด ์๋ก์ด ํ๋ผ๋ฏธํฐ๊ฐ์ ๋ฐ์์ค๋๊ฒ์ ๋ณผ์์๋ค.

## ์ถ๊ฐ.

### ํจ์ํ ์๋ฐ์ดํธ

```javascript
import { useState } from 'react';

export default function Counter() {
  const [number, setNumber] = useState(0);

  const Increase = () => {
    setNumber((prev) => prev + 1);
  };

  const Decrease = () => {
    setNumber((prev) => prev - 1);
  };

  return (
    <div>
      <h1>{number}</h1>
      <button onClick={Increase}>+ 1</button>
      <button onClick={Decrease}>- 1</button>
    </div>
  );
}

```

`onIncrease` ์ `onDecrease` ์์ `setNumber` ๋ฅผ ์ฌ์ฉ ํ  ๋ ๊ทธ ๋ค์ ์ํ๋ฅผ ํ๋ผ๋ฏธํฐ๋ก ๋ฃ์ด์ค๊ฒ์ด ์๋๋ผ, 
๊ฐ์ ์๋ฐ์ดํธ ํ๋ ํจ์๋ฅผ ํ๋ผ๋ฏธํฐ๋ก ๋ฃ์ด์ฃผ์๋ค.

ํจ์ํ ์๋ฐ์ดํธ๋ ์ฃผ๋ก ๋์ค์ ์ปดํฌ๋ํธ๋ฅผ ์ต์ ํ๋ฅผ ํ๊ฒ ๋  ๋ ์ฌ์ฉํ๊ฒ ๋๋ค. ์ง๊ธ ๋น์ฅ์ ํจ์ํ ์๋ฐ์ดํธ๋๊ฒ ์๋ ๊ฒ ์ ๋๋ง ์ดํดํ๋ฉด ์ถฉ๋ถํ๋ค.

```toc
```
