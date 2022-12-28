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





