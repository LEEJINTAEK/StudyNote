# **📚Git Commit Convention**

<br />

## 목차

1. [**commit Convention??**](#commit-convention)
1. [**메세지 구조**](#메세지-구조)
1. [**제목 작성 방법**](#제목-작성-방법)
1. [**본문 작성 방법**](#본문-작성-방법)
1. [**꼬리말 작성 방법**](#꼬리말-작성-방법)
1. [**결과 예시 참조**](#결과-예시-참조)
1. [**Commit Message Emoji**](#commit-message-emoji)
1. [**마무리**](#마무리)

<br />
<br />

## **Commit Convention??**

- 엉터리 Commit Message가 누적된다면?
    - 가독성이 떨어짐
    - 여러 사람과 개발을 같이 할 때 문제 발생 가능 
    - 코드 유지보수의 어려움 발생

<br />

- 협업하는 사람들 간의 Commit Message 스타일을 정해두면?
    - 서로 간의 코드 리뷰에 도움
    - 자신의 이전 로그 탐색 가능

<br />
<br />

## **메세지 구조**

`제목, 본문, 꼬리말 세 가지 파트로 나눈다.`

```plaintext
type(옵션): [#issueNumber - ]Subject  // -> 제목
(한 줄을 띄워 분리합니다.)
body(옵션) //  -> 본문 
(한 줄을 띄워 분리합니다.)
footer(옵션) // -> 꼬리말
```
-  type  
    - 태그와 제목으로 구성
    - 태그는 영어로 쓰고, 첫 문자는 대문자로 표기
    - 어떤 의도로 커밋했는지를 type에 
- subject  
    - 최대 50글자가 넘지 않도록 한다.
    - 영문으로 표기하는 경우 동사(원형)를 가장 앞에 두고 첫 글자는 대문자로 표기 
- body 
    - 긴 설명이 필요한 경우에 작성
    - 어떻게 했는지가 아니라, 무엇을 왜 했는지를 작성
    - 최대 75자를 넘기지 않도록 합니다. 
- footer 
    - issue tracker ID를 명시하고 싶은 경우에 작성

<br />
<br />

## **제목 작성 방법** 
<br />

### **Rule**

1. 제목의 처음은 동사 원형으로 시작
1. 총 글자 수는 50자 이내로 작성
1. 마지막에 특수문자는 삽입하지 않음 ex) ., ! , ?
1. 제목은 개조식 구문으로 작성
 

**영어로 작성하는 경우**

1. 첫 글자는 대문자로 작성
1. **"Fix", "Add", "Change"의 명령어**로 시작합니다.
 

**한글로 제목을 작성하는 경우**

1. **"고침", "추가", "변경"의 명령어**로 시작합니다.
 
```plaintext
Feat: "추가 get data api 함수"
```

<br />
<br />

### **타입**
`'태그:(space)제목'의 형태`

태그 이름 | 설명 
:--|:--
Feat | 새로운 기능을 추가할 경우  
Fix | 버그를 고친 경우   
Design | CSS 등 사용자 UI 디자인 변경  
!BREAKING CHANGE | 커다란 API 변경의 경우
!HOTFIX	| 급하게 치명적인 버그를 고쳐야하는 경우
Style | 코드 포맷 변경, 세미 콜론 누락, 코드 수정이 없는 경우
Refactor | 프로덕션 코드 리팩토링
Comment	| 필요한 주석 추가 및 변경
Docs | 문서를 수정한 경우
Test | 테스트 추가, 테스트 리팩토링(프로덕션 코드 변경 X)
Chore | 빌드 테스트 업데이트, 패키지 매니저를 설정하는 경우(프로덕션 코드 변경 X)
Rename | 파일 혹은 폴더명을 수정하거나 옮기는 작업만인 경우
Remove | 파일을 삭제하는 작업만 수행한 경우

<br />
<br />

### **태그 작성 방법**
<br />

1. **기능**

`Feat, Fix, Design, !BREAKING CHANGE 태그가 기능 태그의 종류`

```plaintext
Feat: 새로운 기능을 추가할 경우
Fix: 버그를 고친 경우
Design: CSS 등 사용자 UI 디자인 변경
!BREAKING CHANGE: 커다란 API 변경의 경우 (ex API의 arguments, return 값의 변경, DB 테이블 변경, 급하게 치명적인 버그를 고쳐야 하는 경우)
``` 

`추가적인 문맥 정보를 제공하기 위한 목적으로 괄호 안에 적을 수도 있다`

```plaintext
ex)
"Feat(navigation): "
"Fix(database): "
```
<br />
<br />

2. **개선**

`Style, Refactor, Comment 태그가 개선 태그의 종류`

- Style의 경우 오타 수정, 탭 사이즈 변경, 변수명 변경 등에 해당 
- Refactor의 경우 코드를 리팩토링 하는 경우에 적용할 수 있음

```plaintext
Style: 코드 포맷 변경, 세미 콜론 누락, 코드 수정이 없는 경우
Refactor: 프로덕션 코드 리팩토링, 새로운 기능이나 버그 수정없이 현재 구현을 개선한 경우
Comment: 필요한 주석 추가 및 변경
```
<br />
<br />

3. **그 외**

`Docs, Test, Chore, Rename, Remove 태그가 그 외 태그의 종류`

- Docs의 경우 README.md 수정 등에 해당
- Test는 test 폴더 내부의 변경이 일어난 경우에만 해당
- Chore의 경우 package.json의 변경이나 dotenv의 요소 변경 등, 모듈의 변경에 해당 


```plaintext
Docs: 문서를 수정한 경우
Test: 테스트 추가, 테스트 리팩토링 (프로덕션 코드 변경 없음)
Chore: 빌드 태스크 업데이트, 패키지 매니저 설정할 경우 (프로덕션 코드 변경 없음)
Rename: 파일 혹은 폴더명을 수정하는 경우
Remove: 사용하지 않는 파일 혹은 폴더를 삭제하는 경우
``` 

<br />
<br />

## **본문 작성 방법**

### **Rule**

1. 본문은 한 줄 당 72자 내로 작성
1. 본문 내용은 양에 구애받지 않고 최대한 상세히 작성
1. 본문 내용은 어떻게 변경했는지 보다 무엇을 변경했는지 또는 왜 변경했는지를 설명

<br />
<br />
 
## **꼬리말 작성 방법**

### **Rule**

1. 꼬리말은 optional이고 이슈 트래커 ID를 작성
1. 꼬리말은 "유형: #이슈 번호" 형식
1. 여러 개의 이슈 번호를 적을 때는 쉼표로 구분
1. 이슈 트래커 유형은 다음 중 하나를 사용
    - Fixes: 이슈 수정중 (아직 해결되지 않은 경우)
    - Resolves: 이슈를 해결했을 때 사용
    - Ref: 참고할 이슈가 있을 때 사용
    - Related to: 해당 커밋에 관련된 이슈번호 (아직 해결되지 않은 경우)

```plaintext    
ex) Fixes: #45 Related to: #34, #23
```

<br />
<br />

## **결과 예시 참조**

```plaintext
Feat: "추가 로그인 함수"

로그인 API 개발

Resolves: #123
Ref: #456
Related to: #48, #45
```
<br />
<br />

## **Commit Message Emoji**

<br />

Emoji | 설명
:--|:--       
🎨 | 코드의 형식 / 구조를 개선 할 때
📰 | 새 파일을 만들 때
📝 | 사소한 코드 또는 언어를 변경할 때
🐎 | 성능을 향상시킬 때
📚 | 문서를 쓸 때
🐛 | 버그 reporting할 때, @FIXME 주석 태그 삽입
🚑 | 버그를 고칠 때
🐧 | 리눅스에서 무언가를 고칠 때
🍎 | Mac OS에서 무언가를 고칠 때
🏁 | Windows에서 무언가를 고칠 때
🔥 | 코드 또는 파일 제거할 때 , @CHANGED주석 태그와 함께
🚜 | 파일 구조를 변경할 때 . 🎨과 함께 사용
🔨 | 코드를 리팩토링 할 때
☔️ | 테스트를 추가 할 때
🔬 | 코드 범위를 추가 할 때
💚 | CI 빌드를 고칠 때
🔒 | 보안을 다룰 때
⬆️ | 종속성을 업그레이드 할 때
⬇️ | 종속성을 다운 그레이드 할 때
⏩ | 이전 버전 / 지점에서 기능을 전달할 때
⏪ | 최신 버전 / 지점에서 기능을 백 포트 할 때
👕 | linter / strict / deprecation 경고를 제거 할 때
💄 | UI / style 개선시
♿️ | 접근성을 향상시킬 때
🚧 | WIP (진행중인 작업)에 커밋, @REVIEW주석 태그와 함께 사용
💎 | New Release
🔖 | 버전 태그
🎉 | Initial Commit
🔈 | 로깅을 추가 할 때
🔇 | 로깅을 줄일 때
✨ | 새로운 기능을 소개 할 때
⚡️ | 도입 할 때 이전 버전과 호환되지 않는 특징, @CHANGED주석 태그 사용
💡 | 새로운 아이디어, @IDEA주석 태그
🚀 | 배포 / 개발 작업 과 관련된 모든 것
🐘 | PostgreSQL 데이터베이스 별 (마이그레이션, 스크립트, 확장 등)
🐬 | MySQL 데이터베이스 특정 (마이그레이션, 스크립트, 확장 등)
🍃 | MongoDB 데이터베이스 특정 (마이그레이션, 스크립트, 확장 등)
🏦 | 일반 데이터베이스 별 (마이그레이션, 스크립트, 확장명 등)
🐳 | 도커 구성
🤝 | 파일을 병합 할 때

<br />

### 첫번째 방법

- Emoji text value 보기 + 사용

> https://www.webfx.com/tools/emoji-cheat-sheet/

### 두번째 방법

- gitmoji 설치 자동입력

> https://gitmoji.dev/

```bash
$ npm i -g gitmogi-cli
```

```bash
$ gitmoji -c
```
<br />
<br />

## 마무리 

### Git Commit Message 작성을 위한 Rule

```plaintext
1. 제목과 본문을 한 줄 띄워 분리하기
2. 제목은 영문 기준 50자 이내로
3. 제목 첫글자를 대문자로
4. 제목 끝에 . 금지
5. 제목은 명령조로
6. 본문은 영문 기준 72자마다 줄 바꾸기
7. 본문은 어떻게보다 무엇을, 왜에 맞춰 작성하기
```
<br />
<br />

## 참고 자료 

> https://overcome-the-limits.tistory.com/entry/%ED%98%91%EC%97%85-%ED%98%91%EC%97%85%EC%9D%84-%EC%9C%84%ED%95%9C-%EA%B8%B0%EB%B3%B8%EC%A0%81%EC%9D%B8-git-%EC%BB%A4%EB%B0%8B%EC%BB%A8%EB%B2%A4%EC%85%98-%EC%84%A4%EC%A0%95%ED%95%98%EA%B8%B0#%EC%BB%A4%EB%B0%8B-%EB%A9%94%EC%8B%9C%EC%A7%80-emoji

> https://somjang.tistory.com/entry/GitHub-commit-%EB%A9%94%EC%84%B8%EC%A7%80%EC%97%90-%EC%9D%B4%EB%AA%A8%ED%8B%B0%EC%BD%98-%EB%84%A3%EB%8A%94-%EB%B0%A9%EB%B2%95-%F0%9F%A4%A9

> https://meetup.nhncloud.com/posts/106