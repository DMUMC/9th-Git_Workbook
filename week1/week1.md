# Git 기초

## Git이란?

Git은 **분산 버전 관리 시스템**으로 소스 코드의 변경 이력을 추적하고 관리하는 도구입니다. 여러 개발자가 협업할 때 코드의 변경사항을 효율적으로 관리할 수 있게 해줍니다.

## Git의 주요 개념

### 1. Repository (저장소)
- **Local Repository**: 개발자의 컴퓨터에 있는 저장소
- **Remote Repository**: 서버에 있는 저장소 (예: GitHub, GitLab)

### 2. Working Directory, Staging Area, Repository
- **Working Directory**: 실제 파일들이 있는 작업 공간
- **Staging Area**: 커밋할 파일들을 임시로 저장하는 공간
- **Repository**: 커밋된 파일들이 저장되는 공간

### 3. Branch (브랜치)
독립적인 개발 라인을 의미합니다. 기본 브랜치는 `main` 또는 `master`입니다.

## Git 기본 명령어

### 초기 설정
```bash
# 사용자 정보 설정
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# 설정 확인
git config --list
```

### 저장소 관리
```bash
# 새 저장소 초기화
git init

# 원격 저장소 복제
git clone <repository-url>

# 원격 저장소 추가
git remote add origin <repository-url>
```

### 파일 관리
```bash
# 파일 상태 확인
git status

# 파일을 Staging Area에 추가
git add <filename>
git add .  # 모든 변경된 파일 추가

# 커밋 생성
git commit -m "커밋 메시지"

# 변경사항 확인
git diff
git diff --staged  # Staging Area의 변경사항
```

### 히스토리 관리
```bash
# 커밋 히스토리 확인
git log
git log --oneline  # 간단한 형태로 보기

# 특정 커밋으로 이동
git checkout <commit-hash>

# 파일을 이전 상태로 되돌리기
git checkout -- <filename>
```

### 브랜치 관리
```bash
# 브랜치 목록 확인
git branch

# 새 브랜치 생성
git branch <branch-name>

# 브랜치 전환
git checkout <branch-name>
git switch <branch-name> (최근에는 이 명령어를 많이 사용함)

# 브랜치 병합
git merge <branch-name>

# 브랜치 삭제
git branch -d <branch-name>
```

### 원격 저장소 연동
```bash
# 원격 저장소에서 최신 변경사항 가져오기
git fetch origin
git pull

# 로컬 변경사항을 원격 저장소에 업로드
git push
git push origin <branch-name>
```

## Git Workflow

### 기본적인 Git 작업 흐름
1. 파일 수정
2. `git add`로 Staging Area에 추가
3. `git commit`으로 변경사항 저장
4. `git push`로 원격 저장소에 업로드

### Feature Branch Workflow
1. `main` 브랜치에서 새로운 기능 브랜치 생성
2. 기능 개발 후 커밋
3. 원격 저장소에 브랜치 푸시
4. Pull Request/Merge Request 생성
5. 코드 리뷰 후 `main` 브랜치에 병합

## .gitignore

Git에서 추적하지 않을 파일들을 지정하는 파일입니다.

```gitignore
# 의존성 모듈
node_modules/

# 빌드 결과물
dist/
build/

# 환경 변수 파일
.env

# IDE 설정 파일
.vscode/
.idea/

# 로그 파일
*.log
```