# 상권 발달 지수

**상권을 발전시키는 요소에는 무엇이 있으며 각 변수는 얼마나 영향을 미치는 가**

## 1. 전처리

전처리는 상권코드를 기준으로 groupby를 하여 집계를 하는 방식을 주로 사용하였습니다.

- **매출 관련 변수**: 요일별 매출/ 성별 매출/ 업종별 매출/ 1년 매출(2020 3분기 ~ 2021 2분기)
- **점포 관련 변수**: 점포수/ 개업 점포 수/ 폐업 점포 수 / 외식 총 점포수 / 미용,의류 총 점포수
  - **점포 관련 파생변수**: 점포 증가량/ 개폐업/ 개폐업 증가량/ 개폐업 비율/ 면적당 점포수/ 면적당 외식 총 점포수/ 면적당 미용,의류 총 점포수
- **인구 관련 변수**: 성별 생활 인구수/ 연령대별 생활 인구수/ 시간대 생활 인구수/ 요일별 생활 인구수
- **요일별 / 성별 매출 변수**: 요일별 매출 비율 / 성별 매출 비율
- **상권 배후지 인구 변수**: 연령대별 생활 인구 비율/ 성별 생활 인구 비율 / 요일 생활 인구 비율
- **직장 인구 변수**: 총 직장 인구 수 / 성별 직장 인구 수
- **상권 소득소비 변수**: 월 평균 소득 금액

## 2. 지수화

전처리 이후의 상권 발달 총 테이블의 사이즈는 (1009, 55)로 변수가 많았습니다.  
이를 바로 지수화를 할 시에는 차원의 저주 및 과적합이 우려되기 때문에 단계적 선택법(Stepwise)를 통해 변수의 수를 줄였습니다.  
### 변수간 영향력
![image](https://user-images.githubusercontent.com/70187490/147720846-0613f2b0-4ed6-4e6a-bc9d-5cf38baf7422.png)

단계적 선택법을 통해 유의미한 변수를 17개로 축소화시켰으며 다음과 같은 과정을 통해 지수화 시켰습니다.  
![image](https://user-images.githubusercontent.com/70187490/147397769-d42fbd4d-521b-44a4-bea4-b0661c255b98.png)

### 데이터 출처:
1. 상권배후지_점포.csv    : 우리마을가게 상권분석서비스
2. 서울시 우리마을가게 상권분석서비스(상권-점포).csv: 우리마을가게 상권분석서비스
3. 서울시 우리마을가게 상권분석서비스(상권-추정매출).csv: 우리마을가게 상권분석서비스
4. 서울시 우리마을가게 상권분석서비스(상권배후지-생활인구).csv: 우리마을가게 상권분석서비스
5. 서울시 우리마을가게상권분석서비스(상권-추정매출)_2020.csv: 우리마을가게 상권분석서비스
6. df_base.csv: 우리마을가게 상권분석서비스의 x, y좌표를 기준으로 QGIS로 전처리함
