# 서울시 상권 활성화 요인 분석 & 미래 유망 상권 예측 모델


본 프로젝트는 서울시 상권 데이터를 활용해 상권 활성화 요인을 규명하여 창업 전략, 입지 선정, 정책 수립에 활용할 수 있는 인사이트를 제공합니다.
---

## 프로젝트 개요
- **목적**
  1. 상권 활성화 요인 규명
  2. 상권 성장 가능성 예측
  3. 전략적 활용 기반 마련 (점포 입지, 창업 전략, 행정 정책 지원)
- **분석 주제**  
  _"서울시 상권 활성화 요인 분석 및 미래 유망 상권 예측 모델 구축"_

---

## 데이터
- **출처**:
    - 행정동 추정매출
    https://data.seoul.go.kr/dataList/OA-22175/S/1/datasetView.do
    - 행정동 업종 별 점포 수
    https://data.seoul.go.kr/dataList/OA-22172/S/1/datasetView.do
    - 업종 별 서울시 추정 매출
    https://data.seoul.go.kr/dataList/OA-22177/S/1/datasetView.do
    - 행정동 시설 수(지하철, 버스정류장)
    https://data.seoul.go.kr/dataList/OA-22169/S/1/datasetView.do
    - 행정동 유동인구 수
    https://data.seoul.go.kr/dataList/OA-22178/S/1/datasetView.do
    - 행정동 면적
    https://data.seoul.go.kr/dataList/OA-22160/S/1/datasetView.do
    - 행정동 아파트 가격
    https://data.seoul.go.kr/dataList/OA-22163/S/1/datasetView.do
    - 서울 행정동 경위도 좌표
    https://github.com/vuski/admdongkor/tree/master/ver20241231

- **종속변수 (Y)**:
  - 행정동별 총 매출액
- **설명변수 (X)**:
  - 유동인구, 상주인구
  - 대중교통 수
  - 집객시설 수(일반적으로 교통이 아닌 다른 요소들(예: 쇼핑, 문화, 레저, 숙박 등)에 의해 사람들이 모이는 시설)
  - 아파트 평균 시가, 월 평균 소득
  - 업종별 점포 수
  - 성별/연령대별 매출 비율, 법인카드 비율

---

## 분석 방법
1. **EDA**  
   - 행정동별 주요 업종 파악  
   - 조건별 소비 특성 분석 (주중/주말, 성별, 연령대, 법인/외국인 비율)
2. **회귀분석**  
   - 다중선형회귀, Random Forest, LightGBM 비교  
   - 로그 변환, IQR 이상치 제거, 표준화 전처리
3. **클러스터링**  
   - 업종별 소비 특성 기반 군집화 (k=5)  
   - 행정동별 소비 특성 기반 군집화 (k=3)  
   - ELBOW Method, Silhouette 계수 활용

---

## 분석 결과

### 1. Random Forest 변수 중요도
<img width="200" height="400" alt="Image" src="https://github.com/user-attachments/assets/29b72153-09cf-4143-9d47-460a3a04aedc" />  

*Random Forest 변수 중요도: 비교통 집객시설 수, 평균 소득 상위*

### 2. LightGBM 변수 중요도
<img width="250" height="450" alt="Image" src="https://github.com/user-attachments/assets/b98dbb18-40e0-49a1-89a7-a4df9fe7944c" />  

*LightGBM: 소득 수준 영향도가 더 높음*

### 3. 모델 성능
<img width="400" height="250" alt="Image" src="https://github.com/user-attachments/assets/246b88f4-ba3f-4855-9522-3c46cfcd8c0f" /> 


### 4. 업종별 클러스터 히트맵
<img width="500" height="250" alt="image" src="https://github.com/user-attachments/assets/205e5665-ed9b-429b-ad45-499f626f41eb" />

*업종별 소비 특성 기반 5개 클러스터 분류*

### 5. 행정동별 클러스터 지도
<img width="500" height="250" alt="image" src="https://github.com/user-attachments/assets/9f5f0b5e-b0b0-471b-b4ef-695055d7ae14" />  

*행정동별 소비 특성 기반 3개 클러스터 지도*

- 노란색 클러스터:
  - 주중중심, 40~60대, 내국인 위주 소비가 이루어지는 지역
- 청록색 클러스터:
  - 법인/외국인 위주, 30대 중심, 직장인 위주 소비
- 파란색 클러스터:
  - 주말위주, 20~30대 위주로 소비가 이루어지는 지역

---

## 결론 및 의의
- 상권 활성화는 단순 유동인구보다 **소득 수준과 소비층 특성**이 더 큰 영향을 미침
- **창업 및 입점 전략**: 지역·업종 소비 특성 기반 정밀 타깃팅
- **마케팅 전략**: 소득·소비 성향 맞춤형 캠페인 설계
- **정책 활용**: 상권 클러스터 특성을 반영한 맞춤형 지원정책 수립 가능

