# ๐ Dom & Bom ?

<br />

## Window ๊ฐ์ฒด?

<br />

**Winsow ๊ฐ์ฒด๋ ์๋ฐ์คํฌ๋ฆฝํธ์ ์ต์์๊ฐ์ฒด์ด์ ์ ์ญ๊ฐ์ฒด, ๋ชจ๋  ๊ฐ์ฒด๊ฐ ์์๋ ๊ฐ์ฒด**

<br />

`๊ด๊ณ๋`

<img width="411" alt="DomBom" src="https://user-images.githubusercontent.com/109197023/220119277-fb8c933b-db83-40fd-b22a-3af53b27531b.PNG">

<br />
<br />

## Dom์ด๋?

<br />

**๋จ์ด ๊ทธ๋๋ก '๋ํ๋จผํธ๋ฅผ ๊ฐ์ฒด๋ก ํํํ๋ ๋ชจ๋ธ', ๋ฌธ์ ๊ฐ์ฒด์ ์๋ฏธํ๋ค.**

- ๋ฌธ์ ๊ฐ์ฒด๋ HTML ๋ฌธ์์ ํ๊ทธ๋ค์ JavaScript๊ฐ ์ฝ์ ์ ์๋ ๊ฐ์ฒด(object)๋ก ๋ง๋  ๊ฒ์ด๋ค.
- HTML, XML ๋ฌธ์์ ํ๋ก๊ทธ๋๋ฐ ์ธํฐํ์ด์ค์ด๋ค.
- ์น๋ธ๋ผ์ฐ์ ๊ฐ HTML ๊ฐ์ ๋ฌธ์๋ฅผ ํด์ํ๊ณ , ํ๋ฉด์ ํตํด ํด์๋ ๊ฒฐ๊ณผ๋ฅผ ๋ณด์ฌ์ฃผ๋๋ฐ, ์ด ๊ณผ์ ์ ๋ ๋๋ง์ด๋ผ ํ๋ค.
- DOM์ ์์ ์ฌํญ์ด ์์ ๋ ์ฒ์๋ถํฐ ๋ ๋๋ง์ ๊ฑฐ์น๋๋ฐ, ์ค์ผ์ผ์ด ์ปค์ง์๋ก ๋ธ๋๊ฐ ์ฆ๊ฐํ์ฌ ๋ธ๋ผ์ฐ์ ์ ์๋๊ฐ ๋๋ ค์ง๋ค.

<br />

**๊ฒฐ๊ตญ Dom์ด๋ ๋ธ๋ผ์ฐ์ ๋ HTML ์ฝ๋๋ฅผ ํด์ํด์ ์์๋ค์ ํธ๋ฆฌ ํํ๋ก ๊ตฌ์กฐํํด ํํํ๋ ๋ฌธ์๋ฅผ ์์ฑํ๋๋ฐ ์ด๋ฅผ ๋งํ๋ค.**

<br />
<br />

**Dom ์ ๋ชฉ์ ??**

<br />

<img width="400" alt="DOM๋ชฉ์ 1" src="https://user-images.githubusercontent.com/109197023/220125344-ac7aa259-966a-44bf-8331-ed5b38d0e47a.PNG">

<br />

**HTML์ ์ ์ ์ด๋ฏ๋ก ๋์ ์ธ ์ํธ์์ฉ์ ์ํด์ ์๋ฐ์คํฌ๋ฆฝํธ๋ฅผ ์จ์ผํ๋๋ฐ DOM์ด ํ์ํ๋ค.**

<br />
<br />

`Dom Tree`

<img width="500" alt="Domtree" src="https://user-images.githubusercontent.com/109197023/220119413-485ba21c-f075-4289-a225-cb344ec54f15.PNG">

<br />

```plaintext
Document Node - ํธ๋ฆฌ์ ์ด์ฑ์์ ์กด์ฌํ๋ฉฐ(์์์ ) ๊ฐ๊ฐ์ ํ์ ์์(์๋ฆฌ๋จผ๋, ์ดํธ๋ฆฌ๋ทฐํธ, ํ์คํธ๋ธ๋)์ ์ ๊ทผํ๋ ค๋ฉด       ๋ฌธ์๋ธ๋๋ฅผ ํตํด์ผ ํ๋ค.

Element Node - <p><div><span>๋ฑ ํ๊ทธ๋ค์ ๋งํ๋ค.

Attribute Node - <input>ํ๊ทธ ์์ name, value ๋ฑ์ ์์ฑ์ ์ฌ์ฉํ๋๋ฐ, ์ด๋ฌํ ์์ฑ๋ค์ ๊ฐ๋ฆฌํค๋ ๋ธ๋์ด๋ค.

Text Node - ํ๊ทธ ๋ด ํ์คํธ๋ฅผ ํํํ๋ฉฐ, ์์ ๋ธ๋์ ์์์ด๋ฉฐ, ๋ ํธ๋ฆฌ์ ์ต์ข๋จ์ด๋ค.
```

