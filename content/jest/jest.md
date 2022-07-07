---
emoji: 🍹
title: jest
date: '2022-07-07 09:59:00'
author: Crong
tags: Jest React TypeScript
categories: Jest React TypeScript
---

## JEST

---

- 페이스북 팀에서 Jasmine 기반으로 만든 테스팅 프레임 워크이다. C-R-A로 만든 리액트 프로젝트에는 자동으로 적용이 되어있다.

---

## react-testing-library

- Enzyme과 달리 모든 테스트를 DOM 위주로 진행하며, 컴포넌트의 props나 state를 조회하는 일은 없다. (컴포넌트를 리팩토링 하게 될 때에는 주로 내부 구조 및 네이밍은 많이 바뀔 수 있어도 실제 작동 방식은 크게 바뀌지 않는다. 이점을 중요시 여겨 컴포넌트의 기능이 똑같이 작동한다면 컴포넌트의 내부 구현 방식이 많이 바뀌어도 테스트가 실패하지 않도록 설계)
- 즉, react-testing-library는 구현 (Enzyme)에 중점을 둔 테스트보다는 사용자 행동 (react-testing-library)에 중점을 둔다.
- 2019.09.04일 기준 라이브러리가 바뀌었다. 아래의 명령어로 설치.
    
      `yarn add @testing-library/react @testing-library/jest-dom @types/jest`
    
- `setupTests.js`의 내용을 아래의 코드로 변경

  ```typescript
  import "@testing-library/react";
  import "@testing-library/jest-dom/extend-expect";
  ```
    
- 해당 `render`에 의구심이 있었는데, 보니까 벨로퍼트의 글에 잘 나와있더라.
    
    > react-testing-library 에서는 리액트에서는 DOM 시뮬레이션을 위한 JSDOM 이라는 도구를 사용하여 document.body 에 리액트 컴포넌트를 렌더링합니다. clean-up-after-each 를 불러오면, 각 테스트 케이스가 끝날때마다 기존에 가상의 화면에 남아있는 UI 를 정리합니다.
    > 

추가적으로, 그 아래에는 jest-dom/extend-expect 를 불러와서 jest 에서 DOM 관련 matcher 를 사용 할 수 있게 해주었습니다.

---

### 사용하는 함수

`it`

- 새로운 테스트 케이스를 만드는 함수이다.

`expect`

- it 내부에서 해당 함수를 통하여 특정 값이 우리가 예상한 값이 나왔는지 확인 할 수 있다.

`describe`

- 여러개의 `it`을 넣기 위함이다. `describe`안에는 또 여러개의 `describe`를 넣을 수 있다.

`render`

- 이 함수가 호출되면 그 결과물에는 DOM을 선택 할 수 있는 다양한 쿼리들과 `container`가 포함되어 있다. 여기서 `container`는 해당 컴포넌트의 최상위 `DOM`을 가르키며, 이를 가지고 스냅샷 테스팅을 할 수 도 있다.

---

### 사용하는 쿼리 함수

### Variant

`getBy*`

- 조건에 일치하는 DOM 엘리먼트 하나를 선택. 존재하지 않으면 에러.

`getAllBy*`

- 조건에 일치하는 DOM 엘리먼트 여러개를 선택. 존재하지 않으면 에러.

`queryBy*`

- 조건에 일치하는 DOM 엘리먼트 하나를 선택. 존재하지 않아도 에러 X.

`queryAllBy*`

- 조건에 일치하는 DOM 엘리먼트 여러개를 선택. 존재하지 않아도 에러 X.

`findBy*`

- 조건에 일치하는 DOM 엘리먼트 하나가 나타날 때까지 기다렸다가 해당 `DOM`을 선택하는 `Promise` 반환. (기본 Timeout 조건인 4500ms 이후에도 나타나지 않으면 에러 발생)

`findAllBy*`

- 조건에 일치하는 DOM 엘리먼트 여러개가 나타날 때까지 기다렸다가 해당 `DOM`을 선택하는 `Promise` 반환. (기본 Timeout 조건인 4500ms 이후에도 나타나지 않으면 에러 발생)

### Queries

`ByLabelText`

- label이 있는 input의 label 내용으로 input 선택.

    ```typescript
    <label for="username-input">아이디</label>
    <input id="username-input" />const inputNode = getByLabelText('아이디');
    ```
<br>    


`ByPlaceholderText`

- placeholder 값으로 input 및 textarea를 선택.

    ```typescript
    <input placeholder="아이디" />;
        
    const inputNode = getByPlaceholderText('아이디');
    ```

<br>

`ByText`

- 엘리먼트가 가지고 있는 텍스트 값으로 DOM 선택

```typescript
<div>Hello World!</div>;
    
const div = getByText('Hello World!');
```
    
- 참고로 텍스트 값에 정규식을 넣어도 작동한다.

