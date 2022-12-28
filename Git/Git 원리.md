# **📚Git 원리** 

## Git?

- git이란? 버전 관리 시스템으로 복잡한 프로젝트에 사용하기에 용이하다. 
- Backup, Recovery, Collaboration 기능

<br  /><br  />

## 분석 도구 
`$pip install gistory (분석 도구 설치)`
<br  />

- 파일의 내용: blob
- 디렉토리의 파일 명 & 내용명에 정보를 담는 곳 : tree
- commit : 각각의 id를 가지고 있다. - hash의 정보로 통하여 저장된다.
<br />

<img width="549" alt="gistory" src="https://user-images.githubusercontent.com/109197023/209471325-e9559ba3-e923-4cc8-a241-280b962e801a.png">

<br  /><br  />

## 브렌치 충돌 
<br  />

- 같은 파일에서 같은 곳을 수정하고 병합을 하면 발생
- git config --global merge.tool kdiff3 (병합전문적으로 하는 툴) 

<br  /><br  />

## 2 way merge vs 3 way merge
<br />

![merge](https://user-images.githubusercontent.com/109197023/209471512-827139ad-1cd2-4329-b7c2-93c32f13649e.jpg)


<br  /><br  />

## pull vs fetch
<br  />

- **pull**은 다운받고 병합까지 다 해준다.
- **fetch**는 원격 저장소의 내용을 확인만 하고 로컬 저장소와 병합 하고 싶지 않을 때 사용한다.

<br  /><br  />

## revase vs merge 
<br  />

**merge**는 병렬 구조이며, 쉽고 안전하다.
**revase**는 일렬 구조이며, 파악이 잘된다. 하지만 어렵고 위험하다.
<br />

![revase](https://user-images.githubusercontent.com/109197023/209471375-628cffbc-1445-4daa-bc2b-ada8432e6799.jpg)

<br  /><br  />

## tag
<br  />

- Annotated tag는 만든 사람의 이름, 이메일 등과 같은 많은 정보를 주석으로 추가할 수 있다. ex)git tag -a v0.2 -m 'jintaek'
- Lightweight tag는 단순하게 특정 커밋에 대한 포인터이다.
- git tag -d 테그 버전 확인,  git push --tags 저장소에 업데이트

<br  /><br  />

## git reset mode 차이
<br />

![str](https://user-images.githubusercontent.com/109197023/209471515-c28cf610-6a0f-4a7f-82d3-2ed7f7951a11.jpg)

<br  /><br  />

## 참고 자료

> https://www.youtube.com/watch?v=23V6_yZSmUY&t=80s

