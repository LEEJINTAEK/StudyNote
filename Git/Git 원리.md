# **๐Git ์๋ฆฌ** 

## Git?

- git์ด๋? ๋ฒ์  ๊ด๋ฆฌ ์์คํ์ผ๋ก ๋ณต์กํ ํ๋ก์ ํธ์ ์ฌ์ฉํ๊ธฐ์ ์ฉ์ดํ๋ค. 
- Backup, Recovery, Collaboration ๊ธฐ๋ฅ

<br  /><br  />

## ๋ถ์ ๋๊ตฌ 
`$pip install gistory (๋ถ์ ๋๊ตฌ ์ค์น)`
<br  />

- ํ์ผ์ ๋ด์ฉ: blob
- ๋๋ ํ ๋ฆฌ์ ํ์ผ ๋ช & ๋ด์ฉ๋ช์ ์ ๋ณด๋ฅผ ๋ด๋ ๊ณณ : tree
- commit : ๊ฐ๊ฐ์ id๋ฅผ ๊ฐ์ง๊ณ  ์๋ค. - hash์ ์ ๋ณด๋ก ํตํ์ฌ ์ ์ฅ๋๋ค.
<br />

<img width="549" alt="gistory" src="https://user-images.githubusercontent.com/109197023/209471325-e9559ba3-e923-4cc8-a241-280b962e801a.png">

<br  /><br  />

## ๋ธ๋ ์น ์ถฉ๋ 
<br  />

- ๊ฐ์ ํ์ผ์์ ๊ฐ์ ๊ณณ์ ์์ ํ๊ณ  ๋ณํฉ์ ํ๋ฉด ๋ฐ์
- git config --global merge.tool kdiff3 (๋ณํฉ์ ๋ฌธ์ ์ผ๋ก ํ๋ ํด) 

<br  /><br  />

## 2 way merge vs 3 way merge
<br />

![merge](https://user-images.githubusercontent.com/109197023/209471512-827139ad-1cd2-4329-b7c2-93c32f13649e.jpg)


<br  /><br  />

## pull vs fetch
<br  />

- **pull**์ ๋ค์ด๋ฐ๊ณ  ๋ณํฉ๊น์ง ๋ค ํด์ค๋ค.
- **fetch**๋ ์๊ฒฉ ์ ์ฅ์์ ๋ด์ฉ์ ํ์ธ๋ง ํ๊ณ  ๋ก์ปฌ ์ ์ฅ์์ ๋ณํฉ ํ๊ณ  ์ถ์ง ์์ ๋ ์ฌ์ฉํ๋ค.

<br  /><br  />

## revase vs merge 
<br  />

**merge**๋ ๋ณ๋ ฌ ๊ตฌ์กฐ์ด๋ฉฐ, ์ฝ๊ณ  ์์ ํ๋ค.
**revase**๋ ์ผ๋ ฌ ๊ตฌ์กฐ์ด๋ฉฐ, ํ์์ด ์๋๋ค. ํ์ง๋ง ์ด๋ ต๊ณ  ์ํํ๋ค.
<br />

![revase](https://user-images.githubusercontent.com/109197023/209471375-628cffbc-1445-4daa-bc2b-ada8432e6799.jpg)

<br  /><br  />

## tag
<br  />

- Annotated tag๋ ๋ง๋  ์ฌ๋์ ์ด๋ฆ, ์ด๋ฉ์ผ ๋ฑ๊ณผ ๊ฐ์ ๋ง์ ์ ๋ณด๋ฅผ ์ฃผ์์ผ๋ก ์ถ๊ฐํ  ์ ์๋ค. ex)git tag -a v0.2 -m 'jintaek'
- Lightweight tag๋ ๋จ์ํ๊ฒ ํน์  ์ปค๋ฐ์ ๋ํ ํฌ์ธํฐ์ด๋ค.
- git tag -d ํ๊ทธ ๋ฒ์  ํ์ธ,  git push --tags ์ ์ฅ์์ ์๋ฐ์ดํธ

<br  /><br  />

## git reset mode ์ฐจ์ด
<br />

![str](https://user-images.githubusercontent.com/109197023/209471515-c28cf610-6a0f-4a7f-82d3-2ed7f7951a11.jpg)

<br  /><br  />

## ์ฐธ๊ณ  ์๋ฃ

> https://www.youtube.com/watch?v=23V6_yZSmUY&t=80s

