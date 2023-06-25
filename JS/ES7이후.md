# ✏️ ES7 ~~~ 요약 정리

<br />
<br />

## 목차

1. [**ES7**](#es7)
2. [**ES8**](#es8)
3. [**ES10**](#es10)
4. [**ES11**](#es11)

<br />
<br />

### ES7

```js
//제곱이 간편해진다.
const a = (x) => x ** 3;
```

<br />
<br />

### ES8

```js
console.log("test".padStart(10)); //"          test"
console.log("test".padEnd(10)); //"test          "
```

<br />

```js
let obj = {
  username0: "Santa",
  username1: "Rudolf",
  username2: "Mr.Grinch",
};

//Map과 마찬가지
// 키와 인덱스 조회 가능
Object.keys(obj).forEach((key, index) => {
  console.log(key, obj[key]);
});

// Value만 조회 가능
Object.values(obj).forEach((value) => {
  console.log(value);
});

// 객체를 배열로 변환
Object.entries(obj).forEach((value) => {
  console.log(value);
});
```

<br />
<br />

### ES10

```js
/* ES10 (ES2019) */
// 중첩 배열 삭제 ( [] 이렇게 한 겹당 1, 만약 [[[[[[[]]]]]]] 7겹이니 array.flat(7)를 입력)
const array = [1, [2, 3], [4, 5]];
array.flat(1); // 결과 : [1,2,3,4,5]
// 데이터 정리
const entries = ["bob", "sally", , , , , , , , "cindy"];
entries.flat(); // 결과 ['bob', 'sally', 'cindy'];
```

<br />

```js
const userProfiles = [
  ["commanderTom", 23],
  ["derekZlane", 20],
];
// 배열을 오브젝트로 변환
const obj = Object.fromEntries(userProfiles);
console.log(obj); // 결과 => [{commanderTom, 23}, {derekZlane, 20}]
// 오브젝트를 배열로 변환
console.log(obj.entries(obj)); // 결과 => [["commanderTom", 23], [derekZlane, 20]]
// 선택적 catch할당
try {
  //...
} catch (e) {
  //handle error
}
```

<br />
<br />

### ES11

#### **BigInt**

```textplain
BigInt와 Number는 어떤 면에서 비슷하지만 중요한 차이점이 있다.
예컨대 BigInt는 내장 Math객체의 메서드와 함께 사용할 수 없고, 연산에서 Number와 혼합해 사용할 수 없다.
따라서 먼저 같은 자료형으로 변환해야 한다.

그러나, BigInt가 Number로 바뀌면 정확성을 잃을 수 있으니 주의해야 한다.
또한 bigDecimal이 아니기 때문에 소수점 이하는 언제나 버린다.
```

<br />

#### **Dynamic Import**

```js
//모듈을 동적으로 가져옴
if (condition1 && condition2) {
  const module = await import("./path/to/module.js");
  module.doSomething();
}
```

#### Optional Chaning

```textplain
?. 연산자는 . 체이닝 연산자와 유사하게 작동하지만, 만약 참조가 nullish(null 또는 undefined)이라면, 에러가 발생하는 것 대신에 표현식의 리턴 값은 undefined로 단락된다. 함수 호출에서 사용될 때, 만약 주어진 함수가 존재하지 않는다면, undefined를 리턴한다.
```

```js
const adventurer = {
  name: "Alice",
  cat: { name: "Dinah" },
};

const catName = adventurer.cat?.name; // 'Dinah'
const dogName = adventurer.dog?.name; // undefined
```

#### Nullish Coalescing Operator

널 병합 연산자는 왼쪽 피연산자가 null 또는 undefined일 때 오른쪽 피연산자를 반환하고, 그렇지 않으면 왼쪽 피연산자를 반환하는 논리 연산자이다.

```js
let user = { u1: 0, u2: false, u3: null, u4: undefined u5: '', }
let u1 = user.u1 ?? 'user 1' // 0
let u2 = user.u2 ?? 'user 2' // false
let u3 = user.u3?? 'user 3' // user 3
let u4 = user.u4?? 'user 4' // user 4
let u5 = user.u5?? 'User 5' // ''
```

#### String.protype.matchAll

matchAll 메서드는 지정된 정규식에 대해 문자열과 일치하는 모든 결과의 iterator를 반환하는 메서드(캡쳐링 그룹 포함)
정규 표현식 뒤에 g flag를 사용해주어야 한다.

```js
const regexp = /t(e)(st(\d?))/g;
const str = "test1test2";
const array = [...str.matchAll(regexp)];

console.log(array[0]); // expected output: Array ["test1", "e", "st1", "1"]
console.log(array[1]); // expected output: Array ["test2", "e", "st2", "2"]
```

#### Module Namespace Exports

```js
export * as A from "./moduleA";
export * as B from "./moduleA";

import { A, B } from "./modules";
console.log(A.a); // 1
console.log(A.b); // 2
console.log(B.b); // 3
console.log(B.c); // 4
```

#### import.meta

현재 모듈파일의 메타정보를 가져올 수 있다.

```js
<script type="module" src="my-module.js">
console.log(import.meta); // { url: "file:///home/user/my-module.js" }
```

#### globalThis

globalThis는 환경에 관계없이 전역객체를 통일된 방법으로 참조할 수 있는 방법이다.

```js
// browser environment
console.log(globalThis); // => Window {...}

// node.js environment
console.log(globalThis); // => Object [global] {...}

// web worker environment
console.log(globalThis); // => DedicatedWorkerGlobalScope {...}
```

### 참조

> https://velog.io/@kyusung/after-es6

> https://velog.io/@sungjin5891/JAVASCRIPT-ES7-ES10-%EC%B6%94%EA%B0%80%EB%90%9C-%EA%B8%B0%EB%8A%A5
