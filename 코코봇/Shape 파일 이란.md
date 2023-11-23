
shape파일은 지리정보시스템(GIS) 분야 등에서 주로 사용하는 파일 포맷으로 위치 기반의 벡터정보(점, 선, 다각형 등)을 표현하기 위해서 사용된다.

지리정보는 현재 자율주행의 발전과 더불어 기반 시스템으로 빠르게 변화하고 있다.

위키 정보를 기반으로하여 shape에 대하여 정리한다.

shape은 arcgis를 만든 ESRI에서 사용하기 시작하였고, 현재는 업계의 반표준으로 널리 사용되고 있다.

shape은 지리정보를 표현하기 위해 아래의 파일들로 구성된다.

하나의 파일이 아니라 여러 개의 파일이며, 확장자에 따라 구분된다.

**필수파일**

- *.shp - 기하학적 지리 정보 (데이터)
- *.shx - 기하학적 지리 정보의 인덱스
- *.dbf - 속성 정보

**그외 파일** (파일들을 본 적이 없어서 종류만 나열한다.)

- *.prj - 투영 정보 (projection description)
- *.sbn, *.sbx
- *.fbn, *.aih
- *.ixs
- *.mxs
- *.atx
- *.shp.xml
- *.cpg
- *.qix

#### Shapefile shape format (*.shp)

논리적 구조는 아래와 같다.

- header
    - 100바이트로 고정되어 있으며, 17개 필드를 포함하고 있다. (파일정보)
    - 포함된 주요 정보는 아래와 같다.
        - 파일코드, 파일길이, 버전, shape타입, shape의 x, y, z, m 범위
- record
    - record-header
        - 8바이트의 레코드 헤더 - record number + record length
    - record-contents
        - 가변길이의 실제 기하학 데이터
            - shape type(4byte) + shape content
            - shape type은 아래와 같다. 
                - Null shape(0), Point(1), Polyline(3), Ploygon(5), MultiPoint(8), PointZ(11), PolylineZ(13),   
                    PolygonZ(15), MultiPointZ(18), PointM(21), PolylineM(23), PolygonM(25), MultiPointM(28), MultPatch(31)

#### Shapefile shape index format(*.shx)

shp와 동일한 100byte의 header와 8byte 고정길이의 2필드(record offset + record length)로 구성된다.

shp, dbf의 색인(index) 역할을 한다.

#### Shapefile attribute format(*.dbf)

각 feature에 대한 속성값을 저장한다.

dBase IV 형식을 사용한다.

[en.wikipedia.org/wiki/Shapefile](https://en.wikipedia.org/wiki/Shapefile)


https://xground.pe.kr/71

ddd