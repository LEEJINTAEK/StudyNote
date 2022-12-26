# **stash 명령어**

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