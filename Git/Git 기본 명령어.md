# **๐git ๊ธฐ๋ณธ ๋ช๋ น์ด**

## ๋ณ๊ฒฝ์ฌํญ ์ถ์ , ๋ฒ์ ๊ด๋ฆฌ ์์
```bash
 $git init
``` 
## ๊ฐํ ๋ฌธ์ ์ค์  
```bash
 $git config --global core.autocrlf true 
``` 
## ์ ๋ณด ๋ฑ๋ก
 ```bash
 $git config --global user.name 'gitname' 
 $git config --global user.email '๊น๋ฉ์ผ'
 ```

## ๊ตฌ์ฑ ํ์ธ
 ```bash
 $git config --global --list 
 ```

## ์ํ ํ์ธ
 ```bash
 $git status 
 ```

## ๋ณ๊ฒฝ์ฌํญ์ ์ถ์ ํ  ํน์  ํ์ผ์ ์ง์ 
 ```bash
 $git add .
 ```

## ๋ฉ์ธ์ง(-m)์ ํจ๊ป ๋ฒ์ ์ ์์ฑ
 ```bash
 $git commit -m 'Start project' 
 ```

## ์ญ์ฌ ํ์ธ 
- git log -p ์ฐจ์ด์ ๊น์ง ๋ณด์ฌ์ค๋ค

 ```bash
 $git log 
 ```

## origin์ด๋ ๋ณ์นญ์ผ๋ก ์๊ฒฉ ์ ์ฅ์๋ฅผ ์ฐ๊ฒฐ
- `$git remote remove origin ์ญ์ ` 

 ```bash
 $git remote add origin ์ ์ฅ์ ์ฃผ์ 
 ```

## origin์ด๋ ๋ณ์นญ์ ์๊ฒฉ ์ ์ฅ์๋ก ๋ฒ์  ๋ด์ญ ์ ์ก
- `$git push origin +master ๊ฐ์  ํธ์ฌ` 

 ```bash
 $git push -u origin master   
 ```

## ์์ ๋ณต์ 
 ```bash
 $git clone  ๊น์ฃผ์ ๋๋ ํ ๋ฆฌ
 ```

## ์๊ฒฉ์์ ๋ก๊ฑธ๋ก ๊ฐ์ ธ์ค๊ธฐ
 ```bash
 $git pull origin master 
 ```

## ์์ ์  ํ์ ์ฐจ์ด์ ์ ๋ณด๊ธฐ 
 ```bash
 $git diff (commit(๋ฒํธ) commit(๋ฒํธ)) 
 ```

## ํด๋น์ปค๋ฐ์ผ๋ก ๋์๊ฐ๊ธฐ
- ์์ ์์ ๋ณธ ์ญ์  (๊ณต์ ํ๊ธฐ ์ ์)
- hard,soft,mixed์ ์ฐจ์ด๊ฐ ์๋ค

 ```bash
 $git reset --(hard) commit(๋ฒํธ) 
 ```

## ๋ฆฌ์ ์ทจ์
- hard,soft,mixed์ ์ฐจ์ด๊ฐ ์๋ค

 ```bash
 $git reset --(hard) ORIG_HEAD 
 ```

## ๊ธฐํ 
```plaintext
pwd ํ์ฌ์์น ํ์ธ 
cd ์ด๋ 
mkdir ํด๋์์ฑ
ls -al ํ์ฌํ์ผ๋ชฉ๋ก
vim f1.txt (ํ์ผ ์์ฑ) -> i ๋๋ฅด๋ฉด ์๋ ฅ๊ฐ๋ฅ -> ESC ๋๋ฅด๋ฉด ์๋ ฅ์ข๋ฃ -> :wq ์ ์ฅ 
cat f1.txt (ํ์ผ ๋ด์ฉ๋ณด๊ธฐ)
cp f1.txt f2.txt (์นดํผ)
์ฉ์ด- stage-> (์ปค๋ฐ๋๊ธฐํ๋ ์ ๋ค์ด ๊ฐ๋๊ณณ)
```


