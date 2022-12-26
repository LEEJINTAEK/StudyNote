# **git 기본 명령어**

## 변경사항 추적, 버전관리 시작
```bash
 $git init
``` 
## 개행 문자 설정 
```bash
 $git config --global core.autocrlf true 
``` 
## 정보 등록
 ```bash
 $git config --global user.name 'gitname' 
 $git config --global user.email '깃메일'
 ```

## 구성 확인
 ```bash
 $git config --global --list 
 ```

## 상태 확인
 ```bash
 $git status 
 ```

## 변경사항을 추적할 특정 파일을 지정
 ```bash
 $git add .
 ```

## 메세지(-m)와 함께 버전을 생성
 ```bash
 $git commit -m 'Start project' 
 ```

## 역사 확인 
- git log -p 차이점까지 보여준다

 ```bash
 $git log 
 ```

## origin 이란 별칭으로 원경 저장소를 연결
- git remote remove origin 삭제 

 ```bash
 $git remote add origin eesskk9909@gmail.com   
 ```

## origin이란 별칭의 원격 저장소로 버전 내역 전송
- `$git push origin +master 강제 푸쉬` 

 ```bash
 $git push -u origin master   
 ```

## 작업 복제
 ```bash
 $git clone  깃주소 디렉토리
 ```

## 원격에서 로걸로 가져오기
 ```bash
 $git pull origin master 
 ```

## 작업 전 후의 차이점을 보기 
 ```bash
 $git diff (commit(번호) commit(번호)) 
 ```

## 해당커밋으로 돌아가기
- 앞에 수정본 삭제 (공유하기 전에)
- hard,soft,mixed의 차이가 있다

 ```bash
 $git reset --(hard) commit(번호) 
 ```

## 리셋 취소
- hard,soft,mixed의 차이가 있다

 ```bash
 $git reset --(hard) ORIG_HEAD 
 ```

## 기타 
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


