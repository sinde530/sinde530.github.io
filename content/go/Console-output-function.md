---
emoji: 🍪
title: 콘솔 출력이 무엇?
date: '2023-04-26 12:34:00'
author: Kim Sung Eun
tags: Go
categories: Go
---

## 콘솔 출력 함수에 대해 알아보자.

Go언어에서 사용하는 fmt package의 **Console output function**은 매우 많은 방법이 있지만, 그중에서 제일 유용하게 쓰이는 3가지를 알아볼 것 예정입니다.

이 문서는 Print, Println, Printf 함수들이 어떤 특징이 있는지 차이점을 중점으로 설명하겠습니다.

`import “fmt”`

---

코드 상단에 `import “fmt”`를 선언함으로써 `fmt` **package**를 사용할 수 있는데, 이는 C언어의 입/출력 함수인 **printf**와 **scanf** 함수같은 유사한 함수들을 형식화된 **입/출력 함수**를 사용할 수 있다는 뜻입니다.

쉽게 말해, Console에 입력 함수와 콘솔 출력함수를 사용하기 위해서는 무조건 **fmt package**를 **import**해야합니다.

<br>

### Print

**Print** 함수는 개행을 하지 않기 때문에 문자열 **“”** 혹은 **Back Quote** 내에서 **escape sequence**인 ‘**\n**’을 입력해 개행해야한다.

밑에 코드는 연산결과를 웹브라우저에 출력하는 코드이다.

```go
package main

import (
	"fmt"
)

func main() {
	var number int = 2023

	fmt.Print("가나다 \n")
	fmt.Print("라마바 \n")
	fmt.Print("사아자 \n")
	fmt.Print("현재 년도는", number, "년 이다.")
}

## result
가나다
라마바
사아자
현재 년도는2023년 이다.
```

<br>

### Println

Println 함수는 사용할 때마다 자동으로 개행이 되어서 출력이 가능합니다.
하나의 인자를 출력할 수도 있고, 여러 개의 인자를 콤마로 결합해 열거할 수 있다는 점이 있습니다.

```go
package main

import (
	"fmt"
)

func main() {
	var number int = 2023

	fmt.Println("가나다")
	fmt.Println("라마바")
	fmt.Println("사아자")
	fmt.Println("현재 년도는", number, "년 이다.")
}

## result
가나다
라마바
사아자
현재 년도는 2023 년 이다.
```

<br>

### Printf

Printf 함수는 C언어의 Printf 함수와 유사하다. Go언어에서도 개발자가 format을 지정하여, 원하는 형태로 출력할 때 사용됩니다.

주의해야 할 점은 반드시 format을 지정해야 한다는 것 이다. 예를 들어 n := 5일때 fmt.Printf(n)을 입력해 출력할 수는 없다. 한 개의 인자라도 출력하기 위해서는fmt.Printf(”%d”, n)형식으로 입력해야 합니다.

C언어 좀 더 편리한 점은, Array를 한번에 출력이 가능합니다.

예를 들어보면, int arr[3] = {1, 2, 3}일때 printf(”%d”, arr)이 불가능하고,

Go언어에서는 var arr [3]int = [3]int{1, 2, 3}일때, fmt.Printf(”%d”, arr)이 가능합니다.

마지막으로. Print 함수와 동일하게 자동 개행이 되지않아, 개행을 하려면 “\n”을 입력해야합니다.

%d는 10진수 정수의 형태로 출력한다는 의미이며, %X는 데이터를 16진수로 출력하되, 알파벳은 대문자로 출력한다는 의미. 이를 서식문자라고 합니다.

```go
package main

import (
	"fmt"
)

func main() {
	var number int = 2023

	fmt.Printf("가나다 \n")
	fmt.Printf("라마바 \n")
	fmt.Printf("사아자 \n")
	fmt.Printf("현재 년도는 %d년 이다.", number)
}

## result
가나다
라마바
사아자
현재 년도는 2023년 이다.
```

<br>

```toc

```

<br>
<br>
