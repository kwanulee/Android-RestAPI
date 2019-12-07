## REST API 테스트 예제

### 1. REST API 설계
- 다음 프로그램 코드를 실행시키기 위해서는 다음 형식의 **REST API**가 준비되어 있어야 합니다.
	- 디바이스 목록 조회
		
		```
		GET /devices
		```
	
	- 디바이스 상태 조회

		```	
		GET /devices/{deviceId}
		```
	- 디바이스 상태 변경

		```	
		PUT /devices/{deviceId}
		```
		
		- message body (payload)
		
			```json
			{ 
				"tags" : [
					{
						"attrName": "temperature",
						"attrValue": "27.0"
					},
					{
						"attrName": "LED",
						"attrValue": "OFF"
					}
				]
			}

	
	- 디바이스 로그 조회	

		```		
		GET /devices/{deviceId}/log?from=yyyy-mm-dd hh:mm:ss&to=yyyy-mm-dd hh:mm:ss
		```
		
### 2. AWS IoT 백엔드 구축

다음 방법을 통해서 다음 IoT 백엔드를 구축한다.

- [디바이스 데이터 저장 IoT 백엔드 구축](https://kwanulee.github.io/IoTPlatform/dynamodb.html#4)
- [디바이스 목록 조회 REST API 구축](https://kwanulee.github.io/IoTPlatform/api-gateway-3.1.html)
- [디바이스 상태 조회 REST API 구축](https://kwanulee.github.io/IoTPlatform/api-gateway-3.2.html)
- [디바이스 상태 변경 REST API 구축](https://kwanulee.github.io/IoTPlatform/api-gateway-3.3.html)
- [디바이스 로그 조회 REST API 구축](https://kwanulee.github.io/IoTPlatform/api-gateway-3.4.html)

### 3. Android 앱 설치 및 실행

- 초기 실행 화면

![](figures/screenshot1.png)

- 아래 세가지 버튼을 클릭하기 전에 API URI를 입력해야 합니다.
	- Amazon API Gateway로 부터 만들어진  API 서버 URL을 기록해 둔다. 
		
		```
		https://xxxxxxxx.execute-api.ap-northeast-2.amazonaws.com/prod 
		```
	- 사물목록 조회 API URI
		
		```
		https://xxxxxxxx.execute-api.ap-northeast-2.amazonaws.com/prod/devices
		```
	
	- 사물상태 조회/변경 API URI

		```
		https://xxxxxxxx.execute-api.ap-northeast-2.amazonaws.com/prod/devices/{devices_name}
		```
	- 사물로그 조회 API URI

		```
		https://xxxxxxxx.execute-api.ap-northeast-2.amazonaws.com/prod/devices/{devices_name}/log
		```	