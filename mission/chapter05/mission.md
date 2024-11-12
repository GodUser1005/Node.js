## 각 api 마다 이슈 생성

![alt text](<이슈 생성.png>)

## 특정지역에 가게 추가 API 구현

### 이슈
![alt text](<1번 API 이슈 및 브랜치 생성.png>)

### Controller
![alt text](1_controller.png)

### Service
![alt text](1_service.png)

### Repository
![alt text](1_repository_1.png) 
![alt text](1_repository_2.png)

### DTO
![alt text](1_dto.png)

### 결과

#### 초기 데이터
아래는 음식 카테고리에 대한 초기 데이터 값이다.
음식 카테고리가 있어야 가게에 음식카테고리를 추가가능하므로 초기 데이터 설정이 필요합니다.
![alt text](1_result_data_1.png)

아래는 위치에 대한 초기 데이터 값이다.
특정지역에 가게를 추가해야하기에 지역에 대한 데이터가 있어야합니다.
![alt text](1_result_data_2.png)

#### Postman 실행 결과

아래는 성공 했을때의 모습
![alt text](1_result_success.png)

아래는 실패 했을때의 모습(category_id 또는 location_id 가 데이터 범위에 벗어나는 경우)
![alt text](1_result_failure.png)

에러 문구는 error 보여주는 방식으로 에러처리
상태코드 변경도 추후 변경해야함

아래는 stores 테이블에 데이터가 잘 들어간 모습이며
에러가 발생한 요청에 대한 데이터는 들어가있지 않다.
![alt text](1_result_success_data.png)


##

