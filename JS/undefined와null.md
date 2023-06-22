# undefined 와 null 차이❓

<br />

**undefined** 와 **null** 은 JavaScript에서 모두 값이 없음을 나타내는데 사용되는 특별한 값!
하지만 undefined와 null은 서로 다른 의미를 가지고 있다.

<br />
<br />

## undefined?

<br />

```textplain
1. 변수가 선언되었지만 값을 할당하지 않은 경우
2. 함수에서 반환 값이 지정되지 않은 경우
3. 객체의 속성이 존재하지 않는 경우
```

**따라서 undefuned는 아직 정의되지 않음을 의미**

<br />
<br />

## 차이?

<br />

```js
let x;
console.log(x); //undefined

let y = null;
console.log(y); //null
```

따라서,

➡️ **undefined**는 변수가 정의되지 않았거나 값이 할당되지 않았을 때 사용
➡️ **null**은 값이 없음을 명시적으로 나나낼 때 사용

<br />
<br />

## 출처

> https://www.crocus.co.kr/1842

> https://2ssue.github.io/common_questions_for_Web_Developer/docs/Javascript/13_undefined&null.html#undefined
