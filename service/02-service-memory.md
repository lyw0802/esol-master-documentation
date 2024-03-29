# Memory Service

---

## 1. Memory Service 란
### 1.1. 정의

>DB 입력 없이 메모리에 데이터를 올려 빠르게 조회하는 기능,  
>고정된 Data 혹은 수정이 빈번하지 않은 Data를 메모리에 상주하였다가 읽는 기능(속도↑ , Database부담↓),  
>설정정보, 버젼정보, 공통최상위코드 등의 고정Data이면서 잦은 호출이 예상되는 Data를 메모리에 올려서 사용

### 1.2. 주요기능 및 부가기능
<img src = "./images/02-01-service-memory-01-2.png" width = "600px"> </img>
| 기능 | 설명 |  
|:--:|:--|  
| 검색  | 서비스 검색 기능 :  그룹별 ,검색조건은 서비스ID ,<br/> 서비스명으로 검색|
| Text Export  | 조회된 화면(목록)을 Text 로 Export |
| 프린트  | 조회된 화면(목록) 인쇄 |
| 생성  | 서비스 생성 |
| 수정  | 조회된 화면(목록)에서 선택된 서비스 수정 |
| 삭제  | 조회된 화면(목록)에서 선택된 서비스 삭제 |
| 복제생성  | 조회된 화면(목록)에서 선택된 서비스를 복제생성<BR/>서비스ID만 입력하여 동일한 서비스를 생성 |
| 테스트실행  | 서비스 실행 (Timeout:120초) |
| JSONP실행  | JSONP(JSON with Padding)형태로 실행<BR/>script태그를 이용하여 CORS를 우회하여 실행 할 수 있다.<BR/>(Timeout:120초)  |
| Export  | 서비스 전체를 Export 한다. 파일로 다운받는다.<BR/>백업용으로 활용하거나 서비스 이관작업에 사용한다. |
| Import  | Export된 파일을 Import한다.<BR/>서비스 복구에 사용하거나 서비스 이관작업에 사용한다. |

## 2. 사용법
### 2.1. 생성

🎈 __menu > 서비스 > Memory Data > 생성__

<img src = "./images/02-service-memory-01.PNG" width = "750px"> </img>

### 2.2. 속성

<img src = "./images/02-service-memory-01-2.PNG" width = "600px"> </img>

| 구분 | 설명 |
|:--:|:--|
| Memory Data 서비스 ID | 고유한 ID(중복 불가, 영어, 숫자, underscore('_') 5자 이상 50자 이내<br/>{host}/svc/md/{application id}/{Memory Data서비스ID} 로 호출되어지는 서비스로 생성 |
| Memory Data 서비스명 | 이름, 혹은 설명입력, 작업자가 구분하기 위해 사용 |
| 그룹 | 작업자가 구분하기 위해 사용 |
| 상태 | 서비스 사용 상태 구분, 활성 / 비활성 선택하여 사용 선택가능 |
| 인증체크 | 발급된 Token을 사용하여 서비스 사용시 인증 체크 사용 여부 |
| 구분 | 데이터 직접입력(고정자료), DB Service 중 선택 가능 |
| 갱신주기(초) | 구분을 DB Service 선택 시 데이터 갱신 주기 |
| DB Service | 구분을 DB Service 선택 시 사용할 DB 서비스 선택 |


#### 2.2.1. 속성 DB Service

- 속성 > 구분 > DB Service(Read Only) 선택 시 미리 생성한 DB Service 항목들 중 선택 가능

<img src = "./images/02-service-memory-01-3.PNG" width = "600px"> </img>

#### 2.2.2. 속성 직접입력

- JSON Format의 문자열 입력 가능

<img src = "./images/02-service-memory-01-4.PNG" width = "600px"> </img>

### 2.3. 테스트

🎈 __생성된 Memory Data Item 선택 > 테스트실행__

<img src = "./images/02-service-memory-01-5.PNG" width = "750px"> </img>

> 좌측: 구분-DB Service 선택 테스트 결과  
> 우측: 구분-직접입력 선택 테스트 결과

<img src = "./images/02-service-memory-01-6.PNG" width = "650px"> </img>
