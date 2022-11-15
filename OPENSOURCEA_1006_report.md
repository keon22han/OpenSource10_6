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



최현진 -  빅데이터 오픈 소스

Graylog

- 연결되어있는 로그들의 정보를 수집, 분석하여 결과를 출력해주는
로그 집중화 기능을 가지고 있는 오픈 소스 툴
- 가장 유명한 오픈소스 로그 관리 플랫폼
- 완전 무료 오픈소스, 유료 지원도 가능
- 제공사 : graylog
- 아키텍쳐 : 엘라스틱서치의 뛰어난 로그 수집/분석 능력에 주목하여

그레이로그 어플리케이션의 메타 정보는 MongoDB에,

수집되는 로그 데이터는 모두 엘라스틱서치에 보관함



Graylog를 이용하여 Graylog를 이용하여 사용자가 웹 사이트를 이용하면서 남긴

사용자가 웹 사이트를 이용하면서 남긴 로그 데이터 (ex: 장바구니 담기, 결제, 

홈 화면 클릭 등)를 기반으로 개별 사용자들의 성향을 파악하여 

고객들이 원하는 맞춤 서비스(ex: 사용자의 취향을 고려한 인테리어 추천, 

인테리어 용품 추천 등)를 제공하고자 한다.



# 채팅

