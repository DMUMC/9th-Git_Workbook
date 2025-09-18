# Git이란 무엇인가?

---
> 파일의 변경 사항을 추적하고 여러 사용자 간에 작업을 조율하기 위한 분산 버전 관리 시스템

여러 명이 한 저장소에 접근해 개별적으로 작업하고, 작업 결과를 기록으로써 반영하는 시스템이다.

# 내 파일은 어떻게 관리되는가?

---
내가 작업하고 있는 공간을 `working directory`라 한다.

디렉토리 내의 파일은 기본적으로 변경 사항이 모두 추적되며, `.gitignore`로 처리된 파일은 변화가 추력되지 않는다.

## Staging Area
추적되는 파일들의 상태는 세 개로 나누어진다.

1. `unmodified`(변경되지 않음)
   - 변경되지 않은 파일
2. `modified`(변경됨)
    - 변경된 파일
3. `staged`(스테이지됨)
   - add로 추가된 파일

체크 포인트를 만드는 일을 `commit`이라 한다.
`staged`는 `modified`된 파일 중 체크 포인트로 저장할 파일로 선택된 상태를 말한다.
이때 `modfied`된 파일을 `staged`상태로 변경하는 것을 `add`라 한다.

> `staged`된 파일들을 `Staging Area`에 있다고 부른다.

## Local Repository

>`commit`을 통해 파일의 변경 사항을 기록하는 곳이다.

반영하고 싶은 사항을 `add`를 통해 `staged`상태로 만들고, 이후 `commit`을 통해 최종적으로 `local repository`에 반영한다.

최종적으로 이 `local repository`를 `remote repository`에 반영한다.

# 새롭게 알게된 정보들

### Checkout
checkout은 브랜치를 이동하는 역할과 파일의 수정 내용을 복원해주는 역할을 수행한다.
Git 2.23 이후 switch와 restore로 책임이 분리되었다.

`git -help` 명령어를 사용해 확인할 수 있는 Git 명령어에서도 checkout이 삭제되었으며 브랜치 전환 시 switch를 활용하는 것이 권장된다.

### Issue
팀원들과 프로젝트의 작업 진행, 기능 구현, 버그 수정, 리팩토링 등을 공유하기 위한 것 이다.