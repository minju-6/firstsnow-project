## 이상징후 효율적 탐지를 위한 IoT 메시지 로깅 시스템  

  
## 💻 프로젝트 소개
전동보장구와 센서에서 발생한 데이터 및 이벤트 메시지를 수집, 저장, 분석하고  
감지한 에러들을 시각화하여 실시간 모니터링이 가능한 시스템입니다.

  
### 📌 주요 기능
- 전동보장구로부터 들어오는 데이터 로깅
- 이상징후를 감지하여 로깅
  - 양옆, 앞뒤 기울기에 따른 넘어짐 감지
  - 현재 배터리 사용량을 확인하여 에러 감지
  - GPS 에러 감지
  - 통신 에러 감지

  
## ⌛️ 개발 기간
2023.09 ~ 2023.12.10 

### 👭 멤버 구성
❄️ 팀명: 첫눈처럼 너에게 가겠다.
- IT 정보공학과 김현지
- IT 정보공학과 김민주  

### 🔧 개발 환경
 <img src="https://img.shields.io/badge/Language-%23121011?style=for-the-badge">![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=java&logoColor=white)   
 <img src="https://img.shields.io/badge/Framework-%23121011?style=for-the-badge">![Spring Boot](https://img.shields.io/badge/springboot-%6DB33F.svg?style=for-the-badge&logo=springboot&logoColor=white)    
 ![ElasticSearch](https://img.shields.io/badge/-ElasticSearch-005571?style=for-the-badge&logo=elasticsearch)
 ![Kibana](https://img.shields.io/badge/-Kibana-005571?style=for-the-badge&logo=kibana)

  
## ❗ 코드 수행 과정
1. 데이터 수집 (담당 클래스: MqttConfig.java)  
   - IoT 디바이스에서 발생한 메시지 수집
   - MQTT 프로토콜을 이용하여 데이터 수신  

<img width="532" alt="image" src="https://github.com/hyeonjikim-kr/firstsnow-project/assets/65073916/a4dc2e45-3463-4e28-adc2-29a6e4209b1c">  

2. 데이터 전처리 (담당 클래스: EventService.java)
   - Jackson 라이브러리를 사용하여 JSON 데이터를 자바 객체로 파싱
   - 파싱된 데이터에서 배터리, 기울기, 위도 및 경도, 통신 에러 정보를 추출
      
  <img width="503" alt="image" src="https://github.com/hyeonjikim-kr/firstsnow-project/assets/65073916/9f02134f-31e6-4c22-895e-ec17c7945bc4">      
 
    2.1 통신 에러 감지  
    : EventType 객체의 Object 필드가 null인지 여부를 확인하고, 필드를 갱신  
  
  <img width="300" alt="image" src="https://github.com/hyeonjikim-kr/firstsnow-project/assets/65073916/324c35bf-ce85-4b03-91c0-dbdbd09434a1">      
       
    2.2 배터리 에러 감지  
    : EventType 객체에서 배터리 상태를 확인하여, 이를 기반으로 배터리 에러 메시지 갱신  
  
  <img width="300" alt="image" src="https://github.com/hyeonjikim-kr/firstsnow-project/assets/65073916/ffa44d18-4779-4222-9535-d8c95f0afd03">   
       
    2.3 넘어짐 감지  
    : EventType 객체에서 기울기 상태를 확인하고, 이를 기반으로 Roll 및 Pitch 상태 메시지 갱신  
  
  <img width="300" alt="image" src="https://github.com/hyeonjikim-kr/firstsnow-project/assets/65073916/bd6cd5be-9d53-42d9-a85d-96ba7e9c5d95">   
       
    2.4 GPS 에러 감지   
    : EventType 객체에서 기기의 위치 정보를 확인하고, 이를 기반으로 운행 상태 메시지 갱신  
    
  <img width="300" alt="image" src="https://github.com/hyeonjikim-kr/firstsnow-project/assets/65073916/193dd8f9-3bbe-41e1-96be-800b4cfff53c">     
  
            
3. 데이터 저장 및 시각화
   - 데이터를 Elasticsearch에 저장하고 Kibana로 시각

  
## 🔗 실행 방법
1. 아래의 웹사이트에 접속한다. (ID: elastic, PW: changeme):
```
http://223.130.146.101:5601
```
  
2. 왼쪽 상단의 '≡' 누르고 Discover로 들어간 후 Data views: firstsnow-final를 선택한다.
```
전동보장구로부터 들어오는 데이터의 현황을 확인할 수 있다. 
```
   
3. 왼쪽 상단의 '≡' 누르고 Dashboard로 이동한다.
```
수집된 로그 데이터들을 시각화한 것을 확인할 수 있다.
```
  
## 📧 연락처 정보
hjhj3677@naver.com  
alswn9691@naver.com  

  
본 프로젝트는 전북대학교 2023년 2학기 '산학실전캡스톤' 수업의 팀 프로젝트입니다.
