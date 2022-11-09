# File Service

---
## 1. File Service 란
### 1.1. 정의

>File 업로드 서비스

## 2. 사용법
### 2.1. 생성

🎈 __Menu > 서비스 > File Service > 생성__

<img src = "./images/02-service-file-01.png" width = "750px"> </img>

### 2.2. 속성

<img src = "./images/02-service-file-01-2.png" width = "1000px"> </img>

| 구분 | 설명 |
|:--:|:--|
| File 서비스 ID | 고유한 ID(중복 불가, 영어, 숫자, underscore('_') 5자 이상 50자 이내<br />{host}/svc/file/{userName}/{File서비스ID} 로 호출되어지는 서비스로 생성 |
| File 서비스명 | 이름, 혹은 설명입력, 작업자가 구분하기 위해 사용 |
| 그룹 | 작업자가 구분하기 위해 사용 |
| 상태 | 서비스 사용 상태 구분, 활성 / 비활성 선택하여 사용 선택가능 |
| 인증체크 | 발급된 Token을 사용하여 서비스 사용시 인증 체크 사용 여부 |
| Download 사용여부 | 다운로드 사용 여부 |
| Download 인증체크 | 발급된 Token을 사용하여 다운로드 사용시 인증 체크 사용 여부 |
| File Upload 검증 설정 | [2.2.1 File Upload 검증 설정 참조](#221) |


#### 2.2.1. File Upload 검증 설정
##### 2.2.1.1. 속성

| 구분 | 설명 |
|:--:|:--|
| 파일 검증 사용 | 사용 여부 |
| File 저장 설정 | 기본저장위치 (<projectPath>/platform/filesystem)에서 사용자 지정 양식으로 변경 가능 |
| File Size 검증 | 검증유형 - 파일 크기 범위, 최소크기, 최대크기, 제한없음 선택가능 |
| File 유형 검증 | 선택에 따라 file 확장자와 File Signature 검증 |
| 추가 옵션 | zip file upload 후 압축보관, 압축해제보관 (압축해제 보관 시 암호걸려 있으면 불가능) |

### 2.3. 테스트

🎈 __생성된 File Service Item 선택 > 테스트실행__

<img src = "./images/02-service-file-01-3.png" width = "750px"> </img>

<img src = "./images/02-service-file-01-4.png" width = "400px"> </img>

```
파일 업로드 서비스 테스트 완료 시 출력

{
   "session": "Y",
   "success": true,
   "message": "",
   "FILE_INFO": [   {
      "FILE_SIZE": 5,
      "SERVICE_ID": "testUpload001",
      "FILE_ID": "2019092614260539016",
      "FILE_MESSAGE": "",
      "FILE_EXT": "txt",
      "FILE_URL_PATH": "/svc/file/evan/testUpload001?_down=_down&FILE_ID=2019092614260539016",
      "FILE_NAME": "test.txt"
   }]
}
```
