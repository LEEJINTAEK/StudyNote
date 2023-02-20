# 📖 Dom & Bom ?

<br />

## Window 객체?

<br />

**Winsow 객체는 자바스크립트의 최상위객체이자 전역객체, 모든 객체가 소속된 객체**

<br />

`관계도`

<img width="411" alt="DomBom" src="https://user-images.githubusercontent.com/109197023/220119277-fb8c933b-db83-40fd-b22a-3af53b27531b.PNG">

<br />
<br />

## Dom이란?

<br />

**단어 그대로 '도큐먼트를 객체로 표현하는 모델', 문서 객체을 의미한다.**

- 문서 객체란 HTML 문서의 태그들을 JavaScript가 읽을 수 있는 객체(object)로 만든 것이다.
- HTML, XML 문서의 프로그래밍 인터페이스이다.
- 웹브라우저가 HTML 같은 문서를 해석하고, 화면을 통해 해석된 결과를 보여주는데, 이 과정을 렌더링이라 한다.
- DOM은 수정사항이 있을 때 처음부터 렌더링을 거치는데, 스케일이 커질수록 노드가 증가하여 브라우저의 속도가 느려진다.

<br />

**결국 Dom이란 브라우저는 HTML 코드를 해석해서 요소들을 트리 형태로 구조화해 표현하는 문서를 생성하는데 이를 말한다.**

<br />
<br />

**Dom 의 목적??**

<br />

<img width="400" alt="DOM목적1" src="https://user-images.githubusercontent.com/109197023/220125344-ac7aa259-966a-44bf-8331-ed5b38d0e47a.PNG">

<br />

**HTML은 정적이므로 동적인 상호작용을 위해서 자바스크립트를 써야하는데 DOM이 필요하다.**

<br />
<br />

`Dom Tree`

<img width="500" alt="Domtree" src="https://user-images.githubusercontent.com/109197023/220119413-485ba21c-f075-4289-a225-cb344ec54f15.PNG">

<br />

```plaintext
Document Node - 트리의 초싱위에 존재하며(시작점) 각각의 하위 요소(엘리먼드, 어트리뷰트, 텍스트노드)에 접근하려면       문서노드를 통해야 한다.

Element Node - <p><div><span>등 태그들을 말한다.

Attribute Node - <input>태그 안에 name, value 등의 속성을 사용하는데, 이러한 속성들을 가리키는 노드이다.

Text Node - 태그 내 텍스트를 표현하며, 요소 노드의 자식이며, 돔 트리의 최종단이다.
```

<br />

**document 객체를 통하여 접근할 수 있다.**

```js
getElementById();
getElementByTagName();
getElementByClassName();
querySelector();
```

<br />

**가상 DOM(Virtual DOM)**

- 가상 DOM은 실제 DOM의 복사본을 메모리 내에 저장하여 사용한다.
- 수정이 될 때 마다 전체가 다시 렌더링 되어 속도의 단점이 있는 진짜 DOM과 달리, 가상 DOM은 변경될 때마다 진짜 DOM과 비교해서 차이를 찾아 그 부분만 수정하는 효율적인 동작을 하여 속도가 빠르다.

<br />

<img width="500" alt="virtualdom" src="https://user-images.githubusercontent.com/109197023/220127096-09fa44cf-7c55-46f5-97d6-ab7b6f5f6c2a.PNG">

<br />

```plaintext
리액트가 가상돔을 반영하는 절차

1. 뭐가 바뀌면 UI 를 가상돔에 리렌더링 한다.
2. 가상돔끼리 비교하고
3. 바뀐 부분만 실제 DOM에 적용한다.
```

<br />

Real Dom

```js
<div id="app">
  <ul>
    <li>
      <input type="checkbox" class="toggle" />
      todo list item 1<button class="remove">삭제</button>
    </li>
    <li class="completed">
      <input type="checkbox" class="toggle" checked />
      todo list item 2<button class="remove">삭제</button>
    </li>
  </ul>
  <form>
    <input type="text" />
    <button type="submit">추가</button>
  </form>
</div>
```

Virtual Dom

```js
function h(type, props, ...children) {
  return { type, props, children: children.flat() };
}

h(
  "div",
  { id: "app" },
  h(
    "ul",
    null,
    h(
      "li",
      null,
      h("input", { type: "checkbox", className: "toggle" }),
      "todo list item 1",
      h("button", { className: "remove" }, "삭제")
    ),
    h(
      "li",
      { className: "completed" },
      h("input", { type: "checkbox", className: "toggle", checked: true }),
      "todo list item 2",
      h("button", { className: "remove" }, "삭제")
    )
  ),
  h(
    "form",
    h("input", { type: "text" }),
    h("button", { type: "submit" }, "추가")
  )
);
```

<br />
<br />

## Bom이란?

<br />

**브라우저에 접근 할 수 있는 객체의 모음이다.**

- DOM은 현재 눈에 보이는 웹문서에 대한 제어와 변경이라면 BOM은 window를 제어한다.
- window 객체를 통해 접근할 수 있다.

```plaintext

window: 가장 최상위 객체로, 아래 서술된 모든 객체는 이 객체 아래에 존재한다.

- location
- document
- navigator
- history
- screen

```

<br />
<br />

## 출처

> https://be-a-weapon.tistory.com/144#recentEntries

> https://cbw1030.tistory.com/46

> https://www.youtube.com/watch?v=zyz1eJJjsNE

> https://doqtqu.tistory.com/316

> https://junilhwang.github.io/TIL/Javascript/Design/Vanilla-JS-Virtual-DOM/#_1-%E1%84%80%E1%85%A1%E1%84%89%E1%85%A1%E1%86%BC%E1%84%83%E1%85%A9%E1%86%B7-virtualdom-%E1%84%86%E1%85%A1%E1%86%AB%E1%84%83%E1%85%B3%E1%86%AF%E1%84%80%E1%85%B5
