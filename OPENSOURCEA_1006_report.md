#1인 가구를 위한 커뮤니티 서비스

*조사

한건희-Search OpenSource
### 1.**ElasticSearch 오픈소스 (Apache라이선스  V2.0) 를 이용**

(오프소스 기반의 분산 데이터베이스로 검색엔진으로 루씬(Lucene)을 밑바탕에 두며 RESTful API를 지원)

(ElasticSearch는 루씬(Lucene)검색 라이브러리 기반)

- WordPress(GPL V3.0)이용시 결합 가능
- Query컨텍스트를 이용한 랭킹 검색
- Filter컨텍스트를 이용한 단어 위주 검색
- Query , Filter는 역색인 기능에 해당한다
- 유의어 , 동의어 기능에 대해 알아보면 좋을것으로 예상
- 문서는 JSON 형식으로 저장됨

▶ **Query 컨텍스트** -Query 컨텍스트는 문자열에 대한 검색결과의 score 을 판단함. 즉 조건을 만족하는 레코드를 찾는 개념을 넘어 가장 적합하고 유사성 높은 결과를 찾는 개념이므로 우리가 만들고자 하는 검색기능에 최적화 되어있음

▶ **Filter 컨텍스트** -필터링은 검색된 문서들에 대한 **score** 계산을 하지 않기 때문에 쿼리검색보다 빠름. 따라서 활용방식에 따라 검색 성능을 높일 수 있음. (카테고리 선택 기능으로 넣을 수 있음)

score 계산이란 검색결과의 정확도인데 , 이 정확도를 계산하는 대표적인 알고리즘으로는 BM25알고리즘이 존재

**※ 역색인 기능** 이란?

일반적인 색인의 목적은 ‘문서의 위치’에 대한 index를 만들어서 빠르게 그 문서에 접근하고자 하는 것인데, 역색인은 반대로 ‘문서 내의 문자와 같은 내용물’의 맵핑 정보를 색인해놓는 것

- 만약 일반적인 DB에서 “Trade”라는 문구가 포함된 문자열을 찾으려고 한다면 SQL에서는 %Trade% 라고 명확히 입력해야 검색이 가능하고 trade, TRADE, trAde…. 등의 문자열은 직접 하나하나 명시하기 전에는 찾을 수 없다. ES의 역색인을 활용하면 대소문자 구분 없이 어떤 문구가 들어와도 찾을 수 있다.

---

**데이터 처리 . . .(저장과 불러오는 용도(?) 일단은(?) )**

▶ **Hadoop**(Apache License V2.0을 사용) RDBMS 에 비하여 비용적인 측면에서 유리

(사용자 검색 로그 등 애매한 비정형 데이터)

● **파일 저장 플로우 방식**으로 Hadoop에 데이터 저장 요청

-요청 절차

1. 어플리케이션이 HDFS 클라이언트에게 파일 저장을 요청합니다. 클라이언트는 네임 노드에게 파일 블록들이 저장될 경로 생성을 요청하고, 네임 노드는 해당 파일 경로가 존재하지 않으면 경로를 생성하고 다른 클라이언트가 해당 경로를 수정하지 못하게 lock을 시킵니다. 이후 네임노드는 클라이언트에게 해당 파일 블록들을 저장할 데이터 노드의 목록을 반환
2. 클라이언트는 첫번째 데이터 노드에게 데이터를 전송
3. 첫번째 데이터 노드는 데이터를 로컬에 저장합니다. 저장한 뒤 두번째 데이터 노드로 전송
4. 두번째 노드도 마찬가지로 로컬에 저장하고, 세번째 데이터 노드로 전송
5. 세번째 노드에서 마지막으로 로컬에 저장이 완료되면 두번째 데이터 노드에게 로컬 저장이 완료됨을 응답(ack)
6. 두번째 노드에서는 세번째 노드에서 온 응답을 통하여 첫번째 데이터 노드에게 응답(ack)
7. 첫번째 데이터 노드에서는 클라이언트에게 데이터 저장이 완료되었음을 응답

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FlYY1B%2FbtreRTHhoHB%2FgGVqSl99pcljzoYEMnLi40%2Fimg.png)

