---
emoji: 🍥
title: 함수형 컴포넌트의 차이점
date: '2022-05-12 14:08:00'
author: Crong
tags: React
categories: React
---

## 함수형 컴포넌트의 차이점

```javascript
// 아래 function들은 원래 이 파일 내에서만 사용할 수 있음.
function Something() {}

function Anything() {}

// 위 function을 아래처럼 export 시키면 다른 파일에서 해당 function을 가져와 쓸 수 있음.
export { Something, Anything };

// 다른 파일에서 위 function을 불러오려면 아래 명령어 사용
import { Something } from '파일명';
import { Anything } from '파일명';
//혹은
import { Something, Anything } from '파일명';

// function을 이 default로 export해서 다음처럼 쓸 수 있음
// 해당 파일에서 export되는게 해당 function 하나 뿐이거나 가장 주요한 function을 default로 내보내는 편
function DefaultFunc() {}
export default DefaultFunc;
//혹은
export default function DefaultFunc() {}

// 불러올때는
import DefaultFunc from '파일명';

// default로 export된 function과 아닌 function은 아래처럼 병기
export default function MajorFunc() {}
function MinorFunc() {}
export { MinorFunc };

// 불러올 때
import MajorFunc, { MinorFunc } from '파일명';
```

```toc

```

<br>
<br>
