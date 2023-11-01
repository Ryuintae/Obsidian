

## OGC 란? (Open Geospatial Consortium)

공간정보 관련 기술의 개방형 표준화를 개발하고 구현하는 국제 표준화 기구이다.

OGC 에서 공간정보 질의 표준을 정의 한 것이  OGC 표준이다. 
공간 정보와 관련된 소프트웨어, 웹, 앱 등이 OGC 표준을 준수한다면, 어떤 형태든 동일한 요청 방식으로 데이터를 제공 받을 수 있다.
즉, OGC 표준을 준수한다면 서비스의 일관성을 지킬 수 있다.

==한번 잘 알아두면 OGC 표준을 준수하는 모든 서비스에서 동일하게 활용이 가능하다.==

### 웹 환경에서의 OGC 표준 주요 항목

* WFS   (Web Feature Service) : 벡터 데이터의 속성 및 공간 정보
* WMS (Web Map Service) : 배경지도 및 시각화
* WCS  (Web Coverage Service) : 래스터 데이터 추출
* WPS  (Web Processing Service) : 공간 분석 처리

**가장 사용 빈도가 높은건 WFS , WMS 이다 


## WFS 

WFS의 주요 명령어
1. GetFeature
2. Transaction

기본 URL은 https:// example.com/geoserver/wfs

## WMS

WMS 주요 명령어
1.  GetMap
2. GetFeatureInfo

기본 URL은 https:// example.com/geoserver/wms