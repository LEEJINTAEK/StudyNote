# React 개념 정리 📝

- 리액트는 HTML을 이쁘게 만들어주는 툴
- 앱처럼 부드럽게 동작하는 html을 만들고 싶을 때 사용하는 툴

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
- [useEffect](#useeffect)
- [ajax](#ajax-서버)
- [if문](#if문-작성법)
- [성능개선](#성능개선)

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

<br />
<br />
<br />

## useEffect

<br />

컴포넌트는

1. 생성이 될 수도 있음 (전문용어로 mount)

2. 재렌더링이 될 수도 있음 (전문용어로 update)

3. 삭제가 될 수도 있음 (전문용어로 unmount)

4. 코드 실행해달라고 간섭할 수 있는데, 갈고리를 달아서 코드를 넣어주면 됨

5. 그럼 진짜 페이지 장착시, 업데이트시, 제거시 코드실행가능 -> Lifecycle hook

<br />

옛날 React에서 Lifecycle hook 쓰는 법

```js
class Detail2 extends React.Component {
  componentDidMount() {
    //Detail2 컴포넌트가 로드되고나서 실행할 코드
  }
  componentDidUpdate() {
    //Detail2 컴포넌트가 업데이트 되고나서 실행할 코드
  }
  componentWillUnmount() {
    //Detail2 컴포넌트가 삭제되기전에 실행할 코드
  }
}
```

<br />

요즘 React에서 Lifecycle hook 쓰는 법

```js
import { useState, useEffect } from "react";

function Detail() {
  useEffect(() => {
    //여기적은 코드는 컴포넌트 로드 & 업데이트 마다 실행됨
    console.log("안녕");
  });

  return 생략;
}
```

<br />
<br />

**정리**

1. 재랜더링마다 코드를 실행가능

```js
useEffect(() => {
  실행할코드;
});

// 컴포넌트 mount시 1회만 실행가능
useEffect(() => {
  실행할코드;
}, []);
```

<br />

2. useEffect 안의 코드 실행 전에 항상 실행 -> 타이머나 서버 코드 실행할 때 정리(?) 로 많이 사용

```js
useEffect(() => {
  return () => {
    실행할코드;
  };
});

// unmount시 1회 실행
useEffect(() => {
  return () => {
    실행할코드;
  };
}, []);
```

3. 응용(state1이 변경될 때만 실행)

```js
useEffect(() => {
  실행할코드;
}, [state1]);
```

<br />
<br />
<br />

## ajax (서버)

<br />

**서버란?**

- 유저가 데이터달라고 요청을 하면 데이터를 보내주는 간단한 프로그램

- 정확한 규격에 맞추어 서버에 데이터 요청

1. 어떤 데이터인지 (URL 형식으로)

2. 어떤 방법으로 요청할지 (GET or POST)

<br />
<br />

**ajax란?**

- 서버에 GET, POST 요청을 할 때 새로고침 없이 데이터를 주고받을 수 있게 도와주는 간단한 브라우저 기능을

- 예를 들어, 새로고침 없이도 쇼핑몰 상품을 더 가져올 수도 있고, 새로고침 없이도 댓글을 서버로 전송할 수도 있고 ...

<br />

**사용하려면??**

1. XMLHttpRequest라는 옛날 문법 쓰기

2. fetch() 라는 최신 문법 쓰기 (js)

3. axios 같은 외부 라이브러리 쓰기

   ```shell
   npm install axios
   ```

<br />

**axios 응용**

```js
import axios from "axios";

function App() {
  let [shoes, setShoes] = useState(data);
  return (
    <button
      onClick={() => {
        axios
          .get("https://codingapple1.github.io/shop/data2.json")
          .then((datas) => {
            let copy = [...shoes, ...datas.data];
            setShoes(copy);
          })
          .catch(() => {
            console.log("실패함");
          });
      }}
    >
      버튼
    </button>
  );
}
```

1. axios를 쓰려면 상단에서 import

2. axios.get(URL) 이러면 그 URL로 GET요청

3. 데이터 가져온 결과는 결과.data 안에 !!

4. 인터넷이 안되거나 URL이 이상하면 실패하는데, 실패했을 때 실행할 코드는 .catch() 안에 적으면 끝.

<br />
<br />

**post 요청 방법**

```js
axios.post("URL", { name: "kim" });

// 실행하면 서버로 { name : 'kim' } 자료가 전송
//완료시 특정 코드를 실행하고 싶으면 이것도 역시 .then() 뒤에 붙이면 됨
```

<br />

**동시에 AJAX 요청 여러개 날리려면**

```js
Promise.all([axios.get("URL1"), axios.get("URL2")]);
//둘 다 완료시 특정 코드를 실행하고 싶으면 .then() 뒤에 붙이면 됨
```

<br />
<br />

**axios vs fetch**

<br />

원래 서버와 문자자료만 주고받을 수 있음 <br />
object/array 이런거 다루려면, object/array 자료에 따옴표를 쳐놓으면 됨 <br />
**"{"name" : "kim"}"** 이걸 **JSON** 이라고 함 <br />

JSON은 문자 취급을 받기 때문에 서버와 자유롭게 주고받을 수 있음 <br />
그래서 실제로 결과.data 출력해보면 따옴표쳐진 JSON이 나와야하는데, <br />
axios 라이브러리는 JSON -> object/array 변환작업을 자동으로 해줘서 <br />
출력해보면 object/array가 나옴

<br />

fetch('URL').then(결과 => 결과.json()).then((결과) => { console.log(결과) } )
쌩자바스크립트 문법인 **fetch()** 를 이용해도 **GET/POST 요청이 가능**한데

그건 JSON -> object/array 이렇게 자동으로 안바꿔줘서 직접 바꾸는 작업이 필요!!

<br />
<br />
 
ajax로 가져온 데이터를 html에 넣을 때 에러 발생 이유는??

- ajax요청으로 데이터를 가져와서, state에 저장하라고 코드를 짜놨고 <br />
  state를 html에 넣어서 보여달라고 `<div> {state.어쩌구} </div>` 이렇게 코드 짰는데, <br />
  state가 비어있다고 에러가 나는 경우가 많다.

- 이유는 ajax 요청보다 html 렌더링이 더 빨라서 그럴 수 있다.
- 따라서, state안에 뭐가 들어있으면 보여달라고 if문 같은걸 추가하거나 그러면 된다.

<br />
<br />
<br />

## if문 작성법

<br />

1. 컴포넌트 안에서 쓰는 if/else

```js
function Component() {
  if (true) {
    return <p>참이면 보여줄 HTML</p>;
  }
  return null;
}
```

<br />

2. JSX안에서 쓰는 삼항연산자

```js
function Component() {
  return (
    <div>
      {1 === 1 ? (
        <p>참이면 보여줄 HTML</p>
      ) : 2 === 2 ? (
        <p>안녕</p>
      ) : (
        <p>반갑</p>
      )}
    </div>
  );
}
```

<br />

3. && 연산자로 if 역할 대신하기

```js
function Component() {
  return <div>{1 === 1 && <p>참이면 보여줄 HTML</p>}</div>;
}
```

<br />

4. switch / case 조건문

```js
function Component2() {
  let user = "seller";
  switch (user) {
    case "seller":
      return <h4>판매자 로그인</h4>;
    case "customer":
      return <h4>구매자 로그인</h4>;
    default:
      return <h4>그냥 로그인</h4>;
  }
}
```

<br />

5. object/array 자료형 응용

```js
function Component() {
  let state = "info";
  return (
    <div>
      {
        {
          info: <p>상품정보</p>,
          shipping: <p>배송관련</p>,
          refund: <p>환불약관</p>,
        }[state]
      }
    </div>
  );
}
```

<br />
<br />
<br />

## 성능개선

<br />
<br />

### **lazy & Suspense**

```js
import Detail from "./routes/Detail.js";
import Cart from "./routes/Cart.js";
```

<br />

```js
import { lazy } from "react";

const Detail = lazy(() => import("./routes/Detail.js"));
const Cart = lazy(() => import("./routes/Cart.js"));
```

- "Detail 컴포넌트가 필요해지면 import 해주세요" 라는 뜻

- 이렇게 해놓으면 Detail 컴포넌트 내용을 다른 js 파일로 쪼갬

- 그래서 첫 페이지 로딩속도를 향상!!

<br />

```js
import { Suspense } from "react";

<Suspense fallback={<div>로딩중임</div>}>
  <Detail shoes={shoes} />
</Suspense>;
```

lazy 사용하면 당연히 Detail 컴포넌트 로드까지 지연시간이 발생할 수 있음. 따라서,

1. Suspense 라는거 import 해오고

2. Detail 컴포넌트를 감싸면 Detail 컴포넌트가 로딩중일 때 대신 보여줄 html 작성도 가능

<br />
<br />

### **memo & useMemo**

```js
import {memo, useState} from 'react'

let Child = memo( function(){
  console.log('재렌더링됨')
  return <div>자식임</div>
})

function Cart(){

  let [count, setCount] = useState(0)

  return (
    <Child />
    <button onClick={()=>{ setCount(count+1) }}> + </button>
  )
}
```

- memo를 import 해와서 원하는 컴포넌트 정의부분을 감싸면 됨

- 그럼 이제 Child로 전송되는 props가 변하거나 그런 경우에만 재렌더링!
  <br />

memo로 감싼 컴포넌트는 헛된 재렌더링을 안시키려고 기존 props와 바뀐 props를 비교하는 연산이 추가로 진행된다.. <br />
props가 크고 복잡하면 이거 자체로도 부담이 될 수도 있음! <br />
그래서 꼭 필요한 곳에만 사용하자

<br /> 
<br />

useMemo라는 문법도 있는데 useEffect와 비슷한 용도 <br />
컴포넌트 로드시 1회만 실행하고 싶은 코드가 있으면 거기 담으면 됨.

```js
import {useMemo, useState} from 'react'

function 함수(){
  return 반복문10억번돌린결과
}

function Cart(){

  let result = useMemo(()=>{ return 함수() }, [])

  return (
    <Child />
    <button onClick={()=>{ setCount(count+1) }}> + </button>
  )
}
```

<br />

1. 예를 들어서 반복문을 10억번 돌려야하는 경우

2. 그 함수를 useMemo 안에 넣어두면 컴포넌트 로드시 1회만 실행

- 그럼 재렌더링마다 동작안하니까 좀 효율적으로 동작
- useEffect 처럼 dependency도 넣을 수 있어서
- 특정 state, props가 변할 때만 실행할 수도 있음

<br />
<br />

### batching & useTransition & useDeferredValue

<br />

[1] batching

```js
setCount(1);
setName(2);
setValue(3); //여기서 1번만 재렌더링됨
```

state변경함수를 연달아서 3개 사용하면 재렌더링도 원래 3번 되어야하지만

리액트는 재렌더링을 마지막에 1회만 처리해줌 -> 일종의 쓸데없는 재렌더링 방지기능인 **batching**

```js
fetch().then(() => {
  setCount(1); //재렌더링됨
  setName(2); //재렌더링됨
});
```

ajax요청, setTimeout안에 state변경함수가 있는 경우 batching이 일어나지 않았는데... <br />
18버전 이후 부터는 어디 있든 간에 재렌더링은 마지막에 1번만 됨 <br /> <br />
batching 되는게 싫고 state변경함수 실행마다 재렌더링시키고 싶으면 **flushSync**라는 함수를 쓰자

<br />
<br />

[2] useTransition

<br />

```js
import { useState, useTransition } from "react";

let a = new Array(10000).fill(0); // 성능저하 만들기

function App() {
  let [name, setName] = useState("");
  let [isPending, startTransition] = useTransition(); //보통 변수 작명은 이렇게..

  return (
    <div>
      <input
        onChange={(e) => {
          startTransition(() => {
            setName(e.target.value);
          });
        }}
      />

      {a.map(() => {
        return <div>{name}</div>;
      })}
    </div>
  );
}
```

- useTransition() 쓰면 그 자리에 [변수, 함수]가 남는다.

- 그 중 우측에 있는 startTransition() 함수로 state변경함수 같은걸 묶으면 그걸 다른 코드들보다 나중에 처리해 줌

- 그래서 <input> 타이핑같이 즉각 반응해야하는걸 우선적으로 처리해줄 수 있음

- 타이핑해보면 아까보다 반응속도가 훨씬 낫다.

<br />

물론 근본적인 성능개선이라기보단 특정코드의 실행시점을 뒤로 옮겨주는 것일 뿐....
html이 많으면 여러페이지로 쪼개쓰자.

<br />

```js
{
  isPending
    ? "로딩중기다리셈"
    : a.map(() => {
        return <div>{name}</div>;
      });
}
```

위의 isPending은 startTransition 으로 감싼 코드가 처리중일 때 true로 변하는 변수 <br />
따라서 위와 같이 사용할 수 있음

<br />
<br />

[3] useDeferredValue

startTransition() 이거랑 용도가 똑같다. <br />
근데 얘는 state 아니면 변수하나를 집어넣을 수 있게 되어있다...<br />
그래서 그 변수에 변동사항이 생기면 그걸 늦게 처리해줌

<br />

```js
import { useState, useDeferredValue } from "react";

let a = new Array(10000).fill(0);

function App() {
  let [name, setName] = useState("");
  let state1 = useDeferredValue(name);

  return (
    <div>
      <input
        onChange={(e) => {
          setName(e.target.value);
        }}
      />

      {a.map(() => {
        return <div>{state1}</div>;
      })}
    </div>
  );
}
```

<br />

- useDeferredValue 안에 state를 집어넣으면 그 state가 변동사항이 생겼을 때 나중에 처리함
- 그리고 처리결과는 let state에 저장해줌
