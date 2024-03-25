# Browser Rendering

## CSR(Client Side Rendering)?

- Ajax등의 기술, 자바스크립트 프레임워크를 활용하여, <br />
  데이터를 받아 자바스크립트로 페이지를 동적으로 만들 수 있게 됨
- 데이터는 XML,JSON 현태로 클라이언트에 전송

<br />

![image](https://github.com/LEEJINTAEK/Algorithm_Solving/assets/109197023/4f4083c6-ccab-4d8f-bf2e-4f37fc1c9478)

<br />

```plaintext
과정 설명

1. User가 Website 요청을 보냄
2. CDN이 HTML 파일과 JS로 접근할 수 있는 링크를 클라이언트로 보냄
3. 클라이언트는 HTML과 JS를 다운로드 받음 (이때 SSR과 달리 유저는 아무것도 볼 수 없음)
4. 다운이 완료된 JS가 실행된다. 데이터를 위한 API가 호출됨 (이때 유저들은 placeholder를 보게된다. )
5. 서버가 API로부터의 요청에 응답한다.
6. API로부터 받아온 data를 placeholder 자리에 넣어준다. 이제 페이지는 상호작용이 가능해짐
```

<br />

**장점?**

1. 자바스크립트만으로 완전히 페이지를 만들 수 있음
2. 자바스크립트를 최대한도로 활용하여 HTML, CSS 동적 생성
3. 컴포넌트 단위로 코드를 나누고, 다양한 디자인 패턴을 적용하는 등, <br />
   클라이언트 개발의 수준을 한 단계 끌어올림
4. Full page load 없이 라우팅
   <br />

**단점?**

1. SEO가 좋지 않음
2. JS코드가 많으면 앱 로딩이 느려짐

<br />
<br />

## SSR(Server Side Rendering)?

- 서버에서 자바스크립트를 이용해 페이지를 미리 빌드
- 컴포넌트 생성에 필요한 API 요청, routing, redux store 생성 등을 처리
- 클라이언트는 빌드된 페이지와 자바스크립트를 받아, <br />
  웹앱을 CSR처럼 동작하게 함
- Universal Rendering이라고 함

<br />

![image](https://github.com/LEEJINTAEK/Algorithm_Solving/assets/109197023/291d6c01-a9f0-466e-8ae3-ca51bf1122b2)

<br />

```plaintext
과정 설명

1. User가 Website 요청을 보냄
2. Server는 'Ready to Render'. 즉, 즉시 렌더링 가능한 html파일을 만듦
3. 클라이언트에 전달되는 순간, 이미 렌더링 준비가 되어있기 때문에 HTML은 즉시 렌더링 된다. 그러나 사이트 자체는 조작 불가능하다. (Javascript가 읽히기 전)
4. 클라이언트가 자바스크립트를 다운
5. 다운 받아지고 있는 사이에 유저는 컨텐츠는 볼 수 있지만 사이트를 조작 할 수는 없다. 이때의 사용자 조작을 기억
6. 브라우저가 Javascript 프레임워크를 실행
7. JS까지 성공적으로 컴파일 되었기 때문에 기억하고 있던 사용자 조작이 실행되고 이제 웹 페이지는 상호작용 가능
```

<br />

**장점?**

- 첫 페이지 로딩 속도가 CSR보다 빠르다
- SEO 가능

**단점?**

- 초기 로딩 이후 페이지 이동 시 속도가 느림

<br />
<br />

## 사용 권장 정리

SSR

```plaintext
1. 네트워크가 느릴 때  (CSR은 한번에 모든 것을 불러오지만 SSR은 각 페이지마다 나눠불러오기 때문)
2. SEO(serach engine optimization : 검색 엔진 최적화)가 필요할 때
3. 최초 로딩이 빨라야하는 사이트를 개발 할 때
4. 메인 스크립트가 크고 로딩이 매우 느릴 때 CSR은 메인스크립트가 로딩이 끝나면 API로 데이터 요청을 보낸다.
    하지만 SSR은 한번의 요청에 아예 렌더가 가능한 페이지가 돌아온다.
5. 웹 사이트가 상호작용이 별로 없을 때
```

<br />

CSR

```plaintext
1. 네트워크가 빠를 때
2. 서버의 성능이 좋지 않을 때
3. 사용자에게 보여줘야 하는 데이터의 양이 많을 때 (로딩창을 띄울 수 있는 장점이 있다.)
4. 메인 스크립트가 가벼울 때
5. SEO 필요없을 때😤
6. 웹 어플리케이션에 사용자와 상호작용할 것들이 많을 때 (아예 렌더링 되지 않아서 사용자의 행동을 막는 것이 경험에 오히려 유리함)
```

<br />

## React 활용한 SSR

1. ReactDOMServer

- ReactDOMServer를 활용하여, 특정 React Component를 HTML로 빌드
- Node.js 서버에서 JSX를 사용하여 페이지 빌드

<br />

2. renderToString

- React Component를 HTML로 변환
- 클라이언트의 페이지 요청 시, 변환된 HTML string을 전달
- renderToNodeStream은 readable stream을 생성 <br /> 브라우저가 받아서 점진적으로 페이지 그림

<br />

3. ReactDom.hydrate

- renderToString으로 생성한 HTML의 root기준으로, <br /> 받아온 React code를 통해 markup에 이벤트 핸들러를 등록하는 등 컴포넌트화

- 서버에서 생성한 컴포넌트와 브라우저에서 Hydration을 거친 후의 마크업이 다르면, <br /> React runtime은 경고를 보냄 ex. 현재 시간을 보여주는 컴포넌트

- 경고 발생 시, 어느 부분에서 차이점이 생기는지 반드시 파악해야 함

- componentDidMOunt 역할을 하는 useEffect의 경우, SSR시 서버에서 동작하지 않음

- data loading 등의 처리를 별도로 해주어야 할 필요가 있음

### 참조

> https://proglish.tistory.com/216

> https://swtrack.elice.io/courses/

> https://www.startupcode.kr/company/blog/archives/12
