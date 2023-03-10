# React ๊ฐ๋ ์ ๋ฆฌ ๐

<br />
<br />

## ๋ชฉ์ฐจ

<br />

- [JSX?](#jsx)
- [Babel?](#babel)
- [์ปดํฌ๋ํธ](#์ปดํฌ๋ํธ)
- [์คํ์ผ๋ง](#์คํ์ผ๋ง)
- [์ด๋ฒคํธ](#์ด๋ฒคํธ)
- [์ํ](#์ํ)
- [๋ฆฌ์คํธ](#๋ฆฌ์คํธ)
- [ํผ](#ํผ)

<br />
<br />

## JSX?

<br />

- JS์ HTMLํ๊ทธ๋ฅผ ๋ผ์น์ ๋ฌธ๋ฒ
- HTML ํ๊ทธ ์์์  ์ค๊ดํธ({})๋ฅผ ์ฌ์ฉํ์ฌ JS๋ฅผ ์ธ ์ ์๋ค.

```js
const count = 1;
const title = <h1>{count}๋ฒ์งธ</h1>; // h1ํ๊ทธ -> ๋ฆฌ์กํธ ์๋ฆฌ๋จผํธ
```

<br />
<br />

## Babel?

<br />

์ต์  ๋ฌธ๋ฒ์ ๋ธ๋ผ์ฐ์ ๊ฐ ์ดํดํ  ์ ์๋ JS๋ก ํต์ญ

- ๋ธ๋ผ์ฐ์ ๋ JSX๋ฅผ ์ดํดํ์ง ๋ชปํ๊ธฐ ๋๋ฌธ์ Babel์ด๋ผ๋ ํต์ญ์ฌ๊ฐ ํ์ํ๋ค

<br />
<br />

## ์ปดํฌ๋ํธ

<br />

```js
<Card emoji = {dog} title="๋ฉ๋ฉ" />
<Card emoji = {cat} title="๋์น" />

function Card(props){
    return(
        <div>
          {props.emoji}
          <h2>{props.title}</h2>
        </div>
    )
}
```

<br />
<br />

## ์คํ์ผ๋ง

<br />

๋ฆฌ์กํธ์ CSS ๋ผ์น๊ธฐ

<br />

1. CSS ํด๋์ค: className ์ฌ์ฉ <br />
   `<div className ='name'>`
2. ์ธ๋ผ์ธ ์คํ์ผ๋ง: style={{์คํ์ผ์์ฑ:์คํ์ผ๊ฐ}} <br />
   `<div style= {{color:'red'}}>`
3. > https://emotion.sh/docs/introduction
4. > https://tailwindcss.com/

<br />
<br />

## ์ด๋ฒคํธ

<br />

- ์ผ๋ฐ ์๋ฐ์คํฌ๋ฆฝํธ ์ด๋ฒคํธ ๋ชฉ๋ก๊ณผ ๋์ผํ์ง๋ง ์ค๊ฐ์ ๋๋ฌธ์๋ก!!
- onclick => onClick / onsubmit => onSubmit

```js
function handleClick(e) {
  console.log("ํด๋ฆญ");
}
<button onClick={handleClick}>์ ์ถ</button>;
```

<br />
<br />

## ์ํ

<br />

์ปดํฌ๋ํธ ์์์ ์์ ๋กญ๊ฒ ๋ณ๊ฒฝํ  ๊ฐ์ด ํ์ํ  ๋

- **useState ํจ์**๋ก ์ํ๋ฅผ ์ถ๊ฐ
- **const[์ํ๋ช, ์ํ๋ณ๊ฒฝํจ์๋ช] = React.useState(์ด๊ธฐ๊ฐ)**
- ์ปดํฌ๋ํธ ์์์ ๋ง๋ค ์ ์๋ค. <br />

```js
const [counter, setCounter] = React.useState(1);

function countPlus() {
  setCounter(counter + 1); //setCounter(prev => prev + 1)
}
return <button onClick={countPlus}>์นด์ดํฐ๋{cunter}</button>;
```

<br />
<br />

## ๋ฆฌ์คํธ

<br />

๋ฐฐ์ด๋ก ๋ฐ๋ณต๋๋ UI ๊ทธ๋ฆฌ๊ธฐ

- ์น์ฌ์ดํธ๋ฅผ ๋ง๋ค ๋ ์ ๋ง ๋ง์ด ์ด๋ค.
- map์ ์ฌ์ฉํ์ฌ ๋ฆฌ์กํธ UI๋ฅผ ๋ฐํ

```js
const favorites = ["์ด๋ฏธ์ง1",'์ด๋ฏธ์ง2','์ด๋ฏธ์ง3']

<ul>
    {favorites.map(image=><img src={image} />)}
</ul>
```

<br />
<br />

## ํผ

<br />

์ฌ์ฉ์ ์๋ ฅ๊ฐ์ ์ง์  ๋ค๋ฃจ๊ธฐ ์ํด value๋ฅผ ์ํ๋ก ๊ด๋ฆฌ

```js
const [value, setValue] = React.useState("์ด๊ธฐ๊ฐ");
function onValueChange(e) {
  setValue(e.target.value);
}
<form onSubmit={handleSubmit}>
  <input value={value} onChange={onValueChange} />
  <button type="submit">์ ์ถ</button>
</form>;
```

<br />
<br />

## ๋ก์ปฌ์คํ ๋ฆฌ์ง(๋ฆฌ์กํธ x ๋ธ๋ผ์ฐ์  ๊ธฐ๋ฅ)

<br />

- ๊ฐ๋จํ ๋ฐ์ดํฐ ์ ์ฅ์ด ํ์ํ  ๋ localStorage ์ด์ฉ
- `localStorage.setItem('์ด๋ฆ','์')` ์ ์ฅ
- `localStorage.getItem('์ด๋ฆ')` ๋ถ๋ฌ์ค๊ธฐ