● **파일 읽기 플로우 방식**으로 Hadoop에 저장된 데이터를 요청

-요청 절차

1. 어플리케이션이 HDFS 클라이언트에게 파일 읽기 요청
2. 클라이언트는 네임 노드에게 요청된 파일이 어떤 블록에 저장되어있는지 정보를 요청
3. 메타 데이터를 통해 파일이 저장된 블록 리스트를 클라이언트에게 반환
4. 클라이언트는 데이터 노드에 접근하여 블록 조회를 요청
5. 데이터 노드는 클라이언트에게 요청된 블록을 전송
6. 클라이언트는 어플리케이션에 조회된 데이터를 전송

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FcqxSq8%2FbtreYo66xxo%2F6SOrR9pepNReOPP8FOQ0K0%2Fimg.png)

한수민- 가구배치 OpenSource

- Floor planner2D
- [https://github.com/CanKavaloglu/floorplanner2D](https://github.com/CanKavaloglu/floorplanner2D)
- MIT라이센스
1. 바닥 평면도를 본인이 직접 디자인 할 수 있고, 미리 만들어진 디자인을 확장하여 설계하는 것도 가능하다.
2. 다양한 카메라 각도로 제작한 평면도를 볼 수 있다. 
3. 2차원 평면도에서 3차원 모델을 자동으로 생성해준다.
4. 카탈로그에 다양한 가구들이 있고, 본인이 직접 개체를 추가하는 것이 가능하다.

- Floorplanner (아예 오픈되어있는 소프트웨어인데 어떻게 사용할 수 있을지 모르겠습니다ㅠ)
- [https://floorplanner.com/](https://floorplanner.com/)
- [https://github.com/floorplanner](https://github.com/floorplanner)
- 라이센스 (?)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3242c01b-9d78-458d-b5b6-58640a03c466/Untitled.png)

1. 위의 오픈소스와 기능은 비슷합니다. (아래는 추가사항)
2. Drag&Drop 인터페이스를 웹 브라우저에서 제공한다.
3. 라이브러리에 업로드할 수 있고, 클라우드 동기화도 가능하다.

- ARKit
- [https://github.com/ignacio-chiazzo/ARKit](https://github.com/ignacio-chiazzo/ARKit)
- MIT라이센스
- 실제 AR기반 가구배치 오픈소스(가구가 한정적)

송형원 - 웹 구축 OpenSource

# primavera

[https://github.com/csj4032/primavera](https://github.com/csj4032/primavera)

스프링부트 활용 커뮤니티 사이트

- Social 정보를 이용한 회원 가입
- Social 정보를 이용한 로그인, 로그아웃, 탈퇴
- 게시글 등록, 수정, 삭제, 조회 기능
- 게시글 답글 등록, 수정, 삭제 기능
- 게시글 댓글 등록, 수정, 삭제 기능 및 대댓글 등록, 수정, 삭제
- 게시글 관련 첨부파일 등록, 삭제
- 게시글 편집 기능

LICENSE - Apache-2.0

# Web_Community_Project

[https://github.com/youjeonghan/Web_Community_Project](https://github.com/youjeonghan/Web_Community_Project)

회원가입, 로그인, 게시글, 댓글 등의 기본적인 기능을 제공하는 커뮤니티 사이트 오픈소스입니다.

하지만 라이선스가 명시되어있지 않아 스프링부트관련 소스를 사용하는것이 좋아보입니다.

# Ultimatemember

[https://github.com/ultimatemember/ultimatemember](https://github.com/ultimatemember/ultimatemember)

Wordpress의 프로필/로그인 관련 플러그인 오픈소스입니다.

관련 주제로 찾다가 혹시 필요할 까 싶어서 일단 올려놨습니다.

LICENSE - GPL-2.0