# **📚branch 명령어**

## 상태 확인
```bash
 $git branch 
``` 
## 새로운 브랜치
```bash
 $git branch newbranch 
``` 
## 브렌치 변경
```bash
 $git checkout newbranch 
``` 
## 브랜치 정보 확인
```bash
 $git log --bracnshes --decorate --graph
``` 
## master에는 없고 newbranch에 있는것 차이 비교
- -p 붙이면, 소스 코드 차이까지 비교

```bash
 $git log -p master..newbranch
``` 
## 커밋 및 작업 트리 등의 변경 사항 표시
```bash
 $git diff master..newbranch 
``` 
## newbranch을 master로 병합
- checkout을 master로 한다음 명령어 입력

```bash
 $git merge newbranch
``` 

<br />
<br />

# **📚stash 명령어**

## **stash란?**
- 작업 했던 것을 어딘가에 숨겨놓음
- 수정이 덜 끝났는데 저장하기에 모호할 때 사용
- 버전관리가 되고 있는 파일에 대해서만

<br />

## 작업 디렉토리 작업중인 변경사항들이 세이브, 현재 branch에
```bash
 $git stash 
``` 

## 최신 stash 가져오기
```bash
 $git stash apply 
``` 

## 최신 stash 삭제
```bash
 $git stash drop  
``` 

## apply + drop
```bash
 $git stash pop 
``` 

## stash 모두 지우기
```bash
 $git stash clear
``` 

# **📚branch 명령어**

## 상태 확인
```bash
 $git branch 
``` 
## 새로운 브랜치
```bash
 $git branch newbranch 
``` 
## 브렌치 변경
```bash
 $git checkout newbranch 
``` 
## 브랜치 정보 확인
```bash
 $git log --bracnshes --decorate --graph
``` 
## master에는 없고 newbranch에 있는것 차이 비교
- -p 붙이면, 소스 코드 차이까지 비교

```bash
 $git log -p master..newbranch
``` 
## 커밋 및 작업 트리 등의 변경 사항 표시
```bash
 $git diff master..newbranch 
``` 
## newbranch을 master로 병합
- checkout을 master로 한다음 명령어 입력

```bash
 $git merge newbranch
``` 
