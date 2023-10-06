# 자바스크립트의 this?

<br />

**자바스크립트 내에서 this는 '어디서 불렀느냐' 즉, 선언이 아닌 호출에 따라 달라진다!!**

<br />
<br />

## 단독 쓰여진 this...

<br />

```js
console.log(this); // window
```

<br />

단독으로 쓰이면... global object를 가르키는데, 브라우저에 호출했으니 object Window!! 가 된다.

<br />
<br />

## 함수 안에 this..

<br />

함수 안에서 this는 함수의 주인에게 바인딩 되는데,
함수의 주인은? window객체다!

<br />

```js
let num = 0;
function addNum() {
  this.num = 100;
  num += 1;

  console.log(num); // 101
  console.log(window.num); // 101
  console.log(num === window.num); // true
}

addNum();
```

<br />

위 코드에서 this.num의 this는 window 객체를 가리킨다.<br />
따라서 num은 전역 변수를 가리키게 된다. <br />

다만, strict mode(엄격 모드)에서는 조금 다르다.<br />
함수 내의 this에 디폴트 바인딩이 없기 때문에 undefined가 된다.

```js
"use strict";

let num = 0;
function addNum() {
  this.num = 100; //ERROR! Cannot set property 'num' of undefined
  num += 1;
}

addNum();
```

<br />

**use Strict?**
<br />

이렇게 (의미 없는 this) 일반 모드에서는 함수가 전역 객체를 가리키는 문제가 있지만, <br />
"use strict" 모드에서는 함수 내에서 "this"의 값이 "undefined"가 된다. <br />
**이는 오류를 미리 방지하는 데 도움이 된다.**

<br />
<br />

## 매서드 안에 this...

<br />

메서드 호출 시 메서드 내부 코드에서 사용된 this는 해당 메서드를 호출한 객체로 바인딩 된다.

```js
const person = {
  firstName: "John",
  lastName: "Doe",
  fullName: function () {
    return this.firstName + " " + this.lastName;
  },
};

person.fullName(); //"John Doe"
```

<br />
<br />

## 이벤트 핸들러 안에 this...

 <br />

이벤트 핸들러에서 this는 이벤트를 받는 HTML 요소를 가리킨다.

```js
const btn = document.querySelector("#btn");
btn.addEventListener("click", function () {
  console.log(this); //#btn
});
```

<br />
<br />

## 생성자 안에 this...

 <br />

생성자 함수가 생성하는 객체로 this가 바인딩 된다.

```js
function Person(name) {
  this.name = name;
}

const kim = new Person("kim");
const lee = new Person("lee");

console.log(kim.name); //kim
console.log(lee.name); //lee
```

하지만 new 키워드를 빼먹는 순간 일반 함수 호출과 같아지기 때문에, 이 경우는 this가 window에 바인딩된다!!

```js
const name = "window";
function Person(name) {
  this.name = name;
}

const kim = Person("kim");

console.log(window.name); //kim
```

<br />
<br />

## 명시적 바인딩을 한 this

<br />

명시적 바인딩은 짝을 지어주는 것

**apply()** 와 **call()** 메서드는 Function Object에 기본적으로 정의된 메서드인데, <br />
**인자를 this로 만들어주는 기능**을 함 <br />

```js
function whoisThis() {
  console.log(this);
}

whoisThis(); //window

const obj = {
  x: 123,
};

whoisThis.call(obj); //{x:123}
```

<br />

apply()에서 매개변수로 받은 첫 번째 값은 함수 내부에서 사용되는 this에 바인딩되고,
두 번째 값인 배열은 자신을 호출한 함수의 인자로 사용됨

```js
//이렇게 두 생성자 함수, this.name과 this.level을 받아오는 부분이 똑같으면

function Character(name, level) {
  this.name = name;
  this.level = level;
}

function Player(name, level, job) {
  Character.apply(this, [name, level]);
  this.job = job;
}

const me = new Player("Nana", 10, "Magician");
```

<br />

call()도 apply()와 거의 같다.
**차이점이 있다면 call()은 인수 목록을 받고 apply()는 인수 배열을 받는다는 차이가 있다.**

