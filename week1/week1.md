# Git 간단 정리

## Git이란 무엇이고 왜 사용할까?
Git은 파일 변경 이력을 기록하고 관리하는 도구입니다.  
- 파일 수정 이력을 저장하고 필요 시 이전 상태로 되돌릴 수 있음  
- 여러 개발자가 동시에 작업 가능  
- 로컬과 원격 모두에서 기록 관리 가능 (분산 버전 관리 시스템)

## 내 파일은 어떻게 관리될까?
1. **Working Directory**: 실제 작업 파일  
2. **Staging Area**: 커밋 전 변경 사항 준비 공간 (`git add`)  
3. **Local Repository**: 변경 사항 기록 (`git commit`)

## Git 사용 방법
1. 원격 레포 생성 후 로컬과 연결 (`git clone`, `git remote add`)  
2. `.gitignore`로 추적하지 않을 파일 관리  
3. `git add → git commit → git push` 순으로 상태 관리  
4. `git status`로 파일 상태 확인

## 브랜치(branch)
- 독립적인 작업 영역, 새로운 기능/수정 시 사용  
- `git branch <이름>`: 브랜치 생성  
- `git switch <이름>`: 브랜치 전환  
- `git merge <브랜치>`: 브랜치 병합

## 커밋 기록 확인
- `git log`로 기록 조회  
- **HEAD**: 현재 브랜치 최신 커밋

## Issue와 PR
- **Issue**: 작업 목표, 버그, 개선 사항 기록  
- **Pull Request (PR)**: 작업 브랜치를 메인 브랜치에 반영 요청