```typescript
const div = getByText(/^Hello/);
``` 

<br>

`ByAltText`

- `alt` 속성을 가지고 있는 엘리먼트(주로 `img`)를 선택.

    ```typescript
    <img src="/awesome.png" alt="awesome image" />;
    const imgAwesome = getByAltText('awesome image');
    ``` 

<br>

`ByTitle`

- `title` 속성을 가지고 있는 DOM 혹은 `title` 엘리먼트를 지니고 있는 SVG를 선택할 때 사용.
    
    > title 속성은 html에서 툴팁을 보여줘야 하는 상황에 사용하곤 한다.

    ```typescript
    <p><span title = "React">리액트</span>는 짱 멋진 라이브러리다.
    </p>

    <svg><title>Delete/title>
        <g><path /></g>
    </svg>

    const spanReact = getByTitle('React');
    const svgDelete = getByTitle('Delete');
    ```

<br>

`ByDisplayValue`

- `input`, `textarea`, `select`가 지니고 있는 현재 값을 가지고 엘리먼트를 선택

```typescript
<input value = "text" />const input = getByDisplayValue('text');
```

<br>

`ByRole`

- 특정 `role`값을 지니고 있는 엘리먼트를 선택.

```typescript
<span role="button">삭제</span>;

const spanRemove = getByRole('button');
```
- `role`이란?
    - `WAI-ARIA`와 관련이 생기는데, 그전에 `RIA`의 개념을 잡고 가야한다.(참고한 웹사이트 : [WAI_ARIA](https://www.biew.co.kr/36))
    
    ---
    
    - `RIA(Rich Internet Applications)`란?
        - 정적인 HTML과 단순한 자바스크립트 환경의 웹이 아닌 동적인 자바스크립트와 Ajax와 같은 기술을 사용한 환경에서 수준 높은 UX(User eXperience)를 제공하는 웹 어플리케이션
        - [단점]
            - 화려하고 편리한 웹 애플리케이션이지만 스크린 리더와 같은 보조 기술을 사용하는 장애인들이 접근하기에 취약.
            - 자바 스크립트, AJAX 등을 활용하여 의미를 가지지 않는 요소(<div>, <span>)로 특정 컴포넌트를 구현할 때 스크린 리더 등 보조기기에서 해당 컴포넌트의 기능을 명확하게 파악하기 어려움.
            - 주식 시세나 RSS Feed 등 정보가 자동으로 업데이트 되는 경우 스크린리더 등 보조기기에서 업데이트 된 정보를 파악하기 어려움.
    - 때문에 `WAI-ARIA`는 `RIA`에서 스크린 리더 및 보조기기 등에서 접근성 및 상호 운용성을 향사시키기 위한 목적으로 탄생 했으며, 웹 어플리케이션에 역할(Role), 속성(Property), 상태(State) 정보를 추가하여 이를 개선할 수 있도록 제공.
    
    ---
    
    - 결국 `role`이란 유저 인터페이스(UI)에 포함된 특정 컴포넌트의 역할을 정의한다. (Abstract Roles, Widget Roles, Document Structure Roles, Landmark Roles로 분류)
    - [예시]
        - 탭 목록(tablist)과 본문(tabpanel)이 따로 나뉘어져 있는 마크업 구조는 스크린 리더 등 보조기기를 사용하는 사용자에게는 정보 접근이 어려울 수 있다. 이때 Tab 관련 Widget Role을 사용하면 보조기기를 사용하는 사용자에게 보다 정확한 정보를 제공할 수 있다.
            
            [https://t1.daumcdn.net/cfile/tistory/992852365B727A0124](https://t1.daumcdn.net/cfile/tistory/992852365B727A0124)
            
            *<!--tablist를 사용한 탭메뉴 예시 -->*<div class="tab_wrap">
                *<!-- 탭메뉴 --><!-- role="tablist"을 사용하여 탭메뉴 역할 부여 -->*<ul role="tablist" class="list_tab">
                    *<!-- 
                        1. role="tab"을 사용하여 탭메뉴의 탭요소 역할 부여
                        2. aria-controls="{ID}"를 사용하여 해당 탭의 본문과 연결
                        3. aria-seleceted="{boolen}"를 사용하여 해당 탭이 선택유무 명시
                        4. 초점을 받지 못하는 li요소에 tabindex="0"을 사용하여 초점을 받게함
                    -->*<li role="tab" tabindex="0" aria-selected="ture" aria-controls="section1" id="tab1">
                        탭메뉴1
                    </li>
                    <li role="tab" tabindex="0" aria-selected="false" aria-controls="section2" id="tab2">
                        탭메뉴2
                    </li>
                    <li role="tab" tabindex="0" aria-selected="false" aria-controls="section3" id="tab3">
                        탭메뉴3
                    </li>
                </ul>
                    
                *<!-- 탭메뉴 본문 -->*<div class="tab_content">
                    *<!--
                        1. role="tabpanel"을 사용하여 탭메뉴의 본문 역할 부여
                        2. aria-labelledby="{ID}을 사용하여 탭메뉴와 본문 연결"
                    -->*<section role="tabpanel" id="section1" aria-labelledby="tab1">
                        탭메뉴1의 본문
                    </section>
                    <section role="tabpanel" id="section2" aria-labelledby="tab2">
                        탭메뉴2의 본문
                    </section>
                    <section role="tabpanel" id="section3" aria-labelledby="tab3">
                        탭메뉴3의 본문
                    </section>                              
                </div>
            </div>
            
<br>

`ByTextId`

- 다른 방식으로 해당 엘리먼트를 선택하지 못할때 사용하는 방식. 특정 DOM에 직접 test할때 사용할 id를 달아서 선택하는 것을 의미.

```typescript
<div data-testid = "commondiv">흔한 div</div>;
    
const commonDiv = getByTestId('commondiv');
```
    
    - 주의할 점
        - 값을 설정할 때 `data-testid = "..."`의 포맷으로만 설정해야 한다. 추가적으로 `ByTestId`는 다른 방법으로 선택할 수 없을 때에만 사용하자!
        - DOM의 `querySelector`를 사용할 수도 있으나, 이는 지양해야 한다. 차라리 `data-testid`를 설정하는 것이 좋다.
- 어떤 쿼리를 사용해야하지?
    - 위에 적어놓은 순서가 사용 우선 순위 순서이다.

<br>

### Event

`fireEvent()`

- 해당 함수는 이벤트를 발생시켜 준다.
- [사용법]
    
      `fireEvent.이벤트이름(DOM, 이벤트객체);`
    
    - 클릭 이벤트의 경우엔 이벤트 객체를 따로 넣어주지 않아도 되지만, change 이벤트 경우엔 다음과 같이 해주어야 한다.
        
          `fireEvent.change(myInput, { target: { value: 'hello world' } });`
        

---

### DOM 함수

`toHaveAttribute`

- 해당 DOM에 특정 속성이 있는지 확인해준다.
    
      `const { getByPlaceholderText } = render(<TodoForm />);
      const input = getByPlaceholderText('할 일을 입력하세요');
     
      fireEvent.change(input, {
          target: {
              value: 'TDD 배우기'
          }
          });
      expect(input).toHaveAttribute('value', 'TDD 배우기');`
    

`jest.fn()`

- jest에서 제공하는 `mock 함수`이다. 이 함수를 사용하면 이 함수가 호출 된 다음 `toBeCalled` 또는 `toBeCalledWith`같은 matcher를 사용해서 함수가 호출 됐는지, 호출 됐다면 어떤 파라미터로 호출 됐는지 등을 쉽게 확인 가능.

`toBeTruthy`

- 내부 구성 :
    
      `function toBeTruthy() {return {compare: function(actual) {return {pass: !!actual
          };}};}`
    
    - 이부분에서 `!!`가 무엇이냐에 대한 궁금증 해소 예시
        
          `> !!"hello"
          true
          > !!""
          false
          > !![1, 2, 3]
          true
          > !![] 
          true`
        
        배열이 비어있던지 아니던지, 배열 객체는 존재하고 있기때문에 `truthy` 값은 `true`로 나온다.
        

`toHaveStyle`

- 해당 machers는 해당 DOM에 특정 스타일이 있는지 확인 가능.
- 해당 함수 앞에 `not`을 사용하는 것은 특정 조건이 만족하지 않아야 함을 의미.
    
      `expect(span).not.toHaveStyle('text-decoration: line-through;');`
    

`toBeCalledWith`

- 해당 `mock` 함수가 해당 파라미터로 제대로 호출 됐는지 확인.

`nextSibling`

- 같은 모체속에 있는 다음 형제 노드 정보를 가져온다. 대신 `nextElementSibling`은 엘리먼트만 가져오지만, 해당 프로퍼티는 엘리먼트뿐만 아니라 텍스트 노드 정보도 가져온다.

`toBeInTheDocument()`

- 특정 엘리먼트가 화면에서 사라졌는지 확인. [사용 예제]
    
      `expect(todoText).not.toBeInTheDocument(); *// 페이지에서 사라졌음을 의미함*`
    
    - 이를 사용하지 않는다면 아래와 같이 구현 가능하다.
        
          `const removedText = queryByText('TDD 배우기');
          expect(removedText).toBeNull();`
        

`React.memo`

- 기본적으로 `HOC`이다. Shallow Compare를 통해 props 값에 변화가 있을 때만 리렌더링 한다. [사용예제]
    
      `export default React.memo(TodoItem);`
    
- 중요 : 이 방법은 성능 최적화 방법으로만 존재해야 한다. 즉 `shouldComponentUpdate` 대용으로 사용하지 못한다!

---

### Async Utilities

`wait`

`function wait(callback?: () => void,options?: {timeout?: number
    interval?: number
  }): Promise<void>`

- 특정 콜백에서 에러를 발생하지 않을 때 까지 대기할 수 있다.
- 콜백 안의 함수가 에러가 발생하지 않을 때 까지 기다리다가, 대기시간이 timeout이 되면 테스트 케이스가 실패된다. timeout은 기본값 4500ms 이며, 아래와 같이 커스텀이 가능하다.
    
    *`// 콜백 안의 함수가 에러를 발생시키지 않을 때 까지 기다림*await wait(() => getByText('야호!!'), { timeout: 3000 });`
    

`waitForElement`

`function waitForElement<T>(callback: () => T,options?: {container?: HTMLElementtimeout?: number
    mutationObserverOptions?: MutationObserverInit}): Promise<T>`

- 특정 엘리먼트가 나타났거나, 바뀌었거나, 사라질때까지 대기를 해준다. 그리고 `Promise`가 끝날 때 우리가 선택한 엘리먼트를 `resolve` 한다.

`waitForDomChange`

`function waitForDomChange<T>(options?: {
  container?: HTMLElement
  timeout?: number
  mutationObserverOptions?: MutationObserverInit
}): Promise<T>`

- 콜백 함수가 아니라 검사하고 싶은 엘리먼트를 넣어주면 해당 엘리먼트에서 변화가 발생 할 때까지 기다려 준다.
- `render`를 했을때 결과 값에 있는 `container`를 넣어주면, 사전에 쿼리를 통해 엘리먼트를 선택하지 않아도 변화가 발생했음을 알 수 있다. 또한, `Promise`가 `resolve` 됐을 땐 `mutationList`를 반환하여 DOM이 어떻게 바뀌었는지에 대한 정보를 알 수 있다.

`waitForElementToBeRemove`

`function waitForElementToBeRemoved<T>(callback: () => T,options?: {container?: HTMLElementtimeout?: number
    mutationObserverOptions?: MutationObserverInit}): Promise<T>`

- 특정 엘리먼트가 화면에서 사라질 때까지 기다리는 함수

---

### REST API 테스트

- REST API를 호출해야 하는 컴포넌트의 경우, 테스트 코드에서도 똑같이 요청을 보낼 수 있지만, 일반적으로 서버에 API를 직접 호출하지 않고 이를 mocking 한다. (서버의 API가 실제로 작동하고 안하고는 서버쪽의 일이기 때문)
- `node_modules를 mocking`하는 방법과 `axios-mock-adapter`라는 라이브러리를 쓰는 두가지 방법이 있는데, 본인은 `axios-mock-adapter`를 사용했다.
    
    `yarn add axios-mock-adapter`
    

---

### axios-mock-adapter 활용방법

`MockAdapter`

- 특정 API 요청이 발생했을 때 어떤 응답이 와야 하는지 직접 정의 해 줄 수 있다. (컴포넌트 내부에서 API 요청이 발생하게 될 때, 실제로 서버로 요청이 날아가지 않고, 우리가 정의한 가짜 응답을 사용하게 됨.)
- `delayResponse` 옵션을 설정하면 딜레이를 임의적으로 설정 할 수 있다.
1. 한번만 mocking 하기 - `replyOnce`
    
     `mock.onGet('/users').replyOnce(200, users);`
    
    요청을 딱 한번만 moking하며, 한번 요청을 하고 난 후 그 다음 요청은 정상적으로 요청이 된다.
    
2. `replyOnce`를 연달아서 사용하기
    
     `mock
         .onGet('/users')
         .replyOnce(200, users) *// 첫번째 요청*.onGet('/users')
         .replyOnce(500); *// 두번째 요청*`
    
3. 아무 요청이나 mocking 하기 - `onAny()`
    - 보퉁 메서드에 따라 `onGet()`, `onPost()` 식으로 사용하나, `onAny()`를 사용하면 어떤 메서드던 mocking이 가능하다.
        
          `mock.onAny('/foo').reply(200);`
        
    - 만약 주소까지 생략하면 어떤 주소던 mocking 한다.
        
          `mock.onAny().reply(200);`
        
4. `reset`
    
     `mock.reset();`
    
    - mock 인스턴스에 등록된 모든 mock 핸들러를 제거. 만약 테스트 케이스 별로 다른 mock 설정을 하고 싶으면 이 함수를 사용.
5. `restore`
    
     `mock.restore();`
    
    ## axios에서 mocking 기능을 완전히 제거. 만약 테스트를 하다가 요청이 실제로 날아가게 하고 싶으면 이 함수를 사용.

```toc
```

<br>
<br>
