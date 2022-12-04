### 3. 오픈 소스 소개 - 3.9 MongoDB

MongoDB는 C++로 작성된 오픈 소스 Document-Oriented, NoSQL 데이터 베이스로 SSPL License입니다. MongoDB는 Collection 안의 Document에 데이터를 저장합니다. Document의 Field 안의 데이터 형식이 서로 달라도 입력이 가능하고, 각 Document들이 일관된 Field를 가지지 않아도 되기 때문에 비정형 데이터를 저장하기에 좋습니다.

![img](https://www.mongodb.com/assets/images/mongodb-architecture/image_diagram_platform_kr.png)

- 서버 장애에도 서비스는 계속 동작하기 때문에 신뢰성(Reliability)을 가집니다.
- 데이터와 트래픽 증가에 따라 수평확장(scale-out)을 할 수 있어 확장성이 좋습니다.
- 여러가지 형태의 데이터를 손쉽게 저장할 수 있는 유연성(Flexibility)을 가집니다. 서비스 요구사항에 맞춰 다양한 종류의 데이터가 추가되어도 스키마 변경 과정 없이 필요한 데이터를 바로 저장하고 읽을 수 있습니다.
- Index 지원(Index Support)으로 다양한 조건으로 빠른 데이터 검색이 가능합니다.



MongoDB는 GrayLog의 구성요소 중 하나로 GrayLog로부터 전달받은 환경정보, 메타 데이터를 저장합니다.