1. react-native-gifted-chat
   
    →[https://github.com/FaridSafi/react-native-gifted-chat](https://github.com/FaridSafi/react-native-gifted-chat)
    
    →MIT License 
    
2. firebase (채팅+푸시 알람 모두 가능) 
   
    →[https://firebase.google.com/docs?hl=ko](https://firebase.google.com/docs?hl=ko)
    
    →platform 형태 
    
    →인증. 데이터베이스, 스토리지, 원격 구성, 푸시 알람 등 한 번에 가능 
    

# 푸쉬알림

1. ntfy
   
    →[https://github.com/binwiederhier/ntfy](https://github.com/binwiederhier/ntfy)
    
    →Apache 2.0 and GPLv2 License 
    
2. apprise
   
    →[https://github.com/caronc/apprise](https://github.com/caronc/apprise)
    
    →MIT License 
    
    →Apprise() 객체가 모든 것을 처리 하고,  AppriseAsset() 객체를 사용하여 일부 기본 구성에서 벗어나 사용자 경험을 개인화
    
    →비동기식 전송으로 응답시간 빠름





##### 송지환 - 위치기반서비스 OpenSource, API

사용 오픈소스: **Swift Location**

사용 오픈API:  **Google Maps Platform API(Google Maps API, Google Place API)**

## 1. Swift Location 오픈소스 - (MIT LICENSE)

 ##### Swift Location은 사용자의 위치 관련 기능들을 쉽게 사용 할 수 있는 MIT LICENSE 오픈소스 입니다. 언어는 Swift를 사용합니다. 

[malcommac/SwiftLocation: 🛰 CoreLocation Made Easy - Efficient & Easy Location Tracker, IP Location, Gecoder, Geofence, Autocomplete, Beacon Ranging, Broadcaster and Visits Monitoring (github.com)](https://github.com/malcommac/SwiftLocation#autocomplete)

#### 기능

1. GPS를 통해서 사용자의 위치를 가져 올 수 있습니다. - **(아래 예시, Swift 사용)**

   ```swift
   SwiftLocation.gpsLocation().then {
       print("Location is \($0.location)")
   }
   ```

   

2. 주소, 장소에 대해서 검색 시에 자동완성 기능을 제공합니다.

3. 자주 방문한 곳에 대해서 위치 모니터링 서비스를 제공합니다.

4. 프로그램(앱)이 실행되지 않는 사이에도 마지막으로 알려진 위치를 자동으로 저장합니다.

5. 좌표(위도,경도)에서 주소를 가져 올 수 있고, 반대로 주소를 통해 좌표를 얻을 수 있습니다.

   ##### (Google Map 사용, 지오코딩 예시, Swift사용)

   ```swift
   let service = Geocoder.Google(lat: 37.331656, lng: -122.0301426, APIKey: "<your api key>")
   SwiftLocation.geocodeWith(service).then { result in
       // Different services, same expected output [GeoLocation]
       print(result.data)
   }
   ```

   

#### GeoCoding (지오코딩)

지오코딩이란, 고유명칭(장소)를 가지고 좌표(위도,경도)를 얻는 것을 뜻합니다.

SwiftLocation에서의 지오코딩 기능은 **Google Maps Platform API**와 연동되어 있습니다. 구글 맵 플랫폼에는 구글 맵 관련 다양한 API들을 단순히 Key발급을 통해서 쉽게 이용이 가능합니다. (사용하는 기능에 따라 어느정도의 과금이 요구됨). 이때 사용하는 언어는 많이 사용하는 언어인 Python, Java, JavaScript, Go 등을 사용합니다. 



#### 지오코딩 기능 사용과정

**Google Maps API**에서 key를 발급받고, GoogleMap 패키지를 다운받습니다. 이제 특정 장소를 위도, 경도를 입력하면, 해당 지역 근처에 있는 장소들을 띄워줍니다. 만약, 우리가 찾는 가구점과 인테리어점들이 구글맵에 등록이 안되어 있다면, Google Map API의 마커등록을 통해서 지도에 원하는 위치에 장소를 도식 가능합니다.  EX. JavaScript 기준으로 google.mapss.Marker() 생성자 함수 사용.

##### 마커등록 사용 예시_JavaScript사용 - (동대문 쇼핑몰을 지도에 등록)

```javascript
window.initMap = function () {
  const map = new google.maps.Map(document.getElementById("map"), {
    center: { lat: 37.5400456, lng: 126.9921017 },
    zoom: 10,
  });

  const malls = [
    { label: "C", name: "코엑스몰", lat: 37.5115557, lng: 127.0595261 },
    { label: "G", name: "고투몰", lat: 37.5062379, lng: 127.0050378 },
    { label: "D", name: "동대문시장", lat: 37.566596, lng: 127.007702 },
    { label: "I", name: "IFC몰", lat: 37.5251644, lng: 126.9255491 },
    { label: "L", name: "롯데월드타워몰", lat: 37.5125585, lng: 127.1025353 },
    { label: "M", name: "명동지하상가", lat: 37.563692, lng: 126.9822107 },
    { label: "T", name: "타임스퀘어", lat: 37.5173108, lng: 126.9033793 },
  ];
  malls.forEach(({ label, name, lat, lng }) => {
    const marker = new google.maps.Marker({
      position: { lat, lng },
      label,
      map: map,
    });
  });
};
```



### Google Places API (주변 가게들 리뷰, 댓글 확인 기능)

사용자가 주변 가구점 및 인테리어점에 대해서, 리뷰, 댓글 등을 확인할 수 있는 서비스를 제공하기 위해 Google Places API를 사용합니다. Places API는 HTTP 요청을 사용해서 장소에 관한 정보를 반환하는 서비스 입니다. 이 API 내에서 장소는 각각의 고유한 ID가 부여되어 구별됩니다.  Places api사용은 위의 구글맵api 사용과 유사하게, 키를 발급받고 서비스에 따라 돈을 지불하면 사용이 가능합니다.



##### google places api 기능

1. **장소 검색**- 사용자의 위치 또는 검색 문자열을 기준으로 장소 목록을 반환함.
2. **장소 세부정보**- 사용자 리뷰, 댓글을 비롯하여 특정 장소에 대한 자세한 정보를 반환함
3. **장소 자동완성**- 사용자가 검색 시, 장소의 이름 혹은 주소를 자동완성 해준다.
4. **추천검색어**- 쿼리 예측 서비스로 인해 사용자가 입력하면 추천 검색어를 반환한다.



