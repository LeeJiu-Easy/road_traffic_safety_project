# 보행자 사망 교통 사고 요인 분석 <br> 및 안전속도 5030 개선 제안
![image](https://github.com/LeeJiu-Easy/road_traffic_safety_project/assets/131653682/5b8b47bf-5161-4c2e-ab94-5ebf0ad73f6a)


### 기획 배경
안전속도 5030 시행 후 2년이 지났음에도 여전히 논쟁이 진행 중이며 거센 여론에 일부 시군구에서는 야간에 제한 속도를 상향하는 등 정책을 수정 시행할 예정
성숙한 교통 문화 정착을 위해 교통 안전에 중요한 요소를 분석하고, 향후 교통 정책 수립에 대한 가이드라인을 제공하고자 한다.

### Dataset
 **분석기간:** 2019/01/01~2022/12/31
 **분석 툴:** 빅쿼리, 파이썬(Matplotlib, Folium, Numpy, Pandas)

### EDA
 **피해자 특성**
 : 사망 보행자는 71세 이상이 가장 많으며 연령이 높아질 수록 사망자 수도 증가하는 추세. <br> 사망 보행자는 사고 당시 횡단 중인 경우가 가장 많았다.

 **가해자 특성**
 : 보행자 사망 교통사고 가해 운전자는 60대 이상, 성별로는 남성이 가장 많았으며 가해 차량은 승용차가 가장 많았다.
 
 **환경적 특성**
 : 보행자 사망 교통사고는 10월과 12월, 20~22시, 금요일, 맑은 날씨일 때 가장 많이 발생하였으며 <br> 지역적으로는 경기, 서울, 부산 등 대도시 단위에서 많이 발생

 **서울시 특징**
 : 서울시 보행자 사망 교통사고는 전국 대비 4월, 새벽 4~6시에 많이 발생했으며 가해자는 50대, 남성이 더 많았다.


### 가설
EDA를 토대로 가설은 다음과 같이 3가지 측면에서 수립하였다.
 
 **1. 치사율: 가시거리가 짧아지면 사고 치사율이 올라갈 것이다.**
:EDA는 절대적인 사망자 '수'의 측면에서 분석되었기 때문에 사상자 대비 사망자 수(사망률) 또는 사고 건수 대비 사망자수(치사율) 관점에서 접근하였다. <br>
 보행자 교통사고는 맑은 날씨일 때 가장 많이 발생하였으나, 각 날씨 별 사상자 대비 사망자 비중은 안개가 가장 높은 순위를 차지하였다. <br>
![image](https://github.com/LeeJiu-Easy/road_traffic_safety_project/assets/131653682/000952fa-9d82-4cbe-9c32-fa80f27b5ab8)
<br> 4개년도 서울시 시간대별 사망자 수 비교 결과, 일몰 후부터 일출 전(약 19시~06시) 시간대에 사망자 수가 많이 발생하고 있는 경향
사고건수 대비 사망자 수 즉 치사율의 입장에서도 일몰 후부터 치사율이 증가하며 일출 직전 정점을 찍는 모습
![image](https://github.com/LeeJiu-Easy/road_traffic_safety_project/assets/131653682/32ab33d5-4eab-4a85-9c93-964e347c60c5)


 **2. 운전자: 차량 평균 속도가 높을수록 사망 사고가 많이 일어날 것이다.**
<br>: 2022년 한 해 사망자 수는 시간대별 평균 속도와 비슷한 양상을 보이며 야간(18시~06시) 시간에는 주요 도로 최고 속도 추이와 일치
<br> 서울 주요 도로 기준, 최고 속도와 평균속도가 가장 빠른 4시~6시에 가장 많은 사망자가 발생.
![image](https://github.com/LeeJiu-Easy/road_traffic_safety_project/assets/131653682/fd9daca5-1ad3-4488-bc34-53b4c93edea7)
![image](https://github.com/LeeJiu-Easy/road_traffic_safety_project/assets/131653682/5dd95716-11d3-481a-860c-9c0d167f0ed3)
<br> 차량 평균 속도가 사망 사고에 영향을 미쳤다고 판단하여 차량 평균 속도를 억제하는 요인인 '과속 단속 카메라' 요인을 추가로 분석 진행
<br> 과속 단속 카메라가 가장 많은 서초구, 강동구, 동작구는 카메라 1대당 사망자 수가 낮았으며 과속 단속 카메라가 적은 중랑구, 강북구는 카메라 1대당 높은 사망자 수 기록
<br> <u>종합적으로 과속 단속 카메라가 보행자 사망 교통사고 감소에 영향을 줄 것으로 판단</u>
![image](https://github.com/LeeJiu-Easy/road_traffic_safety_project/assets/131653682/2976ace6-8c30-4343-9e11-5aedac71dd4b)
![image](https://github.com/LeeJiu-Easy/road_traffic_safety_project/assets/131653682/46278034-136e-41a9-933f-d3621f6e83f2)



 **3. 보행자: 인구 수가 많을 수록 사망 사고가 많이 일어날 것이다.**
: 송파구 – 강남구 순서로 인구수가 많으며 중구 – 종로구 순으로 인구수가 적은 지역
<br> 동대문구 – 영등포 구 순으로 사망자 수가 많으며 도봉구 – 구로구 순으로 사망자 수가 적은 지역으로
<br><u>인구 수와 사망자 수는 불일치하는 경향을 보이며 인구 수 대비 사망자 수가 많은 지역을 볼 때, 거주 인구 수 보다 유동인구 수가 영향을 줄 것으로 생각</u>

![image](https://github.com/LeeJiu-Easy/road_traffic_safety_project/assets/131653682/2fc96056-9634-4fd3-8d2a-7fbd91ba005e)


### 정책 실효성
시행 이후 서울 주요 도로 평균 속도가 감소하였으며 사고의 심각성 또한 감소
특히, 운전자의 빠른 대처가 필요한 <횡단 보도 외 횡단 중> 교통사고의 치사율이 낮아진 것으로 보아 안전속도 5030이 보행자 사망 교통사고에 긍정적인 영향을 준 것으로 판단

### 시사점
보행자 사망 감소 영향 요인 <새벽 시간>과 <안개 낀 날씨>를 토대로 '야간 시간에 속도 상향' 수정 시행 철회를 제안하며
감속을 유도하며 정책의 효과성 극대화할 수 있도록 과속 단속 카메라 1대 당 사망자 수가 많은 지역에 단속 카메라 추가 설치할 것을 제안
