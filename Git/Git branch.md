# **📚branch 전략**

<br />

## 목차 

1. [**Git branch 전략이란?**](#git-bracnh-전략이란)
1. [**Git-flow 전략**](#git-flow-전략)
1. [**Git-flow 이용**](#git-flow-이용)
1. [**Github-flow 전략**](#github-flow-전략)
1. [**Github-flow 이용**](#github-flow-이용)

## **Git bracnh 전략이란?**

**브랜치 생성에 규칙을 만들어서 협업을 유연하게 하는 방법론** <br />
- 여러 개발자가 하나의 저장소를 사용하는 환경에서 저장소를 효과적으로 활용하기 위한 **work-flow**
- 브랜치의 생성, 삭제, 병합 등 git의 유연한 구조를 활용해서, 각 개발자들의 혼란을 최대한 줄이며 다양한 방식으로 소스를 관리하는 역할

## **Git-flow 전략**

<br />

![gitflow](https://user-images.githubusercontent.com/109197023/209947316-40696c29-9e79-4395-8d32-65e7929082ce.PNG)

<br />

- feature > develop > release > hotfix > master
- 왼쪽으로 갈수록 포괄적인 가지
- master branch를 병합할 경우 왼쪽에 있는 hotfix 등 모든 가지들에 있는 커밋들도 병합하도록 구성
- 항시 유지되는 **메인 브랜치 master, develop** 
- merge 되면 사라지는 **보조 브랜치 feature, release, hotfix**
- 브랜치들 간 merge할 때 "--no-ff"를 사용하여 기록을 그룹화
    - merge commit 생성하여 해당 브랜치 존재 정보를 남길 수 있음
    - commit기록을 되돌리기 편해짐


<br />

### Git-flow 구조 

<br />

![gitflow구조](https://user-images.githubusercontent.com/109197023/209948585-d101004e-1a73-448d-ab5b-d3f0571c96a2.PNG)

```plaintext
master: 라이브 서버에 제품으로 출시되는 브랜치 
develop: 다음 출시 버전을 대비하여 개발하는 브랜치
feature: 추가 기능 개발 브랜치 (develop 브랜치에 들어간다)
release: 다음 버전 출시를 준비하는 브랜치 (develop 브랜치를 release 브랜치로 옮긴 후 QA, 테스트를 진행하고 master 브랜치로 합친다)
hotfix: master 브랜치에서 발생한 버그를 수정하는 브랜치 
```

<br />

### 메인 브랜치 
`mater 브랜치와 develop 브랜치`

- **master 브랜치는** 배포 가능한 상태만을 관리하는 브랜치 
- **develop 브랜치는** 다음에 배포할 것을 개발하는 브랜치 
- develop 브랜치는 통합 브랜치의 역할을 하고, 평소에는 이 브랜치 기반으로 개발 진행

<br />

### 보조 브랜치 
`feature 브랜치(topic 브랜치)`

<br />

![feature브랜치](https://user-images.githubusercontent.com/109197023/209951481-8928e8da-d5da-4148-8fe6-c7cdc01e29de.PNG)

```plaintext
가지가 뻗어 나오는 곳:develop
뻗어나갔던 가지가 다시 합쳐지는 곳: develop
이름 설정: master, develop, release-*, hotfix-* 를 제외하고 자유롭게 이름 설정 가능 
새로운 기능을 추가할 때 주로 사용
```

<br/>

- 보조 브랜치는 기능을 다 완성할 때까지 유지하고, 다 완성되면 develop 브랜치로 merge, 결과가 좋지 않으면 discard
- 보조 브랜치는 보통 개발자 저장소에만 존재 
- origin에는 push하지 않음

<br />

### 릴리즈 브랜치 
`release 브랜치`

<br />

```plaintext
이름 설정: release-*
새로운 제품을 배포하고자 할 떄 사용하는 가지 
```

- 배포를 위한 최종적인 버그 수정 등의 개발을 수행하는 브랜치 
- develop 브랜치에 버전에 포함되는 기능이 merge 되었다면, QA를 위해 develop 브랜치에서 release 브랜치 생성
- 배포 가능한 상태가 되면 master 브랜치로 병합 후, 출시된 master 브랜치에 버전 태그 (v1.0 v2.0....)추가
- release 브랜치에서 기능을 점검하며 발견한 버그 수성 사항은 develop 브랜치에도 적용 
- 배포 완료 후 develop 브랜치에도 merge 작업 수행해야 함

<br />

### 핫픽스 브랜치 
`hotfix 브랜치`

<br />

```plaintext
이름 설정: hotfix-*
- 제품에서 버그가 발생했을 경우, 처리를 위해 이 가지로 해당 정보들을 모아둠
- 버그 수정 완료 후에 develop, master에 바로 반영, tag를 통해 관련 정보 기록
```

- hotfix는 버그를 고치기 위해 생성되는 가지, 따라서 버그 해결 후에 제거됨
- 다른 이가 버그 잡는 동안에도 develop 브랜치에서 작업 가능 
- hotfix 브랜치에서 변경 사항은 develop 브랜치에도 merge 하여 문제가 되는 부분을 처리해줘야 함
- release 가지가 생성되어 관리되고 있는 상태면, 해당 가지에 hotfix 정보를 병합(다음 배포 시 반영이 정상적으로 이루어지도록)

<br />

## Git flow 이용

```plaintext
- mater, develop 모두 운용
- 나머지 브랜치는 사용하지 않으면, 활용할 상황에만 만들어 사용 가능
- 대부분 작업은 develop에서 취합
- 테스트를 통해 확실하게 변동사항이 없을 때 master로의 병합 
- master가 아닌 가지들은 master의 변동사항을 꾸준히 주시할 것 
```

1. 신규 기능 개발
    - 개발자는 develop 브랜치로부터 본인이 신규 개발할 기능을 위한 feature 브랜치 생성
    - feature 브랜치에서 기능을 완성하면, develop 브랜치에 merge 진행

<br />

2. 라이브 서버로 배포 
    - 모두 develop 브랜치에 merge 되었다면, QA를 위해 release 브랜치 생성
    - release 브랜치를 통해 오류가 확인된다면 release 브랜치 내에서 수정을 진행
    - QA와 테스트를 모두 통과했다면, 배포를 위해 release 브랜치를 master 브랜치 쪽으로 merge
    - release 브랜치 내부에서 오류 수정이 진행되었을 경우 동기화를 위해 develop 브랜치 쪽에도 merge

<br />

3. 배포 후 관리 
    - 만일 배포된 master에서 버그가 발생했을 때, hotfix 브랜치를 생성하여 버그 수정 
    - 버그 픽스 후 master, develop 양 쪽에 merge하여 동기화 

<br />

![gitflowex](https://user-images.githubusercontent.com/109197023/209967306-84fe3d80-7a10-4350-9e92-32e239e2c4dd.PNG)

<br />
<br />

## Github-flow 전략
<br />

**Github-flow??**

- 자동화 개념 내장
- Git flow에 비해 흐름이 단순해짐에 따라 규칙도 단순
- master branch에 대한 규직만 정확하게 정립되어 있다면, 나머지 가지들에 대해서 특별한 관여 하지 않음
- pull request 기능 사용 권장

<br />

### Github-flow 특징

1. release 브랜치가 명확하게 구분되지 않은 시스템에서의 사용이 유용
1. GitHub 자체의 서비스 특성상 배포의 개념이 없는 시스템으로 되어있기 때문에 이 flow가 유용 
1. 웹 서비스들에 배포의 개념이 없어지고 있는 추세. 따라서 앞으로도 Git flow에 비해 사용하기 수월할 것
1. hotfix와 가장 작은 기능을 구분하지 않음
1. 구분하는 것은 우선 순위가 어떤 것이 더 높은지

<br />

## Github-flow 이용

1. 브랜치 생성(브랜치 이름을 통해 의도를 명확하게 드러내야 함)
    - master 브랜치는 항상 최신 상태, stable 상태로 product에 배포되는 브랜치(엄격한 Rule 필요)
    - 새로운 브랜치는 항상 master 브랜치에서 생성
    - Git-flow와 다르게 feature, develop 브랜치 존재하지 않음 
    - 기능 추가나, 버그 수정등 브랜치 이름에 작업에 대해 명확히 표시 

2. 개발, 커밋, 푸쉬
    - 커밋메세지를 정확하고 간결하게 작성
    - Git-flow와 상반되는 방식
    - 항상 원격지에 자신이 하고 있는 일들을 올려 다른 사람들도 확인할 수 있도록 함(작업 손실나도, 원격지 소스 받아서 작업 가능)

3. PR(Pull Request) 생성
    - PR은 코드 리뷰를 도와주는 시스템 
    - 자신의 코드를 공유하고, 리뷰 받음
    - merge 준비 완료 시, master 브랜치로 반영을 요구 

4. 리뷰, 토의 
    - PR이 master 브랜치 쪽에 merge된다면, 바로 배포되는 것이므로 상세한 리뷰와 토의가 이루어져야함

5. 테스트 
    - 리뷰와 토의가 끝나면, 라이브 서버(또는 테스트 환경)에 배포(장점) 
    - 배포 시에 문제가 발생했다면, 바로 master 브랜치의 내용을 다시 배포하여 초기화 시킴 

6. 최종 merge
    - 배포 테스트 시에 문제가 발생하지 않았다면, master로 push 하고, 즉시 배포 
    - master로 merge가 일어나면 자동으로 배포가 되도록 설정해놓는다. (CI/CD) > **Github-flow 핵심(자동화)**    

<br />

## 마무리 

<br />

- 작업 팀마다 사용하는 전략이 다르기 때문에, 팀에 적합한 방식을 사용하면 된다.

<br />

## 참조 자료

> https://inpa.tistory.com/entry/GIT-%E2%9A%A1%EF%B8%8F-github-flow-git-flow-%F0%9F%93%88-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EC%A0%84%EB%9E%B5

> https://www.youtube.com/watch?v=wtsr5keXUyE
