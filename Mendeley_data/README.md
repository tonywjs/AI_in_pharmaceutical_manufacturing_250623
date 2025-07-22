### **데이터셋 개요**

- **정식 이름**: **Big Data – Biopharmaceutical Manufacturing**
    
- **출처 / 저자**: Stephen Goldrick (UCL) 외 연구진. Kaggle·Mendeley Data에 공개.
    
- **기원**: 산업 규모(100 000 L) 페니실린 배양을 모사한 **IndPenSim V2** 시뮬레이션에서 생성된 100 batch의 공정 로그와 라만(Raman) 스펙트럼 데이터. 
    
- **규모**
    
    - 약 2.5 GB, 113 935 행(시간 단위 샘플)
        
    - 2 239 열
        
        - 0 – 37 열: 공정·품질 변수(온라인/오프라인 측정)
            
        - 38 – 2 238 열: 900 여 파장대의 라만 스펙트럼 강도
            
        
    
- **배치 구분**
    
    - Batch 1–30: 레시피 기반 제어
        
    - Batch 31–60: 숙련 오퍼레이터 수동 제어
        
    - Batch 61–90: 라만-기반 고급 공정제어(APC)
        
    - Batch 91–100: 의도적 결함-시나리오 삽입 
        
    

  

이 데이터는 **대량 배양 공정의 모니터링·제어 알고리즘, 소프트센서, 시계열 예측, 결함 감지** 연구에 자주 활용됩니다.

---

### **주요 컬럼(1 – 37열) 상세 설명**

|**#**|**컬럼명 (단위)**|**의미**|**비고**|
|---|---|---|---|
|1|**Time (h)**|공정 시간 (0 – ~290 h)|시뮬레이션 내부 clock|
|2|**Aeration rate(Fg:L/h)**|균체 호흡용 공기 유량||
|3|**Agitator RPM(RPM:RPM)**|교반기 회전수|시뮬레이션에서는 100 RPM 고정|
|4|**Sugar feed rate(Fs:L/h)**|설탕(탄소원) 공급 속도||
|5|**Acid flow rate(Fa:L/h)**|pH 하향용 산 주입 유량||
|6|**Base flow rate(Fb:L/h)**|pH 상승용 알칼리 주입 유량||
|7|**Heating/cooling water flow rate(Fc:L/h)**|배양액 온도 조절용 물 유량||
|8|**Heating water flow rate(Fh:L/h)**|가열전용 온수 유량||
|9|**Water for injection/dilution(Fw:L/h)**|희석·세정용 주사용수 유량||
|10|**Air head pressure(pressure:bar)**|발효조 상부 공기 압력||
|11|**Dumped broth flow(Fremoved:L/h)**|배지 제거(배출) 유량|음수 = 배출|
|12|**Substrate concentration(S:g/L)**|잔존 기질(탄소원) 농도||
|13|**Dissolved oxygen concentration(DO2:mg/L)**|용존산소 농도||
|14|**Penicillin concentration(P:g/L)**|즉시 측정된 페니실린 농도|온라인 센서|
|15|**Vessel Volume(V:L)**|실시간 배양액 체적||
|16|**Vessel Weight(Wt:Kg)**|실시간 발효조 무게|체적×밀도|
|17|**pH(pH:pH)**|배지 pH||
|18|**Temperature(T:K)**|배양 온도|297–299 K|
|19|**Generated heat(Q:kJ)**|대사·교반 등으로 발생한 열||
|20|**carbon dioxide percent in off-gas(CO2outgas:%)**|배기 중 CO₂||
|21|**PAA flow(Fpaa:PAA flow (L/h))**|전구체(phenylacetic acid) 주입 유량||
|22|**PAA concentration offline(PAA_offline:PAA (g L^{-1}))**|오프라인 분석 PAA 농도|결측 많음|
|23|**Oil flow(Foil:L/hr)**|거품 방지용 오일 유량|23 L h⁻¹ 고정|
|24|**NH_3 concentration off-line(NH3_offline:NH3 (g L^{-1}))**|오프라인 암모니아 농도||
|25|**Oxygen Uptake Rate(OUR:(g min^{-1}))**|Oxygen Uptake Rate|생물학적 호흡 속도|
|26|**Oxygen in percent in off-gas(O2:O2  (%))**|배기 중 O₂||
|27|**Offline Penicillin concentration(P_offline:P(g L^{-1}))**|실험실 샘플 분석값||
|28|**Offline Biomass concentratio(X_offline:X(g L^{-1}))**|건조세포량(DCW)||
|29|**Carbon evolution rate(CER:g/h)**|CO₂ 배출 속도||
|30|**Ammonia shots(NH3_shots:kgs)**|간헐적 NH₃ 주입량|대부분 0|
|31|**Viscosity(Viscosity_offline:centPoise)**|배양액 점도(centipoise)||
|32|**Fault reference(Fault_ref:Fault ref)**|0 = 정상, 1 = 결함주입||
|33|**0 - Recipe driven 1 - Operator controlled(Control_ref:Control ref)**|제어 방식 참조|0=레시피 기반, 1=운전자 제어|
|34|**2-PAT control(PAT_ref:PAT ref)**|PAT 제어 참조|라만 기반 고급공정제어|
|35|**Batch reference(Batch_ref:Batch ref)**|배치 참조 번호||
|36|**Batch ID**|배치 식별자||
|37|**Fault flag**|결함 플래그|추가 결함 표시|

> **라만 스펙트럼 열(38 – 2239)**

- > 미세 파장(400–1800 cm⁻¹ 등) 별 스펙트럼 강도가 저장되어 있어 **실시간 화학 성분 모니터링**·소프트센서 개발에 사용됩니다. 
    

---

### **파일 단위 요약**

| **파일**                                | **내용**                                                            |
| ------------------------------------- | ----------------------------------------------------------------- |
| **100_Batches_IndPenSim_V3.csv**      | 전체 시계열 + 라만 스펙트럼 (2239 열)                                         |
| 100_Batches_IndPenSim_V3_no_raman.csv | 라만 스펙트럼 컬럼을 제거한 공정 데이터만 포함 (37 열)                                 |
| 100_Batches_IndPenSim_Statistics.csv  | 배치별 제품 수율·결함 플래그 5 열 요약 표                                         |

---

#### **활용 팁**

1. **라만 열은 고차원**이므로 PCA, UMAP 등 차원 축소 후 사용하거나 특정 파장대만 선택.
    
2. **배치 구간별 제어 전략**이 다르므로 모델링 전에 Batch ref를 기준으로 **훈련·검증 집합을 층화**하는 것이 좋습니다.
    
3. 결측률이 높은 오프라인 변수(PAA_offline 등)는
    
    - **보간/추정**하거나
        
    - 제외하고 온라인 변수+라만 스펙트럼으로 소프트센서 구축 가능.
        
    

  