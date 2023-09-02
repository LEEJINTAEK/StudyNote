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
- [Class 이용한 옛날 react 문법 (참조)](#class-이용한-옛날-react-문법-참조)
- [라우터](#리액트-라우터)

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

5. **스타일 컴포넌트**

```js
import styled from "styled-components";

const Btn = styled.button`
  background: ${(props) => props.bg};
  color: ${(props) => (props.bg == "blue" ? "white" : "black")};
  padding: 10px;
`;

<Btn bg="blue">클릭해~</Btn>;
```

방식은 위와 같다.

<br />

```plaintext
장점
1. css 파일 오픈할 필요 없이 js에서 바로 스타일 가능
2. 다른 js파일로 스타일 오염이 없음
3. 페이지 로딩시간 단축 <- html페이지의 <style>태그에 넣어줘서..
4. props 재활용 가능

단점
1. js 파일이 복잡해지고 컴포넌트가 styled인지 일반 컴포넌트인지 구별이 어려움
2. js파일간 중복 디자인이 많아지면 import 기능 사용하면 되지만, 일반 css 사용과 차이 없어짐
3. css 담당 디자이너가 있다면 협업시 불편할 수 있음 -> css를 다시 styled-component로 바꿔야 할...
```

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

<br />
<br />

## Class 이용한 옛날 react 문법 (참조)

<br />

### 컴포넌트 만들기

```js
class Compo extends React.Component {
  constructor() {
    super();
  }

  render() {
    return <div>안녕</div>;
  }
}
```

```plaintext
1. class "~~~" 컴포넌트 이름 작명

2. constructor, super, render 함수 3개 채움 (기본 템플릿같은 것)

3. return 안에 축약할 html 적는다.
```

<br />
<br />

### State 다루기

<br />

만들기

```js
class Compo extends React.Component {
  constructor() {
    super();
    this.state = {
      name: "kim",
      age: 20,
    };
  }

  render() {
    return <div>안녕 {this.state.name}</div>;
  }
}
```

- this.state 라는 변수만들고 거기 안에다가 object 형식으로 state 쭉 나열

<br />

변경

```js
class Compo extends React.Component {
  constructor() {
    super();
    this.state = {
      name: "kim",
      age: 20,
    };
  }

  render() {
    return (
      <div>
        안녕 {this.state.age}
        <button
          onClick={() => {
            this.setState({ age: 21 });
          }}
        >
          버튼
        </button>
      </div>
    );
  }
}
```

- this.setState라는 기본함수를 가져다가 쓴다.
- 소괄호안에 새로운 state 넣으면 그걸로 기존 state를 업데이트해준다.

<br />
<br />

### props

```js
class Compo extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: "kim",
      age: 20,
    };
  }

  render() {
    return <div>안녕 {this.props.프롭스이름}</div>;
  }
}
```

- constructor, super에 props 파라미터 등록하고 this.props 쓰면 props 나온다.

<br />
<br />

## 리액트 라우터

<br />

1. 기본 라우터 설치

```shell
npm install react-router-dom@6
```

<br />

2. 세팅(index.js)

```js
import { BrowserRouter } from "react-router-dom";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </React.StrictMode>
);
```

<br />
<br />

3. **사용하기 (참조)**

<br />

```js
import {
  Routes,
  Route,
  Link,
  useNavigate,
  Outlet,
  Navigate,
  useParams,
} from "react-router-dom";
```

<br />

```js
//url 경로마다 다른 페이지를 보여주고 싶으면
<Route path="/detail" element={ <div>상세페이지</div> } />
<Route path="/about" element={ <div>어바웃페이지</div> } />

//페이지 링크 (Link, navigate)
<Link className="link" to="/">
   Home
</Link>

let navigate = useNavigate();
<Nav.Link
  onClick={() => {
    navigate("/");
  }}
  >
  Home
</Nav.Link>
```

<br />

```js
//서브 경로( Nested routes )
<Route path="/about" element={<About />}>
  <Route path="member" element={<div>멤버들</div>} />
  <Route path="location" element={<div>회사위치</div>} />
</Route>;

//<Outlet>은 nested routes안의 element들을 어디에 보여줄지 표기하는 곳
function About() {
  return (
    <div>
      <h4>about페이지</h4>
      <Outlet></Outlet>{" "}
    </div>
  );
}
```

<br />

```js
//응용

//경로에는 /~~~/~~ 아무렇게 붙여도 상관없다.
// "*" 작성한 경로 외의 것들 -> 404 페이지 응용
//페이지 여러개 만들려면 -> path 작명할 때 /:어쩌구 이렇게 사용하면 "아무 문자"를 뜻 -> "/detail/:id"

<Routes>
  <Route path="/" element={<ShoesPage shoes={shoes} />}></Route>
  <Route path="/detail/:id" element={<Detail shoes={shoes} />}></Route>
  <Route path="*" element={<>404~~</>}></Route>

  <Route path="/event" element={<Event />}>
    <Route path="one" element={<p>첫 주문시 신발 하나</p>}></Route>
    <Route path="two" element={<p>생일 쿠폰 받기</p>}></Route>
  </Route>
</Routes>;

// /:url파라미터 자리에 유저가 입력한 값을 가져옴
//누가 /detail/1로 접속하면 id라는 변수에 1이 들어옴
let { id } = useParams();
console.log(id); // 1
```
