# 소개
기상청은 [공공데이터 포털](https://Data.go.kr)을 통해 기상예보 및 관측정보 등 다양한 서비스를 제공합니다.

본 패키지는 **Python3**를 기반으로 편리하게 **기상청API** 사용할 목적으로 배포하였으며 데이터 사이언스 분야에 많이 활용되는 **Numpy** 와 **Pandas** 를 사용합니다. 서비스별 상세 가이드는 공공데이터 포털을 참고해주세요.

(2023년 1월 28일 기준)
* [동네예보 조회서비스(VilageFcstInfoService2.0)](https://www.data.go.kr/data/15084084/openapi.do)
* [지상(종관, ASOS) 시간자료 조회서비스(AsosHourlyInfoService)](https://www.data.go.kr/data/15057210/openapi.do)
* [지상(종관, ASOS) 일자료 조회서비스(AsosHourlyInfoService)](https://www.data.go.kr/data/15059093/openapi.do)

  <details>
    <summary>(예정)</summary>
    * 중기예보 조회서비스(MidFcstInfoService)
    * 동네예보 통보문 조회서비스(VilageFcstMsgService)
    * 기상특보 조회서비스(WthrWrnInfoService)    
    * 생활기상지수 조회서비스(LivingWthrIdxService01)  
    * 태풍정보 조회서비스(TyphoonInfoService)  
    * 기상청_지진정보(EqkInfoService)  
    * 관광코스별 관광지 상세 날씨 조회서비스(TourStnInfoService)  
    * 위성영상 조회서비스(getInsightSatlit)  
    * 보건기상지수 조회서비스(HealthWthrIdxService)  
    * 레이더영상 조회서비스(RadarImgInfoService)  
    * 지상(방재, AWS)기상관측자료 조회서비스(Aws1miInfoService)  
    * CCTV 기반 도로날씨정보 조회서비스(RoadWthrInfoService)  
    * 낙뢰분포도 조회서비스(LgtDistrbInfoService)  
    * 작물별 농업주산지 상세날씨 조회서비스(FmlandWthrInfoService)  
    * 수치모델자료(경량화) 조회서비스(NwpModelInfoService)  
    * 위성자료(경량화) 조회서비스(WthrSatlitInfoService)  
    * 지상기상월보 조회서비스(SfcMtlyInfoService)  
    * 레이더관측자료 조회서비스(RadarObsInfoService)  
    * 일기도 조회서비스(WthrChartInfoService)  
    * 낙뢰관측자료 조회서비스(LgtInfoService)  
    * 항공기상전문(IWXXMVer.2.0) 조회서비스(AmmIwxxmService)  
    * 해양기상관측자료 조회서비스(OceanInfoService)  
    * 서리발생 가능성 예측정보 조회서비스(FrstFcstInfoService)  
    * 지상기상연보 조회서비스(SfcYearlyInfoService)  
    * 레이더자료(경량화) 조회서비스(WthrRadarInfoService)  
    * 방재기상월보 조회서비스(AwsMtlyInfoService)  
    * 해양기상월보 조회서비스(SeaMtlyInfoService)  
    * 항공기상전문 조회서비스(AmmService)_기상청에서 운영하는 관측지점, 기상예보구역, 기상특보구역 등에 대한 정보를 제공합니다. ※ 방재기상업무 수행을 위해 공공기관에 한해서 제공하는 자료입니다. 활용목적을 정확히 적어주시기 바랍니다.  
    * 지점정보(기상관측, 특보구역) 조회서비스(WethrBasicInfoService)  
    * 황사정보 조회서비스(YdstInfoService)_황사일기도, 황사관측값, 황사위성영상 정보를 조회하는 서비스 ※ 방재기상업무 수행을 위해 공공기관에 한해서 제공하는 자료입니다. 활용목적을 정확히 적어주시기 바랍니다.  
    * 고층기상월보 조회서비스(UppMtlyInfoService)  
    * 방재기상연보 조회서비스(AwsYearlyInfoService)  
    * 세계공항 항공기상전문 조회서비스(AftnAmmService)  
    * 고층기상관측자료 조회서비스(UppInfoService)  
  </details>

# 설치방법
## 의존성 패키지
***pip install requests*** or ***conda install -c conda-forge requests***  
***pip install pandas*** or ***conda install -c conda-forge pandas***  
***pip install lxml*** or ***conda install -c conda-forge lxml***  
***pip install numpy*** or ***conda install -c conda-forge numpy***  

## openKMA 설치
***pip install openKMA***

# 사용방법
## 사전준비
### API 인증키 발급
[공공데이터 포털](https://Data.go.kr)에 가입해서 원하는 서비스에 대하여 활용신청을 합니다.  
마이페이지에서 해당 서비스 정보를 확인하면 **"일반 인증키(Decoding)"** 항목이 표시됩니다.  
일반 인증키는 API의 **ServiceKey**로 사용됩니다.
## 서비스 사용방법
필요한 서비스 종류에 따라 **from** 을 사용해 아래와 같이 해당 **class**를 불러오실 것을 권장합니다.  

**from** openKMA **import** VilageFcstInfoService  
KMA = VilageFcstInfoService("일반 인증키(Decoding)를 복사해 넣으세요")


# 서비스 목록
<details>
  <summary><strong>1. 예보정보 관련 서비스</strong></summary>
    
  ## 1.1 동네예보 조회서비스(VilageFcstInfoService2.0)
  |서비스명|기능|인자|반환(item)|기타|
  |------|---|---|---|---|
  |예보버전조회|**getFcstVersion**|파일구분, 발표시각|DataFrame|'ODAM':실황/'VSRT':초단기예보/'SHRT':동네예보|
  |동네예보조회|**getVilageFcst**|X좌표, Y좌표, 발표시각|DataFrame|1일 8회 02시부터 3시간 간격으로 제공|
  |초단기예보조회|**getUltraSrtFcst**|X좌표, Y좌표, 발표시각|DataFrame|매시간 30분에 생성, 발표시각의 분은 30분|
  |초단기실황조회|**getUltraSrtNcst**|X좌표, Y좌표, 발표시각|DataFrame|매시간 30분에 생성, 발표시각의 분은 00분|

  * 모든 서비스는 24시간 이내에 자료만 조회가 가능하며 발표시각(baseDatetime)은 활용가이드를 참고
  * 동네별 X, Y좌표는 활용가이드 혹은 [기상자료개방포털](https://data.kma.go.kr/cmmn/main.do)의 자료실 참고

  ## 1.2 중기예보 조회서비스(MidFcstInfoService)
  |서비스명|기능|인자|반환(item)|기타|
  |------|---|---|---|---|
  |중기전망조회|**getMidFcst**|지점번호, 발표시각|DataFrame|중기전망 지점코드 참고|
  |중기기온조회|**getMidTa**|예보구역코드, 발표시각|DataFrame|중기기온 지점코드 참고|
  |중기육상예보조회|**getMidLandFcst**|예보구역코드, 발표시각|DataFrame|중기육상예보구역 코드 참고|
  |중기해상예보조회|**getMidSeaFcst**|예보구역코드, 발표시각|DataFrame|중기해상예보구역 코드 참고|
  * 중기예보는 모두 일 2회 (6시, 18시) 생산되며 최근 24시간 자료만 제공
  * 서비스별 지점 및 구역 코드는 해당 서비스의 [활용가이드](https://www.data.go.kr/data/15059468/openapi.do) 참고

  ## 1.3 동네예보 통보문 조회서비스(VilageFcstMsgService)
  |서비스명|기능|인자|반환(item)|기타|
  |------|---|---|---|---|
  |기상개황조회|**getWthrSituation**|발표관서|DataFrame|발표관서 참고|
  |육상예보조회|**getLandFcst**|예보구역코드|DataFrame|예보구역코드 참조|
  |해상예보조회|**getSeaFcst**|예보구역코드|DataFrame|예보구역코드 참조|
  * 동네예보 통보문은 모두 일 3회 (5시, 11시, 17시) 발표됩니다.
  * 통보문 발표시각(~조회시각): 5시(~11시), 11시(~17시), 17시(~다음날 5시)
  * 조회시간에 상관없이 가장 최근에 통보문만 조회됩니다.

</details>

___

<details>
  <summary><strong>2. 관측정보 관련 서비스</strong></summary>

## 2.1 지상(종관, ASOS) 시간자료 조회서비스(AsosHourlyInfoService)
|서비스명|기능|인자|반환(item)|기타|
|------|---|---|---|---|
|기상관측시간자료목록조회|**getWthrDataList**|지점번호, 시작시각, 종료시각|DataFrame|한 번에 최대 999개까지 조회 가능|

* 조회기간은 지점별 운영기간 모두 가능하며, 전날 자료까지만 조회가능합니다. 
* 단, 서버사정에 따라 갱신이 늦을 수 있습니다. (보통 오전 10시 이후 전부 조회 가능)
* 한 번에 최대 999개까지 조회되기 때문에 기간은 한 달이내로 설정해주시기 바랍니다.  
* (한 번 조회에 24시간을 권장합니다.)

## 2.2 지상(종관, ASOS) 일자료 조회서비스(AsosDalyInfoService)
사용예시: [tutorial_AsosHourlyInfoService.py](tutorial_AsosDalyInfoService.py)
|서비스명|기능|인자|반환(item)|기타|
|------|---|---|---|---|
|기상관측일자료목록조회|**getWthrDataList**|지점번호, 시작날짜, 종료날짜|DataFrame|한 번에 최대 999개까지 조회 가능|
* 조회기간은 지점별 운영기간 모두 가능하며, 전날 자료까지만 조회가능합니다. 
* 단, 서버사정에 따라 갱신이 늦을 수 있습니다. (보통 오전 10시 이후 전부 조회 가능)
* 한 번에 최대 999개까지 조회되기 때문에 기간은 2년 이내로 설정해주시기 바랍니다.  

</details>

---

<details>
  <summary><strong>3. 위성 및 레이더 관련 서비스</strong></summary>
  (예정)
</details>

---

<details>
  <summary><strong>4. 수치예보 관련 서비스</strong></summary>
  (예정)
</details>

---

<details>
  <summary><strong>5. 특보 및 지진/태풍 관련 서비스</strong></summary>

## 5.1 기상특보 조회서비스(WthrWrnInfoService)
|서비스명|기능|인자|반환(item)|기타|
|------|---|---|---|---|
|기상특보목록조회|**getWthrWrnList**|지점코드, 시작날짜, 종료날짜|DataFrame|-|
|기상특보통보문조회|**getWthrWrnMsg**|지점번호, 시작날짜, 종료날짜|DataFrame|-|
|기상정보목록조회|**getWthrInfoList**|지점번호, 시작날짜, 종료날짜|DataFrame|-|
|기상정보문조회|**getWthrInfo**|지점번호, 시작날짜, 종료날짜|DataFrame|-|
|기상속보목록조회|**getWthrBrkNewsList**|지점번호, 시작날짜, 종료날짜|DataFrame|-|
|기상속보조회|**getWthrBrkNews**|지점번호, 시작날짜, 종료날짜|DataFrame|-|
|기상예비특보목록조회|**getWthrPwnList**|지점번호, 시작날짜, 종료날짜|DataFrame|-|
|기상예비특보조회|**getWthrPwn**|지점번호, 시작날짜, 종료날짜|DataFrame|-|
|특보코드조회|**getPwnCd**|지점번호, 시작날짜, 종료날짜,<br>특보구역코드, 특보종류|DataFrame|1:강풍, 2:호우, 3:한파, 4:건조, 5:폭풍해일,<br>6:풍랑, 7:태풍, 8:대설, 9:황사, 12:폭염|
|특보현황조회|**getPwnStatus**| - |DataFrame|-|
* 특보는 오늘을 기준으로 6일 전 자료까지만 조회됩니다.
* 조회기간 동안 특보가 없을 시 빈(Empty) DataFrame을 받습니다. 
* [기상청21_기상특보 조회서비스_오픈API활용가이드_특보구역코드 해당 지점](METADATA/기상청21_기상특보&#32;조회서비스_오픈API활용가이드_특보구역코드&#32;해당&#32;지점.csv)  
* [기상청21_기상특보 조회서비스_오픈API활용가이드_특보구역코드안내(200515)](METADATA/기상청21_기상특보&#32;조회서비스_오픈API활용가이드_특보구역코드안내(200515)/)  
* [기상청21_기상특보 조회서비스_오픈API활용가이드](DOCUMENT/기상청21_기상특보&#32;조회서비스_오픈API활용가이드.docx)

</details>

---

<details>
  <summary><strong>6. 생활 및 산업 관련 서비스</strong></summary>
  (예정)
</details>

---

<details>
  <summary><strong>7. 기타</strong></summary>
  (예정)
</details>

---

# 참고
+ [공공데이터 포털](https://www.data.go.kr/)
+ [기상자료개방포털](https://data.kma.go.kr/cmmn/main.do)
+ [기상청(Korea Meteorological Administration)](http://www.kma.go.kr/)

# 감사드리는 분
부족하지만 항상 따뜻하게 대해주시고, 함께 고민해주시는 분들께 감사의 마음을 전합니다.
+ 충남대학교 천문우주학과 대기과학 교수님 및 연구원들
+ 공주대학교 대기과학과 교수님 및 동기, 선후배님들
+ 공주대학교 대기과학과 환경방 형님들
+ 대전지방기상청 아무개
+ 기상청 국가기후데이터센터 아무개