# Proxy Service

---

## 1. Proxy Service 란
### 1.1. 정의

>Proxy Service란 '대리'라는 의미로 직접 통신할수 없는 두점 사이에서 통신을 할 경우  
>그 사이에 있는 중계기로서 대리로 통신을 수행하는 기능

### 1.2. 주요기능 및 부가기능
<img src = "./images/02-01-service-proxy-01-2.png" width = "600px"> </img>
| 기능 | 설명 |  
|:--:|:--|  
| 검색  | 서비스 검색 기능 :  그룹별 ,검색조건은 서비스ID ,<br/> 서비스명으로 검색|
| Text Export  | 조회된 화면(목록)을 Text 로 Export |
| 프린트  | 조회된 화면(목록) 인쇄 |
| 생성  | 서비스 생성 |
| 수정  | 조회된 화면(목록)에서 선택된 서비스 수정 |
| 삭제  | 조회된 화면(목록)에서 선택된 서비스 삭제 |
| 복제생성  | 조회된 화면(목록)에서 선택된 서비스를 복제생성<BR/>서비스ID만 입력하여 동일한 서비스를 생성 |
| 테스트실행  | 서비스 실행  |
| JSONP실행  | JSONP(JSON with Padding)형태로 실행<BR/>script태그를 이용하여 CORS를 우회하여 실행 할 수 있다.  |
| Export  | 서비스 전체를 Export 한다. 파일로 다운받는다.<BR/>백업용으로 활용하거나 서비스 이관작업에 사용한다. |
| Import  | Export된 파일을 Import한다.<BR/>서비스 복구에 사용하거나 서비스 이관작업에 사용한다. |

## 2. 사용법
### 2.1. 생성

🎈 __menu > 서비스 > Proxy Service > 생성__

<img src = "./images/02-service-proxy-01.PNG" width = "750px"> </img>

### 2.2. 속성

<img src = "./images/02-service-proxy-01-2.PNG" width = "600px"> </img>

| 구분 | 설명 |
|:--:|:--|
| Proxy 서비스 ID | 고유한 ID(중복 불가, 영어, 숫자, underscore('_') 5자 이상 50자 이내<br />{host}/svc/prx/{application id}/{Proxy서비스ID} 로 호출되어지는 서비스로 생성 |
| Proxy 서비스명 | 이름, 혹은 설명입력, 작업자가 구분하기 위해 사용 |
| 그룹 | 작업자가 구분하기 위해 사용 |
| 상태 | 서비스 사용 상태 구분, 활성 / 비활성 선택하여 사용 선택가능 |
| 인증체크 | 발급된 Token을 사용하여 서비스 사용시 인증 체크 사용 여부 |
| 로그(DB Insert) | proxy 서비스 사용 내역을 DB에 입력 사용 여부<BR/>사용상태이어야 '로그>Proxy로그보기' 에서 로그를 <BR/>확인 할 수 있습니다.<BR/> Proxy된 내용 전체를 Database에 저장 하므로 사용량이 많을 <BR/>경우 Database 성능을 고려하여 사용을 하셔야 합니다.  |
| Forward IP | Client IP |
| Preserve Host | Host 헤더를 현재 사용자가 요청한 서버 host로 지정 |
| Preserve Cookies | Cookie 헤더를 현재 사용자가 요청한 서버 cookie로 지정 |
| Handle Redirect | {:target="_blank"} |
| Socker Timeout(ms) | Socket 연결 제한시간 |
| Read Timeout(ms) | 백엔드 서버로부터 데이터를 읽을 때의 제한시간 |
| Request Timeout(ms) | 백엔드 서버로 데이터를 전송할 때의 제한시간 |
| Max Connections | 최대 연결 갯수 |
| Load Balancing | 로드밸런싱 알고리즘 선택(round-robin, hash, least) <BR/> Target Path가 2개 이상일 경우에만 작동합니다. <BR/> Target Path가 1개면 화면상에 '사용안함' 으로 표기됩니다.<BR/> 예) 'load balance :round-robin(Target Path 1개는 사용안함)' |
| Target Path | Add Target Path를 선택하여 연결대상 설정가능(복수개 가능) |

#### 2.2.1. Load Balancing
Load Balancing 즉 부하를 분산 하는 기능으로<BR/>
Target Path(호출 대상 서버)가 2개이상 부터 작동합니다.<BR/>
1개면 작동 할 수 가 없습니다.

| 구분 | 설명 |
|:--:|:--|
| Round-robin | 호출 대상 서버가 5개이고 각각의 고유 번호를 1~5번일때 1번부터 5번까지 순차적 호출 기법 |
| hash | 사용자 ip를 hasing하여 분배하는데, 사용자는 항상 같은 서버로 연결을 보장하는 기법 |
| least | 호출 대상서버가 복수개일때 연결 개수가 가장 적은 서버를 선택하여 호출 하는 기법 |

### 2.3. 테스트

🎈 __생성된 Proxy Service Item 선택 > 테스트실행__

<img src = "./images/02-service-proxy-01-3.PNG" width = "750px"> </img>

__테스트 결과__

<img src = "./images/02-service-proxy-01-4.PNG" width = "700px"> </img>
