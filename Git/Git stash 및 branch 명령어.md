# **๐branch ๋ช๋ น์ด**

## ์ํ ํ์ธ
```bash
 $git branch 
``` 
## ์๋ก์ด ๋ธ๋์น
```bash
 $git branch newbranch 
``` 
## ๋ธ๋ ์น ๋ณ๊ฒฝ
```bash
 $git checkout newbranch 
``` 
## ๋ธ๋์น ์ ๋ณด ํ์ธ
```bash
 $git log --bracnshes --decorate --graph
``` 
## master์๋ ์๊ณ  newbranch์ ์๋๊ฒ ์ฐจ์ด ๋น๊ต
- -p ๋ถ์ด๋ฉด, ์์ค ์ฝ๋ ์ฐจ์ด๊น์ง ๋น๊ต

```bash
 $git log -p master..newbranch
``` 
## ์ปค๋ฐ ๋ฐ ์์ ํธ๋ฆฌ ๋ฑ์ ๋ณ๊ฒฝ ์ฌํญ ํ์
```bash
 $git diff master..newbranch 
``` 
## newbranch์ master๋ก ๋ณํฉ
- checkout์ master๋ก ํ๋ค์ ๋ช๋ น์ด ์๋ ฅ

```bash
 $git merge newbranch
``` 

<br />
<br />

# **๐stash ๋ช๋ น์ด**

## **stash๋?**
- ์์ ํ๋ ๊ฒ์ ์ด๋๊ฐ์ ์จ๊ฒจ๋์
- ์์ ์ด ๋ ๋๋ฌ๋๋ฐ ์ ์ฅํ๊ธฐ์ ๋ชจํธํ  ๋ ์ฌ์ฉ
- ๋ฒ์ ๊ด๋ฆฌ๊ฐ ๋๊ณ  ์๋ ํ์ผ์ ๋ํด์๋ง

<br />

## ์์ ๋๋ ํ ๋ฆฌ ์์์ค์ธ ๋ณ๊ฒฝ์ฌํญ๋ค์ด ์ธ์ด๋ธ, ํ์ฌ branch์
```bash
 $git stash 
``` 

## ์ต์  stash ๊ฐ์ ธ์ค๊ธฐ
```bash
 $git stash apply 
``` 

## ์ต์  stash ์ญ์ 
```bash
 $git stash drop  
``` 

## apply + drop
```bash
 $git stash pop 
``` 

## stash ๋ชจ๋ ์ง์ฐ๊ธฐ
```bash
 $git stash clear
``` 
