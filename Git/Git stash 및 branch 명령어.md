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

<br />

- git stash apply 명령은 가장 최근에 저장한 stash를 현재 작업 트리에 적용한다. 이때 stash는 삭제되지 않는다.
- 따라서 git stash apply 명령으로 stash를 적용한 후, 다시 적용하지 않고 남겨둘 경우 git stash drop 명령으로 stash를 삭제해야 한다. <br />

```bash
 $git stash apply
```

## 최신 stash 삭제

```bash
 $git stash drop
```

## pop

- git stash pop 명령도 가장 최근에 저장한 stash를 현재 작업 트리에 적용합니다. 이때 stash는 apply와 달리 삭제됩니다. 따라서 pop 명령으로 stash를 적용한 경우 별도의 drop 명령이 필요하지 않습니다.

```bash
 $git stash pop
```

## stash 모두 지우기

```bash
 $git stash clear
```
