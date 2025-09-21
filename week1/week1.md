## 1. 요구사항 분석

먼저 피그마 자료를 기반으로 서비스에서 필요한 주요 기능을 정리하였다.

- **회원 관리**: 카카오 로그인을 통한 사용자 식별, 주소 관리, 선호 카테고리 저장
- **미션 기능**: 사용자가 참여할 수 있는 미션 제공, 완료 조건 및 시간 기록
- **알림 기능**: 사용자별 알림 내역 관리
- **결제 기능**: 사용자 결제 내역 및 결제 관련 부가 정보 관리
- **가게 및 리뷰 기능**: 가게별 정보와 리뷰, 평점 관리
- **사진 관리**: 결제, 리뷰 등과 연결된 증빙 사진 저장

---

## 2. 엔티티 도출

위 요구사항을 통해 다음과 같은 주요 엔티티를 도출하였다.

- **사용자 정보 (tbl_user_info)**
- **사용자 주소 (tbl_user_address)**
- **사용자 선호 정보 (tbl_favorite_info)**
- **미션 정보 (tbl_mission_info)**
- **사용자 미션 기록 (tbl_user_mission)**
- **사용자 알림 정보 (tbl_user_alarm)**
- **알림 상세 정보 (tbl_alarm_info)**
- **사용자 결제 정보 (tbl_user_purchase)**
- **가게 정보 (tbl_store_info)**
- **리뷰 정보 (tbl_review_info)**
- **사진 정보 (tbl_photo_info)**

---

## 3. 속성 정의

각 엔티티별로 필요한 속성을 정의하였다.

- **사용자**: 닉네임, 휴대폰번호, 성별, 계정 상태, 로그인 여부 등
- **미션**: 미션명, 상세내용, 완료조건, 시작일/종료일, 성공 시각
- **알림**: 알림 제목, 본문, 알림 타입, 활성화 여부
- **결제**: 금액, 결제일시, 결제 방법
- **리뷰**: 리뷰 본문, 점수, 등록일자
- **사진**: 파일명, 이진데이터, 등록일자

---

## 4. 관계 설정

엔티티 간의 관계를 다음과 같이 정의하였다.

- 한 **사용자**는 여러 **주소**를 가질 수 있음
- 한 **사용자**는 여러 **선호 카테고리**를 가질 수 있음
- 한 **사용자**는 여러 **미션 기록**을 가질 수 있고, 미션 정보와 연결됨
- 한 **사용자**는 여러 **알림**을 받음
- 한 **사용자**는 여러 **결제 내역**을 가짐
- 한 **가게**는 여러 **리뷰**를 가짐
- 한 **결제**는 여러 **리뷰**와 연결 가능


# 시니어 미션 (1)

- [ ]  미션 자료로 제공된 피그마를 보고 ERD를 설계한 후 제 1,2,3 정규화를 통해 제 1,2,3 정규형을 만들고 각각 중복된 데이터가 어떻게 변화하였고 어떠한 이점이 있었는 지 작성하여 주세요
    - 1정규형
        
        반복 속성을 분리하여 주소, 선호, 사진 등을 별도 테이블로 분리.
        
    - 2정규형
        
        미션 기록 테이블에서 전체 키에만 종속되도록 정리.
        
    - 3정규형
        
        미션 정보에서 완료 조건은 미션에만 종속되므로 별도 속성으로 관리.
        

- [ ]  피그마의 홈 부분에서 한 사람이 “미션 도전!” 버튼을 빠르게 여러 번 눌렀을 때 여러 가지 이유(비동기 로직 등)로 요청이 지연되어 완전히 처리하기 전 두 번 요청이 들어갈 수 있습니다. 이를 해결할 수 있는 방법에 대해 작성하여 주세요 (ERD 직접적으로 관련이 있기보다는 설계할 때 한번쯤 고민해보면 좋을 것 추가시켜 놓았습니다) (다양한 방법이 있으니 찾아봐 주세요)
    - 클라이언트단
        
        js쪽에서 요청을 날릴때 타입스탬프 기록해서 중복 요청 방지
        
    - 서버단
        
        도전중인 목록에서 같은 미션이 이미 존재하면 튕겨내기




1. 0주차 때 **직접 설계한** 데이터베이스를 토대로 아래의 화면에 대한 쿼리를 작성
- 설계한 DB 사진 (0주차 DB 수정 가능!)