위 코드를 call()로 바꿔 쓴다면 아래와 같은데, <br />
둘다 일단은 함수를 호출한다는 것에 주의하자

```js
function Character(name, level) {
  this.name = name;
  this.level = level;
}

function Player(name, level, job) {
  Character.call(this, name, level);
  this.job = job;
}

const me = new Player("Nana", 10, "Magician");
```

**apply()나 call()은 보통 유사배열 객체에게 배열 메서드를 쓰고자 할 때 사용**

- 예를 들어 arguments 객체는 함수에 전달된 인수를 Array 형태로 보여주지만 배열 메서드를 쓸 수가 없다

- 이럴 때 가져다 쓰면 됨

```js
//1 오류
function func(a, b, c) {
  console.log(arguments);

  arguments.push("hi!"); //ERROR! (arguments.push is not a function);
}

//2 apply
function func(a, b, c) {
  const args = Array.prototype.slice.apply(arguments);
  args.push("hi!");
  console.dir(args);
}

func(1, 2, 3); // [ 1, 2, 3, 'hi!' ]

//3 call
const list = {
  0: "Kim",
  1: "Lee",
  2: "Park",
  length: 3,
};

Array.prototype.push.call(list, "Choi");
console.log(list);
```

<br />
<br />

## 화살표 함수로 쓴 this

 <br />

함수 안에서 this가 전역 객체가 되어 문제가 생기면 화살표 함수를 쓰면 된다.

- 일반 함수는 함수를 호출할 때 함수가 어떻게 호출되었는지에 따라 this에 바인딩 할 객체가 동적으로 결정<br /> 콜백 함수 내부의 this는 전역 객체 window 가리킴
- 화살표 함수는 함수를 선언할 떄 this에 바인딩 할 객체가 정적으로 결정<br /> this는 언제나 상위 스코프의 this를 가리킴(Lexical this)

<br />

```js
// 일반 함수 표현식
const Person = function (name, age) {
  this.name = name;
  this.age = age;
  this.say = function () {
    console.log(this); // Person {name: "Nana", age: 28}

    setTimeout(function () {
      console.log(this); // Window
      console.log(this.name + " is " + this.age + " years old");
    }, 100);
  };
};
const me = new Person("Nana", 28);

me.say(); //global is undefined years old

// 화살표 함수
const Person = function (name, age) {
  this.name = name;
  this.age = age;
  this.say = function () {
    console.log(this); // Person {name: "Nana", age: 28}

    setTimeout(() => {
      console.log(this); // Person {name: "Nana", age: 28}
      console.log(this.name + " is " + this.age + " years old");
    }, 100);
  };
};
const me = new Person("Nana", 28); //Nana is 28 years old
```

<br />
<br />

**화살표 함수를 사용해서는 안되는 경우**

1. 객체의 메서드로 사용할 때

```js
const person = {
  name: "John",
  sayHello: () => {
    console.log(`Hello, ${this.name}`);
  },
};
person.sayHello(); // 출력: "Hello, undefined"
```

화살표 함수는 객체 메서드 내에서 this를 상속하지 않기 때문에 this가 person 객체를 가리키지 않고, <br />
전역 스코프의 this를 가리킴. 따라서 this.name은 undefined가 됨

<br />

2. prototype

```js
function Person(name) {
  this.name = name;
}

Person.prototype.sayHello = () => {
  console.log(`Hello, ${this.name}`);
};

const person1 = new Person("Alice");

person1.sayHello(); // "Hello, undefined"
```

화살표 함수로 정의된 메소드를 prototype에 할당하는 경우도 동일하다.

<br />

3. 생성자 함수로 사용할 때

```js
const Foo = () => {
  this.bar = "baz";
};
const instance = new Foo(); // 에러 발생
```

생성자 함수는 prototype 프로퍼티를 가지며 prototype 프로퍼티가 가르키는 프로토타입 객체의 constructor을 사용한다. <br />
하지만 화살표 함수는 prototype 프로퍼티를 가지고 있지 않음

<br />
<br />
<br />

## 출처

> https://nykim.work/71

> https://sewonzzang.tistory.com/21
