1️⃣ Git이란?

버전 관리 시스템(VCS, Version Control System)

파일이 언제, 어떻게 바뀌었는지 기록하고, 이전 버전으로 돌아갈 수 있음

여러 사람이 동시에 작업해도 충돌을 관리할 수 있음

GitHub: Git을 인터넷에서 협업할 수 있도록 지원하는 원격 저장소 서비스

2️⃣ Git 기본 개념

Working Directory: 내가 현재 작업 중인 공간

Staging Area: 커밋하기 전에 “올려놓는 대기 공간”

Repository (저장소, 레포)

Local Repo: 내 PC에 있는 저장소

Remote Repo: GitHub 같은 원격 서버에 있는 저장소

3️⃣ Git 기본 흐름
git add .                # 변경된 파일을 스테이징
git commit -m "메시지"   # 커밋(버전 기록 남기기)
git push origin main     # GitHub(원격 저장소)에 업로드


git add → 변경 파일을 스테이징

git commit → 변경 사항을 기록(버전 생성)

git push → 기록을 원격 저장소(GitHub)에 반영

상태 확인은 항상

git status

4️⃣ GitHub 레포지토리 연결

GitHub에서 New Repository 생성

주소(URL) 복사

원하는 폴더에서 터미널 열기 → 레포 클론

git clone (레포지토리 주소)


→ 내 PC에 동일한 폴더가 생성됨

5️⃣ .gitignore

Git이 추적하지 않을 파일/폴더를 지정

예: 비밀번호, 환경설정, 임시파일 등

temp1.txt
*.log
secret/

6️⃣ Branch (브랜치)

독립된 작업 공간 (여러 기능을 동시에 개발 가능)

생성

git branch feature-1


전환

git switch feature-1


병합

git merge feature-1



7️⃣ Issue & Pull Request

Issue: 프로젝트 내 작은 목표/할 일 관리

기능 구현, 버그 수정, 리팩토링 등 기록

Pull Request (PR): 내 브랜치 작업을 main에 반영해 달라고 요청

팀원들이 코드 리뷰 후 승인 → merge

8️⃣ Commit 기록 확인
git log


Commit Hash: 커밋 고유 ID

Author: 작성자

Date: 작성 시간

Message: 작업 내용

HEAD: 현재 브랜치의 최신 커밋을 가리킴

✅ 정리

Git = 버전 관리

GitHub = 온라인 협업 저장소

기본 흐름: add → commit → push

협업 필수 개념: Branch, Issue, PR

파일 제외: .gitignore

기록 확인: git status, git log