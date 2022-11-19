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

한수민- 쇼핑 구매 OpenSource

- Aliexpress API
- [https://developers.aliexpress.com/en](https://developers.aliexpress.com/en)
- [https://portals.aliexpress.com/help/help_center_API.html](https://portals.aliexpress.com/help/help_center_API.html)

1. Aliexpress API는 HTTP를 기반으로 호출해야 한다.
2. 특정 API를 호출하기 위해선 2가지의 선택지가 있다.
    	1) (추천) TOP에서 제공하는 공식 SDK를 사용하는 방법. 요청 캡슐화, 응답 해석등 다양한 기능을 이용할 수 있다.
    	2) TOP 프로토콜에 따라 HTTP 요청을 캡슐화 하는 방법.

![]([https://img.alicdn.com/top/i1/LB1Q.YhmYYI8KJjy0FaXXbAiVXa](https://img.alicdn.com/top/i1/LB1Q.YhmYYI8KJjy0FaXXbAiVXa))

3. Aliexpress 와의 통합
	1) Aliexpress 플랫폼에 등록 (판매자 계정, 개발자 등록) → 앱 생성 완료
    	2) 사용자의 개인 데이터(ex : 제품, 주문)와 오픈 플랫폼을 연결하기 위해선 사용자의 데이터에 접근할 수 있는 엑세스 토큰이 필요하다.
     	   → Oauth 2.0 프로토콜 사용 (서버측, 클라이언트 측 프로세스의 2가지 액세스 토큰 획득 방법 지원)
     	   : 표준 사용자 인증 프로토콜로 사용자가 인터넷 서비스의 기능을 다른 애플리케이션에서도 사용할 수 있도록 한 것이다. 사용자의 인증, 권한 부여 등을 지원한다. 
        
4. 제품 관리
	1) Aliexpress 카테고리를 얻고, 카테고리 매핑을 수행한다.
	2) 판매자의 경우 필요한 브랜드의 허가를 신청한다.
	3) 배송 템플릿을 설정한다.
	4) (필요에 따라) 사이즈 차트 템플릿 설정
	5) ( 제품 게시 및 편집시 사용하는 방법 )
	-> Product schema 사용 : 제품의 필드, 옵션등을 정의하기 위한 JSON 타입의 사양이다. 하나의 API 만으로도 제품의 모든 정보를 쉽게 가져올 수 있다. 
        
    
5. 주문 과정

![]([https://tida.alicdn.com/oss_1615879444751_null_FqB19kT6.jpg](https://tida.alicdn.com/oss_1615879444751_null_FqB19kT6.jpg))
![]([https://tida.alicdn.com/oss_1634698965068_null_VEkLpY2P.jpg](https://tida.alicdn.com/oss_1634698965068_null_VEkLpY2P.jpg))

	1) 주문 목록을 받는다.
	2) 목록을 반복한다.
	3) 주문 ID를 포함해 정보를 받는다. 판매자가 구매자에게 주문을 물리적으로 이행하는 단계이다.
	4) 운송업체의 이름을 받는다. 
	5) Aliexpress에서 주문을 이행한다.
		a. order id로 온라인 물류 서비스 목록을 가져온다.
		b. 파라미터를 기반으로 창고에 주문을 생성한다. (경우에 따라)
		c. 국제 물류 번호를 받는다.
		d. 국제 물류 번호로 인쇄 정보를 받는다. (창고에 주문이 생성된 경우)
	6) 판매자로부터 구매자가 제품을 받는다.