<br />

**document ๊ฐ์ฒด๋ฅผ ํตํ์ฌ ์ ๊ทผํ  ์ ์๋ค.**

```js
getElementById();
getElementByTagName();
getElementByClassName();
querySelector();
```

<br />

**๊ฐ์ DOM(Virtual DOM)**

- ๊ฐ์ DOM์ ์ค์  DOM์ ๋ณต์ฌ๋ณธ์ ๋ฉ๋ชจ๋ฆฌ ๋ด์ ์ ์ฅํ์ฌ ์ฌ์ฉํ๋ค.
- ์์ ์ด ๋  ๋ ๋ง๋ค ์ ์ฒด๊ฐ ๋ค์ ๋ ๋๋ง ๋์ด ์๋์ ๋จ์ ์ด ์๋ ์ง์ง DOM๊ณผ ๋ฌ๋ฆฌ, ๊ฐ์ DOM์ ๋ณ๊ฒฝ๋  ๋๋ง๋ค ์ง์ง DOM๊ณผ ๋น๊ตํด์ ์ฐจ์ด๋ฅผ ์ฐพ์ ๊ทธ ๋ถ๋ถ๋ง ์์ ํ๋ ํจ์จ์ ์ธ ๋์์ ํ์ฌ ์๋๊ฐ ๋น ๋ฅด๋ค.

<br />

<img width="500" alt="virtualdom" src="https://user-images.githubusercontent.com/109197023/220127096-09fa44cf-7c55-46f5-97d6-ab7b6f5f6c2a.PNG">

<br />

```plaintext
๋ฆฌ์กํธ๊ฐ ๊ฐ์๋์ ๋ฐ์ํ๋ ์ ์ฐจ

1. ๋ญ๊ฐ ๋ฐ๋๋ฉด UI ๋ฅผ ๊ฐ์๋์ ๋ฆฌ๋ ๋๋ง ํ๋ค.
2. ๊ฐ์๋๋ผ๋ฆฌ ๋น๊ตํ๊ณ 
3. ๋ฐ๋ ๋ถ๋ถ๋ง ์ค์  DOM์ ์ ์ฉํ๋ค.
```

<br />

Real Dom

```js
<div id="app">
  <ul>
    <li>
      <input type="checkbox" class="toggle" />
      todo list item 1<button class="remove">์ญ์ </button>
    </li>
    <li class="completed">
      <input type="checkbox" class="toggle" checked />
      todo list item 2<button class="remove">์ญ์ </button>
    </li>
  </ul>
  <form>
    <input type="text" />
    <button type="submit">์ถ๊ฐ</button>
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
      h("button", { className: "remove" }, "์ญ์ ")
    ),
    h(
      "li",
      { className: "completed" },
      h("input", { type: "checkbox", className: "toggle", checked: true }),
      "todo list item 2",
      h("button", { className: "remove" }, "์ญ์ ")
    )
  ),
  h(
    "form",
    h("input", { type: "text" }),
    h("button", { type: "submit" }, "์ถ๊ฐ")
  )
);
```

<br />
<br />

## Bom์ด๋?

<br />

**๋ธ๋ผ์ฐ์ ์ ์ ๊ทผ ํ  ์ ์๋ ๊ฐ์ฒด์ ๋ชจ์์ด๋ค.**

- DOM์ ํ์ฌ ๋์ ๋ณด์ด๋ ์น๋ฌธ์์ ๋ํ ์ ์ด์ ๋ณ๊ฒฝ์ด๋ผ๋ฉด BOM์ window๋ฅผ ์ ์ดํ๋ค.
- window ๊ฐ์ฒด๋ฅผ ํตํด ์ ๊ทผํ  ์ ์๋ค.

```plaintext

window: ๊ฐ์ฅ ์ต์์ ๊ฐ์ฒด๋ก, ์๋ ์์ ๋ ๋ชจ๋  ๊ฐ์ฒด๋ ์ด ๊ฐ์ฒด ์๋์ ์กด์ฌํ๋ค.

- location
- document
- navigator
- history
- screen

```

<br />
<br />

## ์ถ์ฒ

> https://be-a-weapon.tistory.com/144#recentEntries

> https://cbw1030.tistory.com/46

> https://www.youtube.com/watch?v=zyz1eJJjsNE

> https://doqtqu.tistory.com/316

> https://junilhwang.github.io/TIL/Javascript/Design/Vanilla-JS-Virtual-DOM/#_1-%E1%84%80%E1%85%A1%E1%84%89%E1%85%A1%E1%86%BC%E1%84%83%E1%85%A9%E1%86%B7-virtualdom-%E1%84%86%E1%85%A1%E1%86%AB%E1%84%83%E1%85%B3%E1%86%AF%E1%84%80%E1%85%B5
