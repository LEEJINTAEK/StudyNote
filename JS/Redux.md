# Redux 개념 정리 📝

<br />

## 목차

- [**Context API**](#context-api)
- [**Redux 세팅**](#redux-세팅하기)

<br />
<br />

## Context API??

<p> Context API와 Redux는 둘 다 상태 관리를 위한 도구로 React 애플리케이션에서 상태를 효율적으로 관리하기 위해 사용</p>

<br />

사용해보기

```js
export let 재고context = React.createContext();

function App() {
  let [재고, 재고변경] = useState([10, 11, 12]);

  return (
    <Context1.Provider value={{ 재고, shoes }}>
      <Detail shoes={shoes} />
    </Context1.Provider>
  );
}
```

1. 일단 createContext() 함수를 가져와서 context를 하나 만들어준다. <br />
   (context를 쉽게 비유해서 설명하자면 state 보관함)

2. 아까만든 Context1로 원하는 곳을 감싸고 공유를 원하는 state를 value 안에 다 적으면 된다. <br />
   그럼 이제 Context1로 감싼 모든 컴포넌트와 그 자식컴포넌트는 state를 props 전송없이 직접 사용가능 !!

```js
import { useState, useEffect, useContext } from "react";
import { Context1 } from "./../App.js";

function Detail() {
  let { 재고 } = useContext(Context1);

  return <div>{재고}</div>;
}
```

Context에 있던 state를 꺼내 쓰려면

3. Context1을 import 하고 <br />
4. useContext() 안에 담으면 된다. (Context 해체해주는 함수)
5. 그럼 그 자리에 공유했던 모든 state가 남고, 변수에 담아서 가져다쓰거나 하면 된다.

<br />
<br />

**Context API 단점**

1. state 변경시 쓸데없는 컴포넌트까지 전부 재렌더링이 되고

2. useContext() 를 쓰고 있는 컴포넌트는 나중에 다른 파일에서 재사용할 때 Context를 import 하는게 귀찮아질 수 있다.

그래서 이것 보다는 redux 같은 외부라이브러리를 많이들 사용한다니... 지금부터 Redux를 공부해본다.

<br />
<br />
<br />

## Redux Toolkit 세팅하기

<br />

![image](https://github.com/LEEJINTAEK/StudyNote/assets/109197023/c200916a-9c1d-4693-aa52-79958ad7f605)

<br />

1. 설치

```shell
npm install @reduxjs/toolkit react-redux
```

<br />

2. 세팅

```js
import { configureStore } from "@reduxjs/toolkit";

export default configureStore({
  reducer: {},
});
```

<br />

<p>아무데나 store.js 파일을 만들어서 위 코드를 복붙(state들을 보관하는 파일) </p>

<br />

```js
import { Provider } from "react-redux";
import store from "./store.js";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
    <Provider store={store}>
      <BrowserRouter>
        <App />
      </BrowserRouter>
    </Provider>
  </React.StrictMode>
);
```

<br />

index.js 파일가서 Provider 라는 컴포넌트와 아까 작성한 파일을 import <br />

그리고 밑에 <Provider store={import해온거}> 이걸로 <App/> 을 감싸면 됨. <br />

그럼 이제 <App>과 그 모든 자식컴포넌트들은 store.js에 있던 state를 맘대로 꺼내쓸 수 있음 <br />

<br />
<br />
