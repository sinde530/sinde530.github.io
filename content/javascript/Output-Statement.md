---
emoji: 🍪
title: 출력문 이란?
date: '2022-05-10 15:37:00'
author: Crong
tags: Javascript
categories: Javascript
---

## 3) 출력문

자바스크립트는 HTML 문서를 통해 웹브라우저에서 출력되므로 따로 출력문이 존재한다기 보다는 HTML 문서의 구성요소에 동적으로 출력하거나 웹브라우저의 경고창을 이용해 출력하는 형태가 출력문으로 볼 수 있다.

### HTML 문서에 출력

> HTML 문서에 출력하는 형태로 페이지가 모두 로딩된 다음에 실행하면 원래 있던 HTML 화면내용은 지워지게 된다.

밑에 코드는 연산결과를 웹브라우저에 출력하는 코드이다.

```html
<script>
  document.write(5 + 6);
</script>

<body>
  <h2>Hello World!</h2>
</body>
```

<br>

### HTML 문서의 특정부분에 출력

> HTML 문서의 특정요소를 찾아 해당 콘텐츠를 대체해 출력한다. 자바스크립트에서 가장 보편적으로 HTML 문서를 동적으로 핸들링하는 방법이다.

다음 예제는 앞의 예제와 비슷하지만 기존 HTML 소스를 유지하고 부분적으로 변경 된다.

```html
<script>
  document.getElementById('result').innerHTML = 5 + 6;
</script>

<body>
  <h2>Hello World!</h2>
  <div id="result"></div>
</body>
```

<br>

### Alert 창을 이용한 출력

> 웹브라우저에서 오픈되는 조그만 경고창(alert)를 이용한 출력이다. 보통 프로그램에서 에러, 경고, 사용자 입력을 위해 많이 사용한다.

```html
<script>
  alert(5 + 6);
</script>
```

<br>

### 브라우저 콘솔창을 이용한 출력

> 자바스크립트 코드에서 진행상황을 출력하거나 개발을 위해 참고하기 위한 값들을 출력하기 위한 용도로 사용한다.

보통 프로그램언어의 출력문과 가장 비슷한 경우 이다. console.log()를 사용하며 결과 확인은 웹브라우저의 콘솔창에 나타나게 된다.

```html
<script>
  console.log(5 + 6);
</script>
```

```toc

```

<br>
<br>
