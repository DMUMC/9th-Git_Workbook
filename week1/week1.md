# UMC Git 1주차 내용 정리
## Git이란?
> 파일의 변경 사항을 추적하고 여러 사용자 간에 해당 파일들의 작업들을 조율하기 위한 **분산 버전 관리 시스템**

## Git을 써야하는 이유
* 파일의 변경사항을 추적
* 여러 사용자 간에 해당 파일들의 작업들을 조율
* 분산 버전 관리 시스템

## Git Repository에 파일이 저장되는 과정
**Working Directory** -> **Staging Area** -> **Git Repository**

## Git Repository에 파일 저장을 위한 명령어
* 원격 레포에 있는 저장소를 로컬에 복사합니다.
```git
git clone (레포지토리 주소)
```

* Working Directory의 파일들을 staged 상태로 변경합니다. <br>
해당 경로에 있는 모든 파일을 변경할 수도 있고, 특정 파일만 변경할 수도 있습니다.
```git
git add .
git add (파일이름)
```

* staged 된 파일들의 변경사항을 로컬 레포에 반영합니다.
```git
git commit -m "(커밋메시지)"
```

* 로컬 레포의 내용을 원격 레포로 보냅니다. 
```git
git push origin (브랜치 이름)
```

* Working Directory 와 Staging Area 에 있는 파일들의 상태를 확인할 수 있습니다.
```git
git status
```

## 브랜치(Branch)란?
> 개발자들이 동시에 작업하지만 서로에게 영향을 끼치지 않도록 하는 독립적인 영역

## 브랜치 사용과 관련된 명령어
* 새로운 브랜치를 생성합니다.
```git
git branch (브랜치 이름)
```

* 현재 브랜치에서 다른 브랜치로 이동할 수 있습니다. <br>
두 명령어 모두 브랜치를 이동할 때 쓸 수 있지만, 브랜치 전환 시에는 ***checkout*보다 *switch*를 사용하는 것을 권장합니다.**
```git
git checkout (브랜치 이름)
git switch (브랜치 이름)
```

* 다른 브랜치의 변경사항을 현재 브랜치에 적용시킵니다.
```git
git merge (브랜치 이름)
```

## GitHub의 Issue와 PR이란?
### Issue
> main 브랜치에서 기능 브랜치를 나누기 전 팀원들과 프로젝트의 작업 진행 현황과 기능 구현, 버그 수정, 리팩토링 등을 공유하기 위해 사용하는 것
### Issue에 들어가는 내용
* 이슈 제목
* 이슈 내용
* Assignees
* Labels
* Projects
* Milestone
* Development
---
### PR(Pull Request)
> 메인 브랜치에게 다른 브랜치에서 작업한 내용을 Pull 해달라고 요청(Request)하는 것

### PR에 들어가는 내용
* 제목
* 내용
* Reviewers
* Assignees
* Labels
* Projects
* Milestone
* Development