- 본문

![리뷰 작성하는 쿼리,
* 사진의 경우는 일단 배제]

리뷰 작성하는 쿼리,
* 사진의 경우는 일단 배제

insert into tbl_review_info (tri_tupcode, tri_context, tri_score, tri_regidate)

values(결재정보pk, 본문정보, 별점정보, now())   ⇒ autoTriCode

insert into tbl_photo_info (tpi_targetname, tpi_targetcode, tpi_binary, tpi_regidate, tpi_file_name)

values(’tbl_review_info’, autoTriCode, 바이너리정보, now(), 파일명)


마이 페이지 화면 쿼리

select * from tbl_user_code


내가 진행중, 진행 완료한 미션 모아서 보는 쿼리(페이징 포함)

select tum.*, tmi.*

from tbl_user_mission as tum

inner join tbl_mission_info as tmi

where tum_tuicode = 유저코드

ORDER BY tum_code DESC

LIMIT 페이지n개표시 OFFSET (n페이지 -1);

![홈 화면 쿼리
(현재 선택 된 지역에서 도전이 가능한 미션 목록, 페이징 포함)]

홈 화면 쿼리
(현재 선택 된 지역에서 도전이 가능한 미션 목록, 페이징 포함)

select *

from tbl_mission_info as tmi

left join tbl_user_mission as tum 

     on tum_tmicode = tmi_code and tum_tuicode = 유저코드

left join tbl_user_info as tui on tmi_tuicode = tui_code

left join tbl_address_info as tadi on tsi_address_code = tadi_code

ORDER BY tmi_code DESC

where tadi = 지역코드 and tum_tmicode is null


-  미션 1(내가 진행중, 진행 완료한 미션 모아서 보는 쿼리(페이징 포함))에서
정렬 기준을 1순위는 포인트로 2순위는 최신순으로 하여 Cursor기반 페이지네이션을 구현해보세요!
    
    ```sql
    SELECT tum.*, tmi.*
    FROM tbl_user_mission AS tum
    INNER JOIN tbl_mission_info AS tmi
        ON tum.tum_tmicode = tmi.tmi_code
    WHERE tum.tum_tuicode = 유저코드
      AND tum.tum_code < 이전페이지마지막행pk
    ORDER BY tum.tum_별점 DESC, tum.tum_code DESC
    LIMIT 페이지n개표시
    ```
    
    - order by에 순서대로 조건 넣고 이전 페이지 마지막 데이터 pk가져옴

-  다양한 트랜젝션 상태와, 트랜젝션 전파에 대해 조사해주세요!
    - 트랜잭션 상태(State) 흐름
        - **Active**: 실행 중
        - **Partially Committed**: 마지막 연산 끝, 커밋 직전
        - **Committed**: 커밋 완료
        - **Failed**: 오류 발생으로 더 진행 불가
        - **Aborted(Rolled Back)**: 롤백 완료(필요하면 재시도 가능)
        - (분산/2PC에서) **In-Doubt/Prepared**: 커밋 준비는 했지만 최종 결정 대기
    - 트랜잭션 전파
        - REQUIRED(기본)	있으면 참가, 없으면 새로 시작
        - REQUIRES_NEW	항상 새 트랜잭션 시작, 기존 있으면 잠시 보류
        - SUPPORTS	있으면 참가, 없으면 비트랜잭션으로 실행
        - MANDATORY	반드시 기존 트랜잭션 있어야 함, 없으면 예외
        - NOT_SUPPORTED	트랜잭션을 일시 정지하고 비트랜잭션으로 실행
        - NEVER	트랜잭션 있으면 예외
        - NESTED	부모 트랜잭션 안에서 저장점(savepoint) 기반 하위 트랜잭션처럼 실행(부모 롤백 시 함께 롤백, 자식만 롤백 가능)

- 함수 기반 인덱스와 복합 인덱스에 대해 조사하고,
성능상 이점과 단점을 적어주세요!
    - 함수기반 인덱스
        
        장점 : 데이터 정규화 없이도 검색 최적화
        
        단점 : 복잡한 함수일 경우 인덱스 생성/갱신 비용 증가
        
    - 복합 인덱스
        
        장점 :정렬(ORDER BY)**에도 활용 가능, 비용 절약 가능
        
        단점 : 여러개 걸리면 insert update에서 비용 증가