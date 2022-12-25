# Git 명령어 및 원리 공부
`git이란? 버전 관리 시스템으로 복잡한 프로젝트에 사용하기에 용이하다. Backup, Recovery, Collaboration 기능`
<br />

<details>
<summary>git bash 명령어</summary>
<br />

1. 명령어
    1. [**기본**](#1기본)
    1. [**branch**](#2branch)
    1. [**stash**](#3stash)
    1. [**기타**](#4기타)
<br />

**1.기본**

-------------

## git init 
변경사항 추적, 버전관리 시작
## git config --global core.autocrlf true 
개행 문자 설정 
## 정보 등록
 ```bash
 $git config --global user.name 'gitname' 
 $git config --global user.email '깃메일'
 ```    
## git config --global --list   
구성확인
## git status
상태확인
## git add 파일       
변경사항을 추적할 특정 파일을 지정 ex) add index.html
## git commit -m 'Start project'   
메세지(-m)와 함께 버전을 생성
## git log    
역사확인 (# git log -p 차이점까지 보여준다.)
## git remote add origin 깃주소   
origin 이란 별칭으로 원경 저장소를 연결
(git remote remove origin 삭제) 
## git push -u origin master   
origin이란 별칭의 원격 저장소로 버전 내역 전송
(다음부터 그냥 git push만 해도 된다.)
## git clone  깃주소 디렉토리
작업 복제
## git pull origin master 
원격에서 로걸로 가져오는
## git diff (commit(번호) commit(번호)) 
작업 전 후의 차이점을 보기위해 
## git reset --(hard) commit(번호) 
해당커밋으로 돌아감(앞에 수정본 삭제) (공유하기 전에)
## git reset --(hard) ORIG_HEAD 리셋 취소
hard,soft,mixed의 차이가 있다.

-------------------
<br />

**2.branch**

--------------------

## git branch 
상태 확인
## git branch 브랜치명 
새로운 브랜치(마스터 말고 다른)
## git checkout name 
name으로 작업
## git log --bracnshes --decorate --graph 
브랜치 정보 확인
## git log -p master..name 
master에는 없고 name에 있는것 차이 비교(-p는 소스코드차이까지)
## git diff master..name 
## git merge name 
checkout을 master로 한다음 명령어 입력하면 name을 master로 불러옴

------------------------
<br />

**3.stash**

-----------

- 작업 했던 것을 어딘가에 숨겨놓음
- 수정이 덜 끝났는데.. 저장하기에 모호할 때
- 버전관리가 되고있는 파일에 대해서만
<br />

## git stash 
작업 디렉토리 작업중인 변경사항들이 세이브, 현재 branch에
## git stash --help 
여러 도움말
## git stash apply 
다시 살아남
## git stash drop 
최신 stash 삭제
## git stash pop 
apply + drop

--------------------
<br />

**4.기타**

--------------

```plaintext
pwd 현재위치 확인 
cd 이동 
mkdir 폴더생성
ls -al 현재파일목록
vim f1.txt (파일 생성) -> i 누르면 입력가능 -> ESC 누르면 입력종료 -> :wq 저장 
cat f1.txt (파일 내용보기)
cp f1.txt f2.txt (카피)
용어- stage-> (커밋대기하는 애들이 가는곳)
```
<br/>


<details>
<summary>간단한 원리</summary>
<br />

## 분석 도구 
pip install gistory (분석 도구 설치)
1) 파일의 내용: blob
2) 디렉토리의 파일 명 & 내용명에 정보를 담는 곳 : tree
3) commit : 각각의 id를 가지고 있다. - hash의 정보로 통하여 저장된다.
<img src="./git/gitimage/gistory.png" />

## 브렌치 충돌 
같은 파일에서 같은 곳을 수정하고 병합을 하면 발생
git config --global merge.tool kdiff3 (병합전문적으로 하는 툴) 

## 2 way merge vs 3 way merge
<img src="./git/gitimage/merge.jpg" />

## pull vs fetch
`**pull**은 다운받고 병합까지 다 해준다.`
`**fetch**는 원격 저장소의 내용을 확인만 하고 로컬 저장소와 병합 하고 싶지 않을 때 사용한다.**`

## revase vs merge 
`**merge**는 병렬 구조이며, 쉽고 안전하다.`
`**revase**는 일렬 구조이며, 파악이 잘된다. 하지만 어렵고 위험하다.`
<img src="./git/gitimage/revase.jpg" />

## tag
`Annotated tag는 만든 사람의 이름, 이메일 등과 같은 많은 정보를 주석으로 추가할 수 있다. ex)git tag -a v0.2 -m 'jintaek'`
`Lightweight tag는 단순하게 특정 커밋에 대한 포인터이다.`
`git tag -d 테그 버전 확인,  git push --tags 저장소에 업데이트`

## git reset mode 차이
<img src="./git/gitimage/str.jpg>

<br />

--------
[출처](https://www.youtube.com/watch?v=23V6_yZSmUY&t=80s)

