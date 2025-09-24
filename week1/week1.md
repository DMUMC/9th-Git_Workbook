## ⚙️ 깃(Git)
> 파일의 변경 사항을 추적하고, 여러 사용자 간에 해당 파일들의 작업들을 조율하기 위한 **분산 버전 관리 시스템**

### 🧩 분산 버전 관리 시스템(DVCS, Distributed Version Control System)?
- 모든 사용자가 전체 저장소를 가지고 있는 시스템


## 🐈‍⬛ 깃허브(Github)
> 데이터들을 저장하는 원격 저장소
깃(Git)에서 추적하는 파일을 로컬 저장소 중 하나인 깃허브에서 관리해야 한 파일을 여러 명이서 동시에 작업할 수 있기 때문에 로컬 저장소에 등록하고 관리해야 합니다.

### 1️⃣ 나의 작업 공간, ```Working Directory```
현재 작업하고 있는 공간이 **나의 작업 공간**입니다.

해당 공간 내에서 작업하는 대부분의 파일들은 모두 깃에서 추적하지만,
특정 파일이나 ```.gitignore``` 파일에서 설정한 파일들은 추적하지 않습니다.

> 추적? 깃에서 파일을 기억하여 파일의 수정 및 삭제가 생기면 알려준다는 뜻!

### 2️⃣ 변경사항 확인, ```Staging Area```
앞서 말씀드린 **깃**에서 추적하는 파일은 크게 세 가지 상태로 분류할 수 있습니다.

1. ```unmodified``` : 문자 뜻 그대로 변경사항이 없음을 의미합니다.
2. ```modified``` : 위 문자와 반대로 변경사항이 있음을 의미합니다.
3. ```staged``` : ```commit``` 전 어떤 파일을 ```commit``` 할 것인지 확인할 수 있습니다.

> 📌 **```staged```**?
깃(Git)은 파일을 추적한다고 말씀드렸습니다.
하지만, 추적하는 파일이 여러 개라면 어떤걸 추적해야 할까요?
이러한 문제점을 헤결하기 위해 사용하는 것이 바로 ```staged``` 입니다!

### 3️⃣ 커밋 후, 푸쉬까지!
커밋(commit)하고 싶은 파일을 골라 커밋(commit)한 뒤에 푸쉬(push)까지 어떻게 할까요?

```
~ 9th-Git_Workbook % git push
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 8 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 1.18 KiB | 1.18 MiB/s, done.
Total 4 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/DMUMC/9th-Git_Workbook.git
   00738fc..0287fb6  week1-Vex -> week1-Vex
```

저처럼 VSCode를 활용해 ```push``` 를 하시거나 깃이나 터미널 창을 열어 똑같이 명령어를 타이핑하여 브랜치에 올리시면 됩니다.

```push``` 를 하시게 되면, 브랜치에 제가 지금까지 수정하고 작성한 내용들이 적용됩니다!