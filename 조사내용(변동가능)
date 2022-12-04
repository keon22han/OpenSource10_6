#1인 가구를 위한 커뮤니티 서비스

*조사

## 데이터흐름도

![](https://github.com/hs-1971193-keonheehan/OpenSource10_6/blob/keonheehan/10_6DFD%EB%8D%B0%EC%9D%B4%ED%84%B0%ED%9D%90%EB%A6%84%EB%8F%84.JPG?raw=true)

**한건희-Search OpenSource**

### 1.**ElasticSearch 오픈소스 (Apache라이선스  V2.0) 를 이용**

(오프소스 기반의 분산 데이터베이스로 검색엔진으로 루씬(Lucene)을 밑바탕에 두며 RESTful API를 지원)

(ElasticSearch는 루씬(Lucene)검색 라이브러리 기반)

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
1.AliExpress DB에 접근하여 제품 데이터를 가져온 뒤
2.ElasticSearch 에서 검색 String를 이용하여 특정 컨텐츠 벡터 데이터(가구 데이터)들을 추출
3.추천 가구 리스트들과 관련된 이미지들을 크롤링하여 추천 리스트 & 이미지를 만들고 웹페이지로 전송
---




한수민- 쇼핑 구매 OpenSource

- Aliexpress API
- [https://developers.aliexpress.com/en](https://developers.aliexpress.com/en)
- [https://portals.aliexpress.com/help/help_center_API.html](https://portals.aliexpress.com/help/help_center_API.html)

1. Aliexpress API는 HTTP를 기반으로 호출해야 한다.
2. 특정 API를 호출하기 위해선 2가지의 선택지가 있다.
    	1) (추천) TOP에서 제공하는 공식 SDK를 사용하는 방법. 요청 캡슐화, 응답 해석등 다양한 기능을 이용할 수 있다.
    	2) TOP 프로토콜에 따라 HTTP 요청을 캡슐화 하는 방법.

![](https://img.alicdn.com/top/i1/LB1Q.YhmYYI8KJjy0FaXXbAiVXa)

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

![](https://tida.alicdn.com/oss_1615879444751_null_FqB19kT6.jpg)
![](https://tida.alicdn.com/oss_1634698965068_null_VEkLpY2P.jpg)

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


송형원 - 웹 구축 OpenSource

##스프링부트(SpringBoot)
웹 개발 OpenSource

[https://spring.io/projects/spring-boot]

LICENSE - Apache-2.0

#SpringBoot란?
자바 플랫폼을 위한 오픈소스 애플리케이션 프레임워크 Spring의 많은 부분을 자동화하여
사용자가 편하게 사용할 수 있게 한다. 실행환경 등 인프라 관련을 신경 쓸 필요 없이 코딩을 시작할 수 있다.

#스프링부트의 장점
-쉬운 접근
        -JAVA로 만든 서버 어플리케이션으로 JAVA로 개발하는 사람들이 쉽게 적응 가능
-설정의 자동화
        -프로젝트에 추가된 라이브러리를 기반으로 실행에 필요한 환경을 자동 설정
        -필요한 라이브러리 추가 시 관련된 스프링설정을 자동으로 정리
-라이브러리 버전관리
        -연관된 라이브러리들도 호환되는 버전으로 다운로드
-Emcedded Tomcat
        -Tomcat 서버 내장, 별도 설정없이 실행결과를 빠르게 확인가능
-독립적으로 실행가능한 JAR
        -웹 애플리케이션도 WAR이 아닌 JAR파일로 패키징하여 사용 가능

#스프링부트의 단점
-IT관리자의 능력에 따라 성능차이가 존재하고, 이슈 조치가 어렵다
-대용량 트래픽처리가 어려운 부분이 존재한다

#primavera

[https://github.com/csj4032/primavera](https://github.com/csj4032/primavera)

스프링부트 활용 커뮤니티 사이트 오픈소스

- 게시글 등록, 수정, 삭제, 조회 기능
- 게시글 답글 등록, 수정, 삭제 기능
- 게시글 댓글 등록, 수정, 삭제 기능 및 대댓글 등록, 수정, 삭제
- 게시글 관련 첨부파일 등록, 삭제
- 게시글 편집 기능

LICENSE - Apache-2.0



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



###한우창 - 로그인 서비스 오픈소스
(MIT License) 

https://github.com/react-native-seoul/react-native-kakao-login

기능
 
1. 로그인 화면 구성
2. 로그인 시 API키와 Redirect URL을 담아 카카오 서버로 인가 코드 요청
3. Redirect URL에 붙어온 토큰 발급 코드 split
4. 발급 코드를 담아 토큰 발급 요청 및 유효성 검증 
5. 로그인

###카카오 로그인 API

카카오 SDK는 Android, IOS, JavaScript, REST API 방식의 로그인API가 있으며, 각 방식에 따른 구현 가이드를 제공
REST API방식의 로그인 API를 기준으로 작성.
++카카오 로그인 API는 OAuth 2.0 방식으로 접근 권한을 제공.


**REST API -  주로 HTTP상 에서의 요청이 어떤 동작이나 정보를 위한 것인지 대해 구조를 파악할 필요없이 그 요청의 모습 자체로 기능을 추론할 수 있도록 만들어진 API를 의미.

**사전 준비 - 로그인 API를 사용하려면 https://developers.kakao.com/ 에서 개발자 등록 후 API사용 권한에 해당하는 API키를 발급이 요구됨.
	     - Redirect URL(인가 요청 시 발급될 코드를 받을)

**OAuth - 인터넷 사용자들이 각기 다른 웹사이트 상에서 접근 권한을 부여받을 수 있는 공통적인 수단으로서 사용되는 접근 위임을 의미.

- 도식화
![](https://developers.kakao.com/docs/latest/ko/assets/style/images/kakaologin/kakaologin_sequence.png)

##### 신의환-서버관리 OpenSource

# Prometheus

[https://github.com/prometheus/prometheus](https://github.com/prometheus/prometheus)

- 라이센스 : Apache 2.0 License
- 언어 : Go
- 메트릭 기반의 오픈소스 모니터링(관리) 시스템
    - 메트릭 : 일정한 시간동안 수집 된 일련의 순차적으로 정해진 데이터 셋의 집합(시계열 데이터)을 수집한 데이터
- PromQL이라는 강력하고 유연한 쿼리언어 사용, 실시간 경고 가능함
- 그라파나(Grafana)를 통한 시각화를 지원함
    - 그라파나 : 메트릭 데이터 시각화 오픈소스 도구
- 시스템으로부터 각종 지표를 수집, 저장, 검색 가능함
- Alertmanager라는 단독 알림 생성, 받기, 그룹지정, 조건지정 등 알림 관리 도구를 사용함
- 계층적, 수평적 구조 지원

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/de2bca76-5760-4a38-bec2-9cb1588a8625/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20221115%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20221115T144343Z&X-Amz-Expires=86400&X-Amz-Signature=f58212a87ab35e651f73fada4d2c47faee832179b559c182035acfd6d60531bd&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

아키텍쳐 개요

### 장점

- Pull 방식을 선택해 모든 정보를 중앙 서버로 보내지 않아도 됨.
- OS metric 뿐 아니라 제삼자의 exporter 역시 다양하게 제공함
- 데이터 저장소가 시계열 데이터 저장소라 많은 정보 빠르게 검색 가능함
- 구조가 간단함 ⇒ 특정 솔루션에 대한 export가 쉬움
- 일정 주기로 데이터를 수집하기에 앱에 무리가 가지 않음

### 단점

- 클러스터 구조가 불가능함, 계층적 구조기 때문이다.
- 싱글 호스트이기에 저장공간이 한 쪽에 부담된다
- 프로메테우스 서버가 어떤 이유로 비활성화 되었을 경우, 메트릭이 그동안 유실된다
- 모든 로그를 추적하기에는 적합하지 않다, pulling 할때의 스냅샷 정보만 알 수 있다.


