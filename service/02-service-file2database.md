# File To Database Service

---

## 1. File To Database Service 란
### 1.1. 정의
특정 양식의 파일을 업로드하면 Database에 Table로 삽입하는 기능

## 2. 사용법
### 2.1. 생성
- menu > 서비스 > File To Data > 생성

![Service Create](./images/02-service-file2data-01.PNG)

### 2.2. 속성

| 구분 | 설명 |
|:--:|:--|
| FTD 서비스 ID | 고유한 ID(중복 불가, 영어 숫자 underscore('_') 5자 이상 50자 이내<br />{host}/svc/ftd/{application id}/{서비스ID} 로 호출되어지는 서비스로 생성 |
| FTD 서비스명 | 이름, 혹은 설명입력, 작업자가 구분하기 위해 사용 |
| 그룹 | 작업자가 구분하기 위해 사용 |
| 상태 | 서비스 사용 상태 구분, 활성 / 비활성 선택하여 사용 선택가능 |
| 인증체크 | 발급된 Token을 사용하여 서비스 사용시 인증 체크 사용 여부 |
| Rule | [2.2.1 Rule 생성 및 사용 참조](#221-rule-생성-및-사용) |

![Attribute](./images/02-service-file2data-02.PNG)

#### 2.2.1. Rule 생성 및 사용
입력 룰을 등록 (rule이 복수개여도 현재일자 한개만 사용되므로 기간이 겹치면 안됨)  

| 구분 | 설명 |
|:--:|:--|
| Rule 명 | Rule 식별자 |
| FileType | Upload file Type(excel, txt...) |
| 컬럼 구분자 | 데이터간 구분 문자 |
| 컬럼수 | 아래 컬럼 등록을 하게 되면 자동으로 변경 |
| DB 연결 ID | Menu > 연결정보 > DB연결에서 생성한 DB 연결 ID 선택 [DB POOL 생성 방법 참조](/connection-information/01-connection-information-database.md) |
| DB Catalog | DBMS 별 선택옵션이 달라짐 |
| DB Schema | DBMS 별 선택옵션이 달라짐 |
| Table 명 | 업로드 파일을 입력할 테이블명 |
| Error 처리 | 에러가 발생한 Row 개별 처리, 전체 롤백중 선택 |
| Log Table명 | 해당서비스 로그 남길 테이블명 |
| 시작일자, 종료일자 | 룰 사용 날자 지정 (지정된 날자의 룰을 해당서비스에서 호출하게 되므로 1개만 사용할땐 범위를 길게 선택할것.) |
| Excel Type인 경우 | 첫 행이 데이터인지 컬럼명인지에 따라 선택가능 |

![F2D Rule](./images/02-service-file2data-03.PNG)

#### 2.2.2. Rule에 컬럼 추가 방법

아래 그림의 +, - 를 이용하여 컬럼 추가 제거가 가능하고 만들어진 아이템의 검증, 치환 설정이 가능

| 구분 | 설명 |
|:--:|:--|
| File 컬럼 | 추가되는 컬럼별 자동 기입 |
| 컬럼명 | 사용자 식별값 |
| Table 컬럼 | 실제 입력될 테이블의 컬럼명 ( 테이블을 선택했다면 선택 목록 표시 ) |
| 컬럼길이 | 컬럼의 길이지정 |
| 검증설정 | 해당 컬럼에 입력될 데이터 검증 설정 |
| 치환설정 | 해당 컬럼에 입력될 데이터 치환 설정 |

![F2D add Rule](./images/02-service-file2data-04.PNG)

#### 2.2.3. 컬럼 검증설정
##### 2.2.3.1. 정규식

- 정규식으로 File 컬럼의 Value를 검증

| 구분 | 설명 |
|:--:|:--|
| 에러메세지 | 검증에 걸렸을때 출력될 메세지 |
| 정규식표현 | 검증할 정규식 |

![F2D validation regex](./images/02-service-file2data-05.PNG)

##### 2.2.3.2. 일반

- 일반적인 설정으로 File 컬럼의 Value를 검증

| 구분 | 설명 |
|:--:|:--|
| 에러메세지 | 검증에 걸렸을때 출력될 메세지 |
| 항목유형 | 제한없음(문자), 숫자, 영문대문자, 영문소문자, 영문 중 선택가능 |
| 최소, 최대 | 숫자일 경우 크기, 문자일 경우 문자 길이를 비교하며 값을 입력하지 않으면 제한없음 |

![F2D validation default](./images/02-service-file2data-06.PNG)

##### 2.2.3.3. 목록

- 등록된 목록값만 File 컬럼의 Value로 입력

| 구분 | 설명 |
|:--:|:--|
| 에러메세지 | 검증에 걸렸을때 출력될 메세지 |
| Add Value | 목록에 문자 추가 |
| Remove Value | 선택된 문자 제거 |
| 검증목록 | 목록에 추가된 문자열만 해당 컬럼에 입력이 가능 |

![F2D validation list](./images/02-service-file2data-07.PNG)

#### 2.2.3. 치환 설정

- 등록된 목록값을 찾아 치환

| 구분 | 설명 |
|:--:|:--|
| Add Value | 목록에 문자 추가 |
| Remove Value | 선택된 문자 제거 |
| 찾을 문자, 바꿀 문자 | 컬럼에 입력되는 데이터에서 찾을 문자를 찾아서 바꿀 문자로 치환|

![F2D replace](./images/02-service-file2data-08.PNG)

### 2.3. 테스트

1. Database에 입력할 대상 Table 생성
1. 입력할 Table 구조에 맞는 데이터 생성
1. 생성된 File To Database 아이템 선택 테스트 실행

- 테스트 데이터 생성  
![F2D Tset Request](./images/02-service-file2data-09.PNG)

- 테스트 실행과 결과 확인  
![F2D Test Response](./images/02-service-file2data-10.PNG)
