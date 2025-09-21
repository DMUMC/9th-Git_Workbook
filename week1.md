# Git을 왜 사용해야 하는가?
***
* 파일에서 변경되는 사항을 저장하고, 이전 버전들을 체계적으로 관리할 수 있다.
* 여러 사용자 간에 파일들의 작업들을 조율하고 협업하기에 용이하다.
* 분산 버전 관리 시스템으로써, 여러 명이 한 파일이나 폴더에 접근해 개별적으로 작업하고, 작업 결과를 기록으로써 반영할 수 있다.
 
# 파일이 어떻게 관리되는가?
***
## 1. working directory
* 내가 현재 작업하고 있는 폴더를 지칭한다.
* working directory 내의 파일은 기본적으로 변경 사항이 모두 추적되지만, .gitignore로 추적을 제외시킬 수 있다.

## 2. staging area
* 추적되는 파일들을 커밋 전 준비하는 중간 단계 영역이다.
* .gitignore에 포함된 파일들은 포함되지 않는다.

## 3. local repository
* staging area에 올라간 파일들을 commit을 통해 파일의 변경 사항을 저장하는 곳이다.
* 원격 repository에 반영하기 위해 push할 단계이다.

# git은 어떻게 사용해야 하는가?
***
* github에서 repository를 생성한다.
* .gitignore로 추적하지 않으려는 파일을 관리한다. 프로젝트에 맞게 .gitignore를 자동으로 생성해주는 사이트도 있다. [참고](https://www.toptal.com/developers/gitignore)
* 파일 추적 제외 및 반영할 파일 관리를 완료하였으면, git add [staged 할 파일 대상] 또는 (git add .) (변경된 사항 파일 전부)를 한다.
* staging area에 추가된 파일들을 대상으로 local repository에 반영하기 위해 (git commit -m "(커밋메세지)")를 한다.
* 원격 저장소(github)에 반영하기 위해 (git push)를 한다.

# branch란?
***
* 여러 개발자가 하나의 프로젝트에서 동시에 서로 다른 작업을 할 수 있도록 만들어진 독립적인 공간이다.

## branch을 왜 사용해야 하는가?
* 여러 기능을 동시에 작업할 때, 서로의 작업에 영향을 주지 않고 독립성을 보장한다.
* 보통 새로운 기능 하나당 브랜치 하나를 만들어 사용하는 경우가 많다.

## branch 만들고 전환하기
* (git branch (브랜치 이름)) 으로 브랜치를 쉽게 만들 수 있다.
* 새롭게 만든 브랜치로 이동하려면 (git checkout (브랜치 이름)) 또는 (git switch (브랜치 이름))을 하면 된다.
* 해당 브랜치에서 작업을 했으면, 꼭 commit을 진행하고 switch를 진행해야 한다.

# branch를 merge하기
***
* 현재 브랜치에서 다른 브랜치의 변경사항을 현재 브랜치에 적용시키고 싶을 때 사용하는 명령어이다.
* (git merge (병합할 브랜치))로 할 수 있다.
* 실제 협업 시에는 충돌의 위험 때문에 바로 merge를 하지 않고, Pull Request라는 것을 작성한다.

# 커밋 기록 확인하기
***
* (git log)로 commit한 이력들을 조회할 수 있다.
* HEAD -> main에서 HEAD는 현재 브랜치의 최신 커밋을 참조하는 값이고, main은 브랜치 이름이다.

# Issue와 PR
***
## Issue
* issue는 기능 브랜치를 나누기 전 팀원들과 프로젝트의 작업 진행 현황 및 기능 구현, 버그, 리팩토링 등을 공유하기 위한 공간이다.
* issue는 크게 제목, assignees, labels, projects, milestone, development로 나누어 볼 수 있다.
1. 제목: 보통 작업 태그와 대략적인 작업 요약
2. assignees: 이슈를 작업할 담당자가 할당되는 부분이다. issue를 작성하기 때문에 작업자가 들어간다.
3. labels: 작업 태그가 할당되는 부분이다.
4. projects, milestone: 조금 더 큰 단위의 작업 내용을 적을 수 있는 부분이다.
5. devlopment: 이슈와 연결된 브랜치 또는 PR을 연결할 수 있다.

## PR
* 메인 브랜치에게 pull을 받아줄 것을 요청하는 것이다.
* github에서 관리할 수 있다. 