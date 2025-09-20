## Git이란?
- **분산 버전 관리 시스템(DVCS)**
- 역할
  1. **파일 변경 사항 추적**
     - 언제, 무엇이 바뀌었는지 기록
     - 특정 시점으로 되돌리기 가능
     - 여러 버전 파일을 무작정 쌓아두는 비효율 제거
  2. **여러 사용자 간 작업 조율**
     - 원격 저장소(Github)와 로컬 저장소를 연결
     - 동일한 내용을 여러 사용자가 공유 → 협업 가능
  3. **분산 구조**
     - 모든 사용자가 저장소 전체(이력 포함)를 복사해 사용
     - 네트워크가 끊겨도 로컬에서 기록 관리 가능

---

## Git의 기본 구조
1. **Working Directory (작업 공간)**
   - 실제 작업하는 폴더
   - `.gitignore`로 추적 제외 가능
2. **Staging Area (준비 공간)**
   - `git add` 명령어로 커밋할 파일 선택
3. **Local Repository (내 저장소)**
   - `git commit`으로 기록되는 공간
   - 작업 이력이 로컬에 저장됨
4. **Remote Repository (원격 저장소, ex. Github)**
   - `git push`로 로컬 변경 사항 업로드
   - 다른 사용자들과 공유 가능

---

## Git 사용 흐름
1. 작업 공간에서 수정 → 상태: modified
2. 커밋할 파일 선택 → `git add` → 상태: staged
3. 변경 사항 기록 → `git commit` → Local Repository 반영
4. 원격 저장소 업로드 → `git push`

---

## 주요 개념과 명령어
- `git init` : 새 로컬 저장소 생성
- `git clone [URL]` : 원격 저장소 복제
- `git status` : 현재 상태 확인
- `git add [파일명]` : 변경된 파일을 staging area에 올림
- `git commit -m "메시지"` : staged 파일 기록
- `git push origin main` : 로컬 커밋을 원격 저장소에 반영
- `git pull` : 원격 저장소 변경 사항 가져오기

---

## .gitignore
- 추적하지 않을 파일 목록 지정
- 예: 보안 키, 환경 변수, 빌드 산출물 등
- [gitignore.io](https://www.toptal.com/developers/gitignore) 에서 자동 생성 가능

---

## 정리
Git의 핵심은 **“변경 사항을 기록해두고 협업할 수 있게 해주는 체계적인 관리 시스템”**입니다.
즉, `작업 → add → commit → push`의 흐름으로 이해할 수 있습니다.
"""
