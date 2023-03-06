# React 개념 정리 📝

<br />
<br />

## 목차

<br />

- [JSX?](#jsx)
- [Babel?](#babel)
- [컴포넌트](#컴포넌트)
- [스타일링](#스타일링)
- [이벤트](#이벤트)
- [상태](#상태)
- [리스트](#리스트)
- [폼](#폼)

<br />
<br />

## JSX?

<br />

- JS에 HTML태그를 끼얹은 문법
- HTML 태그 안에선 중괄호({})를 사용하여 JS를 쓸 수 있다.

```js
const count = 1;
const title = <h1>{count}번째</h1>; // h1태그 -> 리액트 엘리먼트
```

<br />
<br />

## Babel?

<br />

최신 문법을 브라우저가 이해할 수 있는 JS로 통역

- 브라우저는 JSX를 이해하지 못하기 때문에 Babel이라는 통역사가 필요하다

<br />
<br />

## 컴포넌트

<br />

```js
<Card emoji = {dog} title="멍멍" />
<Card emoji = {cat} title="냐옹" />

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

## 스타일링

<br />

리액트에 CSS 끼얹기

<br />

1. CSS 클래스: className 사용 <br />
   `<div className ='name'>`
2. 인라인 스타일링: style={{스타일속성:스타일값}} <br />
   `<div style= {{color:'red'}}>`
3. > https://emotion.sh/docs/introduction
4. > https://tailwindcss.com/

<br />
<br />

## 이벤트

<br />

- 일반 자바스크립트 이벤트 목록과 동일하지만 중간을 대문자로!!
- onclick => onClick / onsubmit => onSubmit

```js
function handleClick(e) {
  console.log("클릭");
}
<button onClick={handleClick}>제출</button>;
```

<br />
<br />

## 상태

<br />

컴포넌트 안에서 자유롭게 변경할 값이 필요할 때

- **useState 함수**로 상태를 추가
- **const[상태명, 상태변경함수명] = React.useState(초기값)**
- 컴포넌트 안에서 만들 수 있다. <br />

```js
const [counter, setCounter] = React.useState(1);

function countPlus() {
  setCounter(counter + 1); //setCounter(prev => prev + 1)
}
return <button onClick={countPlus}>카운터는{cunter}</button>;
```

<br />
<br />

## 리스트

<br />

배열로 반복되는 UI 그리기

- 웹사이트를 만들 때 정말 많이 쓴다.
- map을 사용하여 리액트 UI를 반환

```js
const favorites = ["이미지1",'이미지2','이미지3']

<ul>
    {favorites.map(image=><img src={image} />)}
</ul>
```

<br />
<br />

## 폼

<br />

사용자 입력값을 직접 다루기 위해 value를 상태로 관리

```js
const [value, setValue] = React.useState("초기값");
function onValueChange(e) {
  setValue(e.target.value);
}
<form onSubmit={handleSubmit}>
  <input value={value} onChange={onValueChange} />
  <button type="submit">제출</button>
</form>;
```

<br />
<br />

## 로컬스토리지(리액트 x 브라우저 기능)

<br />

- 간단한 데이터 저장이 필요할 때 localStorage 이용
- `localStorage.setItem('이름','얍')` 저장
- `localStorage.getItem('이름')` 불러오기
