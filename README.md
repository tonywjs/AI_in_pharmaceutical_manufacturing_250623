## **1. Laboratory.csv (총 55 개 컬럼)**

|**구분**|**컬럼**|**의미**|
|---|---|---|
|**계보 정보**|batch|최종 제품 배치 번호(인덱스)|
||code|제품 하위군(sub-family)을 구분하는 제품 코드|
||strength|정제 1 개당 API 함량 (mg)|
||size|목표 생산 정제 수(배치 크기)|
||start|생산 시작 시각(YYYY-MM-DD hh:mm)|
|**API/부형제 계열**|api_code, api_batch|API 자재 코드·배치 번호|
||smcc_batch, lactose_batch, starch_batch|실리카화 MCC, 락토스, 전분 배치 번호|
|**API 품질**|api_water|API 수분 함량(%)|
||api_total_impurities, api_l_impurity|총 불순물·L-불순물 함량(%)|
||api_content|순 API 함량(%)|
||api_ps01, api_ps05, api_ps09|입도 10 %·50 %·90 %(µm)|
|**락토스 품질**|lactose_water|수분(%)|
||lactose_sieve0045, …015, …025|체별 잔류율(%)|
|**SMCC 품질**|smcc_water|수분(%)|
||smcc_td, smcc_bd|탭 밀도·벌크 밀도(g/ml)|
||smcc_ps01, smcc_ps05, smcc_ps09|입도 10 / 50 / 90 %(µm)|
|**전분 품질**|starch_ph|pH|
||starch_water|수분(%)|
|**중간제품(정제심) 품질**|tbl_min_thickness, tbl_max_thickness|정제심 최소·최대 두께(mm)|
||tbl_min_weight, tbl_max_weight|정제심 최소·최대 중량(mg)|
||tbl_rsd_weight|정제심 중량 RSD(%)|
||tbl_min_hardness, tbl_max_hardness, tbl_av_hardness|정제심 경도 최소·최대·평균(N)|
|**코팅 후 품질**|fct_min_thickness, fct_max_thickness|코팅정 최소·최대 두께(mm)|
||fct_rsd_weight|코팅정 중량 RSD(%)|
||fct_min_hardness, fct_max_hardness, fct_av_hardness|코팅정 경도 최소·최대·평균(N)|
|**가공 지표**|tbl_tensile, fct_tensile|정제심·코팅정 인장강도(정규화 경도)|
||tbl_yield, batch_yield|압축 공정·전체 배치 수율(%)|
|**최종제품 품질**|dissolution_av, dissolution_min|30 분 약물 방출 평균·최소값(%)|
||residual_solvent|잔류 용매(%)|
||impurities_total, impurity_o, impurity_l|총 불순물, O / L 불순물(%)|

---

## **2. Process Time-series 파일(예: 1.csv)**

|**컬럼**|**의미**|**주요 단위**|
|---|---|---|
|timestamp|10 초 간격 타임스탬프(인덱스)|–|
|campaign|동일 설비 주기 내 배치 묶음 번호|–|
|batch, code|최종제품 배치·제품 코드|–|
|tbl_speed|타정기 프레스 속도(정제/h)|tablets/hour|
|fom|충전 장치 회전 속도|rpm|
|main_comp|메인 압축력 평균|kN|
|tbl_fill|충전 깊이(정제심 체적)|mm|
|SREL|메인 압축력 상대표준편차|%|
|pre_comp|프리-압축력 평균|kN|
|produced|누적 양품 정제수|tablets|
|waste|누적 불량 정제수|tablets|
|cyl_main, cyl_pre|메인·프리 실린드리컬 높이|mm|
|stiffness|하부 펀치 강성|N|
|ejection|정제 배출력 최대값|N|

---

## **3. Process.csv (배치당 파생 특성)**

|**컬럼**|**의미**||
|---|---|---|
|tbl_speed_mean|0 값 제외 평균 프레스 속도||
|tbl_speed_change|속도 변동 횟수(배치 크기로 정규화)||
|tbl_speed_0_duration|속도 0 인 누적 시간(정규화, 주말 제외)||
|total_waste, startup_waste|배치 전체·시동 구간 불량 수(정규화)||
|weekend|주말 생산 여부(Yes/No)||
|fom_mean, fom_change|충전 속도 평균·변동 횟수||
|SREL_startup_mean, SREL_production_mean, SREL_production_max|SREL 시동 평균, 생산 평균·최대||
|main_CompForce_mean, …_sd, …_median|메인 압축력 평균·표준편차·중앙값||
|pre_CompForce_mean|프리 압축력 평균||
|tbl_fill_mean, tbl_fill_sd|충전 깊이 평균·표준편차||
|cyl_height_mean|실린더 높이 평균||
|stiffness_mean/max/min|하부 펀치 강성 평균·최대·최소||
|ejection_mean/max/min|배출력 평균·최대·최소||
|Startup_tbl_fill_maxDifference|시동 구간 충전 깊이 최대-최소 차||
|Startup_main_CompForce_mean, Startup_tbl_fill_mean|시동 구간 메인 압축력·충전 깊이 평균||

---

## **4. Normalization.csv**

|**컬럼**|**의미**|
|---|---|
|Product code|제품 코드(하위군)|
|Batch Size (tablets)|해당 하위군 목표 배치 크기(정제 수)|
|Normalisation factor|배치 크기에 따라 계산된 정규화 계수 (예: Batch Size ÷ 100 000) — 파생 특성 값을 배치 크기로 보정할 때 사용|
