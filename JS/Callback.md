# πμ½λ°±ν¨μ

<br />

## μ½λ°± ν¨μλ?

<img width="500" alt="μ½λ°±ν¨μ" src="https://user-images.githubusercontent.com/109197023/212049790-900f1ca2-8e88-4e20-aaed-c53ade470df3.PNG">

<br />

1. λ€λ₯Έ κ³³μ ν¨μλ₯Ό λ§λ€μ΄μ λ°λ‘ ν¨μλͺμ μ½λ°±ν¨μλ‘ λ£μ΄λ λ¨
1. μ½λ°±ν¨μμ ν¨μλͺ μλͺ κ°λ₯
1. μ½λ°±ν¨μκ° νμν ν¨μμλ§ κ°λ₯

<br />
<br />

## μμ

<br />

```javascript
function first(νλΌλ―Έν°) {
  console.log;
  νλΌλ―Έν°();
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
  print(); //λ¨Όμ  νΈμ΄μ€ν λκ³ 
}
printImmediately(() => console.log("hi"));
```

<br />

```javascript
//2. asynchronous callback
function printDelay(print, timeout) {
  setTimeout(print, timeout); //νΈμ΄μ€ν
}
printDelay(() => console.log("hi"), 2000);
```

<br />

- νμν  λ μ¬μ©
- λ¨μ΄ μ΄ ν¨μλ₯Ό νμλ€μ΄ μμ£Ό μ¬μ©ν  λ
- μμ μ  μμ°¨μ 

<br />
<br />

## μ½λ°±μ§μ₯

<br />

<img width="500" alt="μ½λ°±μ§μ₯" src="https://user-images.githubusercontent.com/109197023/212053742-19da1bfd-252a-404b-b0fa-9e802aac123a.PNG">

<br />

### μ½λ°±μ§μ₯ μμ 

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
const id = prompt("μλ ₯");
const pass = prompt("μλ ₯");
userstage.login(
  id,
  pass,
  (user) => {
    userstage.getRoles(
      user,
      (userWithRole) => {
        alert(`hi ${userWithRole.name}λ, ${userWithRole.role}`);
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

### **μ½λ°± μ§μ₯μ λΉ μ§κ² λλ€λ©΄??**

<br />

- κ°λμ± νλ½
- λλ²κΉ μ μ΄λ €μ
- μ μ§λ³΄μ μ΄λ €μ

<br />

### **μ½λ°±μ§μ₯ νμΆνκΈ°**

<br />

- [Promiseπ](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [Async awaitπ](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/async_function)

<br />

### **Promiseλ₯Ό μ΄μ©ν μ½λ°± μ§μ₯ μμ  νμΆ**

[μ½λ°±μ§μ₯μμ  π](#μ½λ°±μ§μ₯-μμ )

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
const id = prompt("μλ ₯");
const pass = prompt("μλ ₯");

userstage
  .login(id, pass)
  .then(userstage.getRoles)
  .then((user) => alert(`hi ${user.name}λ, ${user.role}`))
  .catch(console.log);
```

<br/>
<br/>

## μΆμ²

> https://www.youtube.com/watch?v=s1vpVCrT8f4&list=PLv2d7VI9OotTVOL4QmPfvJWPJvkmv6h-2&index=11

> https://www.youtube.com/watch?v=-iZlNnTGotk
