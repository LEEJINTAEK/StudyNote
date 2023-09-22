# react-query

 <br />

**실시간 데이터가 중요하면 react-query**

## 사용 이유?

ajax 요청하다보면 이런 기능들이 가끔 필요함

- 몇초마다 자동으로 데이터 다시 가져오게 하려면?

- 요청실패시 몇초 간격으로 재시도?

- 다음 페이지 미리가져오기?

- ajax 성공/실패시 각각 다른 html을 보여주려면?

 <br />
 
**직접 개발해도 되겠지만 귀찮으면 react-query 라는 라이브러리 설치해서 써도 됨** <br />

SNS, 코인거래소같은 실시간 데이터를 보여줘야하는 사이트들이 쓰면 유용!!

<br />
<br />

## 세팅

1. 설치시

```shell
npm install @tanstack/react-query
```

<br />

2. import 해서 사용시엔 이거 입력합시다

```shell
import { QueryClient, QueryClientProvider, useQuery } from '@tanstack/react-query'
```

<br />

3. useQuery쓸 때 '작명' 말고 ['작명']

```shell
useQuery(['작명'],
```

<br />

```js
//index.js

import { QueryClient, QueryClientProvider } from "react-query"; //1번
const queryClient = new QueryClient(); //2번

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <QueryClientProvider client={queryClient}>
    {" "}
    //3번
    <Provider store={store}>
      <BrowserRouter>
        <App />
      </BrowserRouter>
    </Provider>
  </QueryClientProvider>
);
```

<br />
<br />

## 사용

<br />

```js
function App() {
  let result = useQuery("작명", () =>
    axios.get("https://codingapple1.github.io/userdata.json").then((a) => {
      return a.data;
    })
  );
}
```

<br />
<br />

**장점1. ajax 요청 성공/실패/로딩중 상태를 쉽게 파악할 수 있다.**

<br />

```js
function App() {
  let result = useQuery("작명", () =>
    axios.get("https://codingapple1.github.io/userdata.json").then((a) => {
      return a.data;
    })
  );

  return (
    <div>
      {result.isLoading && "로딩중"}
      {result.error && "에러남"}
      {result.data && result.data.name}
    </div>
  );
}
```

<br />

result라는 변수에 ajax 현재 상태가 알아서 저장

- ajax요청이 로딩중일 땐 result.isLoading 이 true

- ajax요청이 실패시엔 result.error 가 true

- ajax요청이 성공시엔 result.data 안에 데이터가 들어옴

<br />
<br />

**장점2. 틈만나면 알아서 ajax 재요청해줍니다.**

<br />

- 페이지 체류하고나서 일정시간이 경과하거나

- 다른 창으로 갔다가 다시 페이지로 돌아오거나

- 다시 메인페이지로 돌아가거나

- 당연히 재요청 끄는 법, 재요청간격 조절하는 법도 있음

<br />

**장점3. 실패시 재시도 알아서 해줌**

<br />

- 잠깐 인터넷이 끊겼거나 서버가 죽었거나 그러면 ajax 요청이 실패하는데.. <br />
  실패했을 때는 얘가 4번인가 5번인가 재시도를 알아서 해줌

<br />
<br />

**장점4. ajax로 가져온 결과는 state 공유 필요없음**

<br />

지금 App 컴포넌트에서 유저이름 가져오는 ajax 요청을 날리고 있을 떄, 유저이름 결과가 Detail 컴포넌트에도 필요하면??

- Detail 컴포넌트에다가 유저이름 ajax 요청하는 코드 똑같이 또 적으면 됨
- react-query는 스마트하기 때문에 ajax 요청이 2개나 있으면 1개만 날려주고
- 캐싱기능이 있기 때문에 이미 같은 ajax 요청을 한 적이 있으면 그걸 우선 가져와서 쓴다.

<br />
<br />

## 결국

**react-query는**

- server-state (DB 데이터)를 프론트엔드에서 실시간 동기화해주는걸 도와준다

- 근데 ajax 요청을 몇초마다 계속 날려서 가져오는 방식이라 좀 비효율적일 수도 있다

- 실시간으로 서버에서 데이터를 자주 보내려면 웹소켓이나 Server-sent events 같은 가벼운 방식들도 있다

- 그래서 react-query는 ajax 관련 기능개발 편하게 할 수 있는데에 의의가 더 있다
