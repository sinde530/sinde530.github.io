---
emoji: ๐ฅ
title: ํจ์ํ ์ปดํฌ๋ํธ์ ์ฐจ์ด์ 
date: '2022-05-12 14:08:00'
author: Crong
tags: React
categories: React
---

## ํจ์ํ ์ปดํฌ๋ํธ์ ์ฐจ์ด์ 

```javascript
// ์๋ function๋ค์ ์๋ ์ด ํ์ผ ๋ด์์๋ง ์ฌ์ฉํ  ์ ์์.
function Something() {}

function Anything() {}

// ์ function์ ์๋์ฒ๋ผ export ์ํค๋ฉด ๋ค๋ฅธ ํ์ผ์์ ํด๋น function์ ๊ฐ์ ธ์ ์ธ ์ ์์.
export { Something, Anything };

// ๋ค๋ฅธ ํ์ผ์์ ์ function์ ๋ถ๋ฌ์ค๋ ค๋ฉด ์๋ ๋ช๋ น์ด ์ฌ์ฉ
import { Something } from 'ํ์ผ๋ช';
import { Anything } from 'ํ์ผ๋ช';
//ํน์
import { Something, Anything } from 'ํ์ผ๋ช';

// function์ ์ด default๋ก exportํด์ ๋ค์์ฒ๋ผ ์ธ ์ ์์
// ํด๋น ํ์ผ์์ export๋๋๊ฒ ํด๋น function ํ๋ ๋ฟ์ด๊ฑฐ๋ ๊ฐ์ฅ ์ฃผ์ํ function์ default๋ก ๋ด๋ณด๋ด๋ ํธ
function DefaultFunc() {}
export default DefaultFunc;
//ํน์
export default function DefaultFunc() {}

// ๋ถ๋ฌ์ฌ๋๋
import DefaultFunc from 'ํ์ผ๋ช';

// default๋ก export๋ function๊ณผ ์๋ function์ ์๋์ฒ๋ผ ๋ณ๊ธฐ
export default function MajorFunc() {}
function MinorFunc() {}
export { MinorFunc };

// ๋ถ๋ฌ์ฌ ๋
import MajorFunc, { MinorFunc } from 'ํ์ผ๋ช';
```

```toc

```

<br>
<br>
