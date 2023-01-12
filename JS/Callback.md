# 📗콜백함수

<br />

## 콜백 함수란?

<img width="500" alt="콜백함수" src="https://user-images.githubusercontent.com/109197023/212049790-900f1ca2-8e88-4e20-aaed-c53ade470df3.PNG">

<br />

1. 다른 곳에 함수를 만들어서 바로 함수명을 콜백함수로 넣어도 됨
1. 콜백함수에 함수명 작명 가능
1. 콜백함수가 필요한 함수에만 가능

<br />
<br />

## 예시

<br />

```javascript
function first(파라미터) {
  console.log;
  파라미터();
}
function second() {
  console.log;
}
first(second);
```

<br />

```javascript
//1. synchronous callback
function printImmediately(print) {
  print(); //먼저 호이스팅 되고
}
printImmediately(() => console.log("hi"));
```

<br />

```javascript
//2. asynchronous callback
function printDelay(print, timeout) {
  setTimeout(print, timeout); //호이스팅
}
printDelay(() => console.log("hi"), 2000);
```

<br />

- 협업할 때 사용
- 남이 쓴 함수를 팀원들이 자주 사용할 때
- 안정적 순차적

<br />
<br />

## 콜백지옥

<br />

<img width="500" alt="콜백지옥" src="https://user-images.githubusercontent.com/109197023/212053742-19da1bfd-252a-404b-b0fa-9e802aac123a.PNG">

<br />

### 콜백지옥 예제

<br />

```javascript
class UserStage {
  login(id, pass, suc, err) {
    setTimeout(() => {
      if (id === "ee" && pass === "1234") {
        suc(id);
      } else {
        err(new Error("not"));
      }
    }, 2000);
  }
  getRoles(user, suc, err) {
    setTimeout(() => {
      if (user === "ee") {
        suc({ name: "ee", role: "admin" });
      } else {
        err(new Error("no"));
      }
    }, 1000);
  }
}

const userstage = new UserStage();
const id = prompt("입력");
const pass = prompt("입력");
userstage.login(
  id,
  pass,
  (user) => {
    userstage.getRoles(
      user,
      (userWithRole) => {
        alert(`hi ${userWithRole.name}님, ${userWithRole.role}`);
      },
      (err) => {
        console.log(err);
      }
    );
  },
  (err) => {
    console.log(err);
  }
);
```

<br />

### **콜백 지옥에 빠지게 된다면??**

<br />

- 가독성 하락
- 디버깅 시 어려움
- 유지보수 어려움

<br />

### **콜백지옥 탈출하기**

<br />

- [Promise👈](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [Async await👈](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/async_function)

<br />

### **Promise를 이용한 콜백 지옥 예제 탈출**

[콜백지옥예제 👈](#콜백지옥-예제)

<br />

```javascript
class UserStage {
  login(id, pass) {
    return new Promise((resolve, reject) => {
      //promise
      setTimeout(() => {
        if (id === "ee" && pass === "1234") {
          resolve(id);
        } else {
          reject(new Error("not"));
        }
      }, 2000);
    });
  }
  getRoles(user) {
    return new Promise((resolve, reject) => {
      //promise
      setTimeout(() => {
        if (user === "ee") {
          resolve({ name: "ee", role: "admin" });
        } else {
          reject(new Error("no"));
        }
      }, 1000);
    });
  }
}

const userstage = new UserStage();
const id = prompt("입력");
const pass = prompt("입력");

userstage
  .login(id, pass)
  .then(userstage.getRoles)
  .then((user) => alert(`hi ${user.name}님, ${user.role}`))
  .catch(console.log);
```

<br/>
<br/>

## 출처

> https://www.youtube.com/watch?v=s1vpVCrT8f4&list=PLv2d7VI9OotTVOL4QmPfvJWPJvkmv6h-2&index=11

> https://www.youtube.com/watch?v=-iZlNnTGotk
