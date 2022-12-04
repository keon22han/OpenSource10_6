
# **오픈소스 소프트웨어 10_6조 시스템 설계서**

### <1인 가구를 위한 인테리어 서비스>











Document ID    :  SYSTEM DESIGN - V 0.1
Version Number :  0.1
Issue Date     :  December 04, 2022
Classification :  Public

------

## 조원 정보 
* 한건희
* 송지환
* 신승혜
* 한수민
* 한우창
* 송형원
* 신의환
* 최현진

------

## 목차

1. 서비스 설명 <br>
1.1    사회적 배경 <br>
1.2    가구조아의 특징 <br>

2. 유사 서비스 분석 <br>
2.1    오늘의 집 <br>
2.2    집꾸미기 <br>

3. 오픈소스 소개 <br>
3.1    SpringBoot <br>
3.2    SpringSecurity <br>
3.3    GrayLog <br>
3.4    ElasticSearch <br>
3.5    Scrapy <br>
3.6    TensorFlow <br>
3.7    Grafana <br>
3.8    SwiftLocation(Google Maps Platform) <br>
3.9    MongoDB <br>

4. DFD <br>
4.1    DFD <br> 
4.2    DFD 설명 <br>

-----------

### 1. 서비스 설명– 1.1 사회적 배경 

+ MZ세대의 인테리어 관심 증가 <br>
	본인을 표현하는 것에 과감한 MZ세대는 자신의 공간을 나만의 취향으로 채워넣음으로써 자아표출을 할 수 있음.  
	1인 가구가 많은 MZ세대는 자가보다는 전월세의 주거 형태가 많음. 이에 낯선 공간을 나만의 것으로 채우는 데에 관심이 많음. 

+ MZ세대의 중고거래 관심 증가  <br>
	늘어난 합리적 소비는, ‘소유보다 경험’을 생각하는 MZ세대 사이에서 유행하고 있음. 
	중고거래로 ‘레스 웨이스트(Less Waste)’와 같은 사회적 가치를 통해 뿌듯함을 느낌. 
	최근 고물가, 불경기 시대가 지속됨에 따라 ‘절약’, ‘짠테크’, ‘무지출’과 같은 트렌드가 지속됨. 이에 필요한 물건을 새로 구매하기 보다는 중고거래를 통해 합리적인 소비를 함. 

-------

### 1. 서비스 설명– 1.2 가구조아의 특징

+ 대상: 1인 가구, 중고거래를 선호하는 대학생이나 사회초년생
+ 특징: GUI, 세부 설명 (아래 참고) 


![가구점정보](https://raw.githubusercontent.com/hs-1971193-keonheehan/OpenSource10_6/f86199b14da257b4983caaf297cb26d45176c50b/%EA%B7%BC%EC%B2%98%EA%B0%80%EA%B5%AC%EC%A0%90_%ED%8F%89%EC%A0%90_%EB%A6%AC%EB%B7%B0.jpeg)
+ 사용자 위치 서비스를 기반으로, 가까운 가구점을 추천해줌. 
+ 가구점의 외관사진, 전화번호, 사용자 리뷰, 현 위치로부터 걸리는 시간 등을 한 번에 파악 가능. 


![가구위치](https://raw.githubusercontent.com/hs-1971193-keonheehan/OpenSource10_6/f86199b14da257b4983caaf297cb26d45176c50b/%EA%B7%BC%EC%B2%98%EA%B0%80%EA%B5%AC%EC%A0%90_%EC%A7%80%EB%8F%84%EC%A0%84%EC%8B%9C.jpeg)
+ 지도에서 사용자의 현재 위치와 가구점의 정확한 위치 파악 가능. 
+ 카테고리 별(침구류, 가구, 인테리어)로 분류해서 위치를 한 번에 시각적으로 파악 가능. 


![가구추천](https://raw.githubusercontent.com/hs-1971193-keonheehan/OpenSource10_6/f86199b14da257b4983caaf297cb26d45176c50b/%EA%B0%80%EA%B5%AC%EA%B2%80%EC%83%89_%EA%B0%80%EA%B5%AC%EC%B9%B4%ED%85%8C%EA%B3%A0%EB%A6%AC_%EA%B0%80%EA%B5%AC%EC%B6%94%EC%B2%9C.jpeg)
+ 검색을 통해 사용자의 데이터를 수집하고, 이를 토대로 가구 추천 서비스 제공. 
+ 더욱 상세한 카테고리 별로 가구들이 정리되어있음.


![커뮤니티](https://raw.githubusercontent.com/hs-1971193-keonheehan/OpenSource10_6/f86199b14da257b4983caaf297cb26d45176c50b/%EA%B0%80%EA%B5%AC_%EC%BB%A4%EB%AE%A4%EB%8B%88%ED%8B%B0.jpeg)
+ 커뮤니티 접근 권한을 동네로 한정지으면서 신뢰감과 편리성 모두 제공. 
+ 다양한 카테고리 별로 구분지어 커뮤니티를 단순히 중고거래에 한정짓지 않고 일상, 고민, 도움요청 등 실제 커뮤니티처럼 사용 가능. 


![대화창](https://raw.githubusercontent.com/hs-1971193-keonheehan/OpenSource10_6/f86199b14da257b4983caaf297cb26d45176c50b/%EC%B1%84%ED%8C%85%ED%99%94%EB%A9%B4.jpeg)
+ 1:1 대화를 통해 빠르고 정확하게 중고거래 가능

------

### 2. 유사 서비스 분석 - 2.1 오늘의 집 
![img](https://mobiinsidecontent.s3.ap-northeast-2.amazonaws.com/kr/wp-content/uploads/2020/11/27143034/04-5.png)

사용자 맞춤형 추천에 따른 인테리어 구조와 가구, 소품까지 제공하는 인테리어 플랫폼이다.

#### 장점
- 키워드 기반 커뮤니티로 사용자가 관심있는 키워드에 대한 글을 모아볼 수 있다.
- 카테고리 기능을 이용해 사용자들의 편의성이 증가시켰다.
- 전문가들의 인테리어 노하우를 볼 수 있어 인테리어 초보도 접근하기 좋다.

- 사회적 배경에 따라 오늘의 집 사용자의 가구 형태는 싱글가구가 53.6%으로 가장 많은 모습을 보이고, 사용자 이용 연령대를 보면 30대까지가 총 65.3%로 가장 많은 비중을 차지하고 있다.
![img](https://img1.daumcdn.net/thumb/R1280x0.fpng/?fname=http%3A//t1.daumcdn.net/brunch/service/user/cjHM/image/52eUNRYgqJkGv3OP635fHaQ35PY.png)

- 인테리어 관련 정보 이용 앱 이용 빈도수로 보았을 때, 연령별로는 20,30대가 가장 많은 비중을 차지한다.
![img](https://img1.daumcdn.net/thumb/R1280x0.fpng/?fname=http%3A//t1.daumcdn.net/brunch/service/user/cjHM/image/G6d4dcuyz-eZResl4QQCOsl7TIg.png)


#### 단점
- 중고 가구 거래 시스템이 없다.
- 가구형태에 따라 사용하는 가구가 달라지는데, 사용자 구분 없이 커뮤니티가 운영되고 있다.
- 다양한 정보들이 존재하지만 사용자, 즉 자취생이 원하는 제품에 대한 평가나 필요한 리뷰들만 골라 보기에는 어려움이 있다.
- 컨텐츠 중심 플랫폼이다.

### 2. 유사서비스 분석 - 2.2 집꾸미기

상황별 상품 제안, 인테리어 관련 상담소, 콘텐츠 서비스를 제공해주는 인테리어 플랫폼이다.

#### 장점
- 오늘의 집과 비슷하게 인테리어의 사례가 잘 구분되어 있고, 구매까지 연계가 가능하다.
- SNS 채널을 통한 인테리어 콘텐츠 서비스가 활성화되어있다.
- 커뮤니티에서 사용자들 간 간단한 피드팩이 이용 가능하다.

#### 단점
- 중고 가구 거래 시스템이 없다.
- 커뮤니티에 홍보성 게시물이 많다고 느껴질 정도로 비활성화되어있었다.

------

### 3.오픈소스 소개 - 3.1 SpringBoot

스프링부트는 자바 플랫폼을 위한 오픈소스 애플리케이션 프레임워크 Spring의 많은 부분을 자동화하여
사용자가 편하게 사용할 수 있게 해주는 모듈입니다. 사용자가 실행환경 등 인프라를 신경쓰지 않고
코딩을 시작할 수 있습니다.

![springboot](https://user-images.githubusercontent.com/115446842/205470010-6bd3c65c-5ff4-46a8-8a8b-290edd6b5206.jpg)


* JAVA로 만든 서버 어플리케이션으로 JAVA로 개발하는 사람들이 쉽게 적응 할 수 있습니다.

* 프로젝트에 추가된 라이브러리를 기반으로 실행에 필요한 환경을 자동으로 설정하고, 
필요한 라이브러리 추가 시 관련된 스프링설정을 자동으로 정리해 줍니다.

* 연관된 라이브러리들을 자동으로 호환되는 버전으로 다운로드하고, Tomcat서버가 내장되어있어 
별도의 설정없이 실행결과를 빠르게 확인할 수 있습니다. 또한 웹 애플리케이션도 WAR이 아닌
JAR파일로 패키징하여 사용할 수 있습니다. 

* https://github.com/sosow0212/community
스프링부트 기반의 커뮤니티 API 오픈소스를 통해 커뮤니티를 구현합니다. 
유저 조회, 게시글 업로드 및 검색, 댓글 조회, 작성 및 삭제, 카테고리, 유저 및 게시글 신고 등
다양한 커뮤니티 기능을 담고 있습니다.  

------

### 3. 오픈소스 소개– 3.2 SpringSecurity 

Spring Security는 Spring 기반의 애플리케이션의 보안(인증과 권한, 인가 등)을 담당.  Apache License 2.0의 오픈소스이며, Spring Security는 '인증'과 '권한'에 대한 부분을 Filter 흐름에 따라 처리. Spring Security는 보안과 관련해서 체계적으로 많은 옵션을 제공해주기 때문에 개발자 입장에서는 일일이 보안관련 로직을 작성하지 않아도 된다는 장점이 있음.

** OAuth2.0  - 인터넷 사용자들이 각기 다른 웹사이트 상에서 접근 권한을 부여받을 수 있는 공통적인 수단으로서 사용되는 접근 위임을 의미. 즉 해당 인증 방식을 통하게 되면, 직접 구현한 사이트에 타 플랫폼 회원의 로그인을 받을 수 있음. 또한 커뮤니티 사이트의 경우 이용자의 풀을 넓히고 접근성을 높히기 위해 타 플랫폼과 연계된 사용자 로그인 기능이 고려될 필요가 있다고 판단. 
** 토큰 방식의 로그인 : 토큰 방식의 유효성 검증은 확장성이 좋아 비용적인 측면에서 효율적임.  만약 여러 서버가 돌아가는 상황이라면, 각 서버마다 세션 저장소를 두거나, 공통 세션 저장소를 만들어야하는데, 이 것을 구축 하는 것은 비용으로 이어질 수 있음. 반면에 토큰은 stateless구조 이기 때문에 기존의 세션 방식 보다 확장에 용이.

기본적인 폼 로그인 구조:
	• 사용자가 로그인 정보와 함께 인증 요청 (HttpRequest)
	• AuthenticationFilter가 요청을 가로챔. 이때 가로챈 정보를 통해 UsernamePasswordAuthenticationToken 객체 (사용자가 입력한 데이터를 기반으로 생성, 즉 현 상태는 미검증 Authentication) 생성
	• ProviderManager (AuthenticationManager 구현체) 에게 UsernamePasswordAuthenticationToken 객체를 전달
	• AuthenticationProvider에 UsernamePasswordAuthenticationToken 객체를 전달
	• 실제 DB로 부터 사용자 인증 정보를 가져오는 UserDetailsService에 사용자 정보를 넘겨줌
	• 넘겨받은 정보를 통해 DB에서 찾은 사용자 정보인 UserDetails 객체를 생성
	• AuthenticationProvider는 UserDetails를 넘겨받고 사용자 정보를 비교
	• 인증이 완료되면, 사용자 정보를 담은 Authentication 객체를 반환
	• 최초의 AuthenticationFilter에 Authentication 객체가 반환됨
	• Authentication 객체를 SecurityContext에 저장
+  만약 OAuth 2.0 로그인을 사용한다면, UsernamePasswordAuthenticationFilter 대신 OAuth2LoginAuthenticationFilter 가 호출됨.

![](https://velog.velcdn.com/images%2Ftmdgh0221%2Fpost%2F943d8964-04c2-4310-8b32-caaf0aac8b65%2Fsecurity-aritchtecture.PNG)

OAuth2.0방식 로그인 구조 :

프론트
	• OAuth 서버로 로그인 요청 후, Authorization code 발급 받아, 백에 전달.
	• 백에서 응답 받은 access token, refresh token 저장.
	• 권한이 필요한 요청마다 Authorization 헤더에 access token을 함께 보냄.
	• access token이 만료되었다면, refresh token 보내서 토큰 갱신(프론트에서 요청을 보낼 때 access token이 만료됨을 미리 판별하여 갱신 요청을 보낼 수 있음)
	• refresh token 의 만료 기간이 지났다면, refresh token 재발급 요청
백
	• Authorization code로 OAuth 서버에 토큰 요청
	• Access token으로 이름, 이메일, 프로필 URL 정보 요청
	• db에 존재하지 않는 유저라면, 새로 등록. db에 존재하는 유저라면 정보 업데이트
	• 유저의 primary key 값으로 JWT 토큰(access token & refresh token) 생성. 일반적으로 access token은 한 시간, refresh token은 2주로 생성(본인 애플리케이션에 맞게 변경하여 사용)
	• refresh token은 DB나 Redis에 저장
	• 유저 정보, access token, refresh token 프론트로 전달
	• access token 만료시 refresh token 검증 후, 재발급


간략화 :
	• 사용자 로그인 요청 -> 데이터 검증 후 Authorization Code 발급 -> Authorization Code로 토큰 요청 -> Access Token 및 Refresh Token 발급 -> Access Token으로 로그인 요청 -> 자원 응답(유저 정보) -> 로그인 
	• 사용자 자원 요청 -> 자원 요청 헤더에 Access Token을 함께 전달 -> Token 유효성 검증 -> 자원 응답 
- 모바일과 웹의 연동이 안되어 있어 인테리어 콘텐츠보다 쇼핑몰에 중점을 둔 것처럼 구매에 초점이 맞춰져 있었다.

--------

### 3. 오픈 소스 소개 - 3.3 GrayLog

GrayLog는 연결되어 있는 로그들의 정보를 수집, 분석하여 결과를 출력해주는 로그 집중화 기능을 가진 오픈 소스 툴로 GPL 3.0 License입니다. 애플리케이션이 전송한 로그 메시지의 적재와 조회, 시각화 등의 기능을 제공합니다. 

- 원하는 데이터를 찾아볼 수 있는 '로그 검색' 기능을 가집니다.
- 미리 설정된 방식으로 로그 현황을 보여주는 '대시보드' 기능이 있습니다.
- 특이사항 발생 시 사용자에게 자동으로 알려주는 '통보' 기능이 있습니다. E-mail이나 HTTP 경보 알림을 제공하여 특정 상황이 발생하면 관계자에게 발송하여 위기대응이 가능합니다.
- 사용자가 원하는 로그를 수집할 수 있도록 '입력구성'을 합니다.
- 입력구성을 자동화된 방식으로 분석, 분류, 처리하는 '스트림'을 가집니다.



GrayLog는 Java 기반의 Graylog Server와 로드 데이터 저장소인 Elasticsearch, 환경설정 저장소인 MongoDB로 구성됩니다. 

![img](https://blog.kakaocdn.net/dn/4xulM/btriz13bpkH/MedroKIfOex6MQOcptw4i0/img.png)

- MongoDB는 구성정보와 메타정보 저장용으로 사용됩니다.
- Elasticsearch는 log원격지에서 받은 로그 메시지를 저장하고 필요할 때 마다 검색할 수 있는 기능을 제공합니다.
- GrayLog Server는 다양한 Input에서 발생하는 로그를 구문 분석하며, 해당 로그들을 처리할 수 있는 웹 인터페이스를 제공합니다. 
 15  
MongoDB.md
@@ -0,0 +1,15 @@

--------

### 3. 오픈소스 소개– 3.4 ElasticSearch

(오프소스 기반의 분산 데이터베이스로 검색엔진으로 루씬(Lucene)을 밑바탕에 두며 RESTful API를 지원)
(ElasticSearch는 루씬(Lucene)검색 라이브러리 기반)
1.Query컨텍스트를 이용한 랭킹 검색이 가능하고,
2.Filter컨텍스트를 이용한 단어 위주 검색도 가능합니다.
- Query , Filter는 역색인 기능에 해당합니다.
3.문서는 JSON 형식으로 저장됩니다.
▶ **Query 컨텍스트** -Query 컨텍스트는 문자열에 대한 검색결과의 score 을 판단함. 즉 조건을 만족하는 레코드를 찾는 개념을 넘어 가장 적합하고 유사성 높은 결과를 찾는 개념이므로 우리가 만들고자 하는 검색기능에 최적화 되어있습니다.
▶ **Filter 컨텍스트** -필터링은 검색된 문서들에 대한 **score** 계산을 하지 않기 때문에 쿼리검색보다 빠름. 따라서 활용방식에 따라 검색 성능을 높일 수 있습니다. 
score 계산이란 검색결과의 정확도인데 , 이 정확도를 계산하는 대표적인 알고리즘으로는 BM25알고리즘이 존재합니다.
**※ 역색인 기능** 이란?
일반적인 색인의 목적은 ‘문서의 위치’에 대한 index를 만들어서 빠르게 그 문서에 접근하고자 하는 것인데, 역색인은 반대로 ‘문서 내의 문자와 같은 내용물’의 맵핑 정보를 색인해놓는 것입니다.
- 만약 일반적인 DB에서 “Trade”라는 문구가 포함된 문자열을 찾으려고 한다면 SQL에서는 %Trade% 라고 명확히 입력해야 검색이 가능하고 trade, TRADE, trAde…. 등의 문자열은 직접 하나하나 명시하기 전에는 찾을 수 없습니다. ES의 역색인을 활용하면 대소문자 구분 없이 어떤 문구가 들어와도 찾을 수 있습니다.

ElasticSearch는 GrayLog와 연동하여 GrayLog에서 보낸 로그들을 저장하는 기능도 가지고있습니다. 그렇기에 GrayLog와 연동해줍니다.

## **다음으로는 GrayLog와 연동하는 법입니다.** ##

### 인터넷이 연결된 경우 yum repository에서 설치

http://www.elastic.co/guide/en/elasticsearch/reference/current/setup-repositories.html
rpm --import https://packages.elasticsearch.org/GPG-KEY-elasticsearch
vi /etc/yum.repos.d/elasticsearch.repo
[elasticsearch-1.4]
name=Elasticsearch repository for 1.4.x packages
baseurl=http://packages.elasticsearch.org/elasticsearch/1.4/centos
gpgcheck=1
gpgkey=http://packages.elasticsearch.org/GPG-KEY-elasticsearch
enabled=1
yum install elasticsearch
chkconfig --add elasticsearch

### 인터넷이 연결되지 않을 경우 페키지 다운로드 후 업로드 설치

wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.4.4.noarch.rpm
rpm -ivh elasticsearch-1.4.4.noarch.rpm

### 설정

vim /etc/elasticsearch/elasticsearch.yml
32 cluster.name: elastic
40 node.name: "node1"
47 node.master: true

### Graylog-server, Graylog-web 설치

http://docs.graylog.org/en/1.0/pages/installation.html#virtual-machine-appliances

### 많은 설치 방법이 있지만, yum repository방법으로 설치

sudo rpm -Uvh https://packages.graylog2.org/repo/packages/graylog-1.0-repository-el6_latest.rpm
yum install graylog-server graylog-web


### Graylog-server 설정

vim /etc/graylog/server/server.conf
3 is_master = true
11 password_secret = l9aZxsHgL1g8Qo3CFLgxXfw9ihuxCRnpLwm8JIo9DoZ69f92OGEhEP3nrNcughxPCE8Co93fRfiiixI2TyvdNvKz2XXrGOYt
생성 방법 : yum install epel-release > yum install pwgen > pwgen -N 1 -s 96
22 root_password_sha2 = 03ac674216f3e15c761ee1a5e255f067953623c8b388b4459e13f978d7c846f4
생성방법 yum install perl-Digest-SHA / echo -n yourpassword | shasum -a 256
30 root_timezone = Asia/Seoul
36 rest_listen_uri = http://0.0.0.0:12900/
152 elasticsearch_cluster_name = elastic
155 #elasticsearch_node_name = graylog2-server
(오픈소스 소개 3.5) Scrapy 에서 웹 크롤링을 한 내용들을 바탕으로 검색을 진행합니다.
Scrapy에 대한 Elasticsearch 지원은 다음 모듈을 설치하여 사용할 수 있습니다.
pip install "ScrapyElasticSearch" 
스파이더가 생성한 항목을 가져오고 라이브러리 pyes 를 사용하여 Elasticsearch에 있는 항목을 인덱싱 합니다.
 
항목을 Elasticsearch에 넣도록 Scrapy를 구성하려면 어딘가에서 실행 중인 인스턴스가 있어야 하기때문에 
settings.py 에서 파이프라인을 구성합니다.

'''python
```python
ITEM_PIPELINES = [
  'scrapyelasticsearch.ElasticSearchPipeline',
]
ELASTICSEARCH_SERVER = 'localhost' 
ELASTICSEARCH_PORT = 9200 
ELASTICSEARCH_INDEX = 'meetups'
ELASTICSEARCH_TYPE = 'meetup'
ELASTICSEARCH_UNIQ_KEY = 'link'
'''
```

--------

### 3.오픈소스 소개 - 3.5 Scrapy

웹 사이트에서 필요한 데이터를 크롤링하고, 정보의 처리나 보완등의 애플리케이션에 사용할 수 있는 구조화된 데이터를 추출하는 오픈소스 프레임워크
https://github.com/scrapy/scrapy

- 가구조아 사용 목적 : 쇼핑사이트의 가구 데이터를 가져와 Elasticsearch에게 보낸다.
- 라이센스 : BSD-3-Clause 라이센스
- 프로그래밍 언어 : 파이썬
- 비동기 네트워킹 라이브러리 (Twisted)를 기반으로 작동한다.
 : 하나의 요청이 에러가 났을 때, 그 외의 로직들은 상관 없이 처리된다.-> 데이터 처리가 지연되지 않는다.

- 사용자가 원하는 방식대로 데이터가 가공되어 저장된다.
- xpath를 통해 복잡한 html도 파싱이 가능하다.
- 웹 스크래핑 기능과 웹 크롤링 기능으로 사용할 수 있다.
	1) 웹 스크래핑 : 특정 데이터 추출
	2) 웹 크롤링 : 모든 데이터 추출

- 구성 요소
	- 엔진 : 시스템의 모든 구성요소 간 데이터 흐름을 제어하고 특정 작업이 발생할 때 이벤트를 작동
	- 스케줄러 : 엔진에서 요청을 수신, 요청할 때 대기열에 넣는 역할
	- 다운로더 : 웹 페이지를 가져와서 엔진에 공급하는 역할
	- 스파이더 : 특정 웹 사이트에서 구조화된 데이터를 추출하는 방법을 포함해 스크랩하는 방법을 정의한 클래스
	- 아이템 파이프라인 : 스파이더에서 추출한 아이템을 처리하는 역할( 정리, 유효성 검사 등 )
	- 다운로더 미들웨어 : 엔진과 다운로더 사이에서 요청을 처리하는 특정 후크
	- 스파이더 미들웨어 : 엔진과 스파이더 사이에 있는 후크로 스파이더의 응답이나 요청을 처리

- 웹 크롤링 방법 
	1) 새로운 Scrapy 프로젝트를 만든다.
	2) 추출할 아이템을 정의한다.
	3) 스파이더를 작성한다.
	4) 아이템 파이프라인을 작성한다.

- 운영 매커니즘
![img](https://docs.scrapy.org/en/latest/_images/scrapy_architecture_02.png)

	- spider모듈로 웹 크롤링 요청을 받는다.
	- 데이터 요청 사항을 scheduler로 스케줄링하고 크롤링할 다음 요청을 요청한다.
	- scheduler가 engine에게 요청사항 반환한다.
	- engine이 downloader에게 요청사항을 전송한다.
	: Middleware를 통해 이동 (이때 Download하기 위한 데이터들의 여러 설정사항들이 적용된다.)
	- 인터넷으로부터 받아온 데이터들을 다시 Middleware를 통해 Engine에게 전송한다.
	- Engine이 응답 데이터를 Spider에게 보내고 이때 spidermiddleware를 통과한다.
	- Spider가 스크랩한 항목과 새로운 요청을 Engine에게 반환한다.
	- Engine이 Item pipeline으로 처리된 데이터를 보내고 다음 처리된 요청도 스케줄러로 보낸다. 그리고 다음 크롤링 요청을 받는다.
	( Item pipeline은 처리된 데이터를 Database나 Excel같은 데이터로 저장하기 위해 응답 데이터를 알맞게 가공하고 저장하게 된다.)
	- 스케줄러에 더 이상의 요청사항이 없을 때까지 프로세스가 반복하게 된다.

--------

### 3. 오픈소스 소개 – 3.6 TensorFlow

+ 딥러닝 프로그램을 쉽게 구현할 수 있도록 다양한 기능을 제공하는 라이브러리 
+ 텐서보드를 통해 딥러닝 학습과정 추적 
+ 인공 신경망과 같은 기계 학습 응용프로그램 및 딥러닝에 사용 
+ 타 머신러닝 라이브버리 중 가장 활발한 커뮤니티를 지님 
+ 텐서(Tensor) 다차원의 배열을 담고 있는 노드(Node)와 이를 다양한 연산으로 연결하고 있는 엣지(Edge)로 구성되어 있으며, 이러한 텐서들이 서로 연산을 통해 값을 주고받는 흐름(Flow)으로 작동
+ 브라우저에서 실행기능한 시각화 도우인 텐서보드를 제공하여, 딥러닝 학습 과정을 추적하는데 유용하게 사용 (GUI를 통한 직관적 관찰) 
+ 텐서플로에서는 Keras나 TF-Slim 과 같은 추상화 라이브러리를 제공하여 저수준 텐서플로 라이브러리에 대해 손쉽게 고수준 접근이 가능하게 해준다. 이를 이용하여 간단하게 딥러닝 모델을 구현할 수 있다.
+ 검색, 음성 인식, 번역 등의 구글 앱에 사용되는 기계 학습용 엔진
+ 아이디어 테스트에서 서비스 단계까지 이용 가능
+ 데이터 플로우 그래프 
[데이터 플로우](https://camo.githubusercontent.com/c9acf08b37f66a71545e6ef507e20a1d723948626dbdc72b20cd8cb2633892f4/68747470733a2f2f7777772e74656e736f72666c6f772e6f72672f696d616765732f74656e736f72735f666c6f77696e672e676966)

-----

+ 용어 
	오퍼레이션(Operation): 그래프 상의 노드는 오퍼레이션(줄임말 op)으로 불립니다. 오퍼레이션은 하나 이상의 텐서를 받을 수 있습니다. 오퍼레이션은 계산을 수행하고, 결과를 하나 이상의 텐서로 반환할 수 있습니다. <br>

	텐서(Tensor): 내부적으로 모든 데이터는 텐서를 통해 표현됩니다. 텐서는 일종의 다차원 배열인데, 그래프 내의 오퍼레이션 간에는 텐서만이 전달됩니다. (Caffe의 Blob과 유사합니다.<br>

	세션(Session): 그래프를 실행하기 위해서는 세션 객체가 필요합니다. 세션은 오퍼레이션의 실행 환경을 캡슐화한 것입니다. <br>

	변수(Variables): 변수는 그래프의 실행시, 패러미터를 저장하고 갱신하는데 사용됩니다. 메모리 상에서 텐서를 저장하는 버퍼 역할을 합니다. <br>


-------

### 3. 오픈소스 소개 - 3.7 Grafana 
[https://github.com/grafana/grafana](https://github.com/grafana/grafana)

#### Grafana는 Go/TypeScript를 기반으로 하는 오픈소스 메트릭/로그 데이터 시각화 오픈소스입니다.

#### 라이센스는 AGPL 3.0를 따릅니다. 내부에서 시각화용도로 사용하고, 소스 코드의 수정이 없이 사용되기 때문에 소스 코드 공개 의무가 없습니다.

![Grafana 대시보드](https://grafana.com/static/img/grafana/showcase_visualize.jpg)

#### 기능
* 메트릭/로그 데이터를 사용하여 그래프 등의 시각화해 대시보드에 출력합니다. Grafana에서는 시각화를 패널이라고 합니다.
* 다른 사용자들이 만든 템플릿을 사용해 다양한 대시보드를 사용할 수 있습니다. 이러한 대시보드는 각각 나오는 그래프 형식과 출력을 다르게 하여 템플릿으로 만들어집니다. 대시보드에 따라서 맞춤형 경고 등의 특별한 맞춤 기능을 지원합니다.
* 플러그인 확장을 사용해서 대시보드에 출력할 그래프 종류를 추가할 수 있고, 데이터 소스의 종류 또한 새롭게 추가할 수 있습니다.

#### Graylog 등의 데이터 수집, 분석 도구 오픈소스와 연결해 데이터를 받아와 사용합니다. 2가지 방식으로 서로 연결할 수 있습니다.
* [Graylog to Grafana](https://github.com/GDATASoftwareAG/graylog-to-grafana) 
   * MIT License를 따르며, Graylog에서 구성 데이터를 공유할 수 있는 방식인 content packs를 만들어 대시보드로 전송하거나 json파일로 변환하는 방식을 사용합니다.
* [Graylog metrics](https://grafana.com/grafana/dashboards/2549-graylog-metrics/)와 [Telegraf](https://github.com/influxdata/telegraf)
   * Graylog metrics는 사용자 템플릿 대시보드 중 하나로, 데이터를 모아서 전송할 수 있는 에이전트 오픈소스인 Telegraf와 Graylog를 서로 연결하고, 이를 Graylog metrics 대시보드로 전송해 출력하는 방식을 사용합니다.

#### 장점
* 많은 사용자 템플릿과 플러그인 확장을 지원해 다양한 기능들을 지원합니다.
   * 기존 30여개의 데이터 소스에 추가로 다양한 데이터 소스들을 추가할 수 있습니다.
   * 대시보드를 변경해 맞춤형 경고 등 맞춤 기능 지원
* 데이터에 주석 달기와 데이터 스냅샷 등의 추가 기능을 제공합니다.
* 사용자 인증 시스템이 내장되어있어 인증받지 않은 사용자의 접근을 막을 수 있습니다.

#### 단점, 해결방안
* 주된 사용 용도가 메트릭 데이터 시각화이기에 로그 데이터 시각화 쪽으로는 빈약할 수 있습니다. 이는 Graylog에서 로그 대신 메트릭 데이터를 보내는 방식으로 해결합니다. 
* 데이터 수집과 저장은 Grafana와 별도로 설정해야합니다. Graylog가 데이터 수집 및 저장을 담당하고 시각화 할 때만 데이터를 받아오는 방식으로 해결합니다.

-------

### 3. 오픈소스 소개  - 3.8  Swift Location(GoogleMaps Platform)



 ##### Swift Location은 Swift언어를 사용하여, 사용자의 위치 관련 기능들을 쉽게 사용 할 수 있게 도와주는  MIT LICENSE 오픈소스 입니다. 

[malcommac/SwiftLocation: 🛰 CoreLocation Made Easy - Efficient & Easy Location Tracker, IP Location, Gecoder, Geofence, Autocomplete, Beacon Ranging, Broadcaster and Visits Monitoring (github.com)](https://github.com/malcommac/SwiftLocation#autocomplete)

#### 기능

* GPS를 통해서 사용자의 위치를 가져 올 수 있습니다. - **(아래 예시, Swift 사용)**

```swift
SwiftLocation.gpsLocationWith {
    // configure everything about your request
    $0.subscription = .continous // continous updated until you stop it
    $0.accuracy = .house 
    $0.minDistance = 300 // updated every 300mts or more
    $0.minInterval = 30 // updated each 30 seconds or more
    $0.activityType = .automotiveNavigation
    $0.timeout = .delayed(5) // 5 seconds of timeout after auth granted
}.then { result in // you can attach one or more subscriptions via `then`.
    switch result {
    case .success(let newData):
        print("New location: \(newData)")
    case .failure(let error):
        print("An error has occurred: \(error.localizedDescription)")
    }
}
```

* 주소, 장소에 대해서 검색 시에 자동완성 기능을 제공합니다.  

* 자주 방문한 곳에 대해서 위치 모니터링 서비스를 제공합니다.

* 지오펜싱 영역을 설정 가능합니다.  **(아래 예시)**

  ```swift
  let options = GeofencingOptions(circleWithCenter: CLLocationCoordinate2D(latitude: 3, longitude: 2), radius: 100)
  SwiftLocation.geofenceWith(options).then { result in
      guard let event = result.data else { return }
  
      switch event {
      case .didEnteredRegion(let r):
          print("Triggered region entering! \(r)")
      case .didExitedRegion(let r):
          print("Triggered region exiting! \(r)")
      default:
          break
      }
  }
  ```

* 프로그램(앱)이 실행되지 않는 사이에도 마지막으로 알려진 위치를 자동으로 저장합니다.

* 만약, 사용자가 GPS로 위치정보를 얻는 것에 대해 비동의 할 경우, 정확하지는 않지만 IP주소를 통해 어느정도 위치정보를 얻을 수 있습니다.  **(이 기능을 위해 IPLocation data 객체를 얻는 방법 코딩 예시, Swift 사용)**

```swift
SwiftLocation.ipLocationWith(IPLocation.IPData()).then { result in
    print(result.location.coordinates)
    // get the city and other data from .info dictionary
    print(result.location.info[.city])
    print(result.location.info[.countryCode])
}
```

* 좌표(위도,경도)에서 주소를 가져 올 수 있고, 반대로 주소(혹은 지역 명)를 통해 좌표를 얻을 수 있습니다. **(Google Map 사용, 지오코딩 예시, Swift사용)**

```swift
let service = Geocoder.Google(lat: 37.331656, lng: -122.0301426, APIKey: "<your api key>")
SwiftLocation.geocodeWith(service).then { result in
    // Different services, same expected output [GeoLocation]
    print(result.data)
}
```



#### GeoFencing (지오펜싱)

지오펜싱은 실제 위치에 기반하여, 가상의 경계나 구역을 만드는 기술입니다. 지오펜스는 사용자의 실시간 위치와 출입 정보를 기록할 때 활용됩니다. 위치 정보를 담은 모바일 기기가 지저된 구역에 들어오면 조건에 따라 텍스트 메시지, 알람 등 미리 정해진 이벤트를 실행할 수 있습니다. '가구조아' 에서는 지오펜싱을 이용해서, 특정 지역으로 가면 해당하는 지역에 있는 가구, 인테리어점들의 할인 쿠폰을 사용자에게 발송하는 기능 등을 추가 할 수 있습니다.  또한 백그라운드에서도, 앱이 종료되어도 작동하기에 유용합니다. 

#### GeoCoding (지오코딩)

지오코딩이란, 고유명칭(장소)를 가지고 좌표(위도,경도)를 얻는 것을 뜻합니다.

SwiftLocation에서의 지오코딩, 역 지오코딩 기능은 **Google Maps Platform API**와 연동되어 있습니다. 구글 맵 플랫폼에는 구글 맵 관련 다양한 API들을 단순히 Key발급을 통해서 쉽게 이용이 가능합니다. (사용하는 기능에 따라 어느정도의 과금이 요구됨). 이때 사용하는 언어는 많이 사용하는 언어인 Python, Java, JavaScript, Go 등을 사용합니다. 



#### 지오코딩 기능 사용과정

**Google Maps API**에서 key를 발급받고, GoogleMap 패키지를 다운받습니다. 이제 특정 장소를 위도, 경도를 입력하면, 해당 지역 근처에 있는 장소들을 띄워줍니다. 만약, 우리가 찾는 가구점과 인테리어점들이 구글맵에 등록이 안되어 있다면, Google Map API의 마커등록을 통해서 지도에 원하는 위치에 장소를 도식 가능합니다.  EX. JavaScript 기준으로 google.mapss.Marker() 생성자 함수 사용.

##### 마커등록 사용 예시_JavaScript사용 - (동대문 쇼핑몰을 지도에 등록한다고 가정)

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

* **장소 검색**- 시설, 주요 관심 장소, 지리적 위치에 대한 장소 정보를 검색합니다.

* **장소 세부정보**- 사용자 리뷰, 댓글을 비롯하여 특정 장소에 대한 자세한 정보를 반환함

* **장소 자동완성**- 사용자가 검색 시, 장소의 이름 혹은 주소를 자동완성 해준다.
* **장소 사진** - 앱에 장소에 대한 사진을 추가 할 수 있습니다. 
* **장소 ID** - 특정 장소에 대한 세부정보를 가져오고, 장소들을 ID로 구분합니다. 
* **장소 아이콘** - 다양한 장소에 대한 요청 및 표시 아이콘을 전시할 수있습니다. 

* **추천검색어**- 쿼리 예측 서비스로 인해 사용자가 입력하면 추천 검색어를 반환한다.

-------

### 3. 오픈 소스 소개 - 3.9 MongoDB

MongoDB는 C++로 작성된 오픈 소스 Document-Oriented, NoSQL 데이터 베이스로 SSPL License입니다. MongoDB는 Collection 안의 Document에 데이터를 저장합니다. Document의 Field 안의 데이터 형식이 서로 달라도 입력이 가능하고, 각 Document들이 일관된 Field를 가지지 않아도 되기 때문에 비정형 데이터를 저장하기에 좋습니다.

![img](https://www.mongodb.com/assets/images/mongodb-architecture/image_diagram_platform_kr.png)

- 서버 장애에도 서비스는 계속 동작하기 때문에 신뢰성(Reliability)을 가집니다.
- 데이터와 트래픽 증가에 따라 수평확장(scale-out)을 할 수 있어 확장성이 좋습니다.
- 여러가지 형태의 데이터를 손쉽게 저장할 수 있는 유연성(Flexibility)을 가집니다. 서비스 요구사항에 맞춰 다양한 종류의 데이터가 추가되어도 스키마 변경 과정 없이 필요한 데이터를 바로 저장하고 읽을 수 있습니다.
- Index 지원(Index Support)으로 다양한 조건으로 빠른 데이터 검색이 가능합니다.



MongoDB는 GrayLog의 구성요소 중 하나로 GrayLog로부터 전달받은 환경정보, 메타 데이터를 저장합니다.

-------

### 4. DFD - 4.1 DFD

![](https://github.com/hs-1971193-keonheehan/OpenSource10_6/raw/keonheehan/10_6DFD%EB%8D%B0%EC%9D%B4%ED%84%B0%ED%9D%90%EB%A6%84%EB%8F%84.JPG?raw=true)

-------

### 4.DFD - 4.2 DFD 설명


* 사용자가 **SpringBoot** 기반으로 제작한 페이지에 접속을 하면 페이지에서 GUI를 제공합니다. 
* 로그인창이 뜨고, **SpringSecurity** 와 다른 **Oauth2(오어쓰2)** 서비스 제공자와의 서비스 연동을 통해 소셜 로그인을 하여 웹서버에 접속이 
  가능합니다. 
* 이때 접속한 사용자의 접속 정보, 아이디 정보 등은 **MongoDB** 에 저장됩니다. 
* 어플리케이션의 가구 검색창에서 특정 단어를 검색하면 **GrayLog** 에서 **ElasticSearch** 로 검색 로그를 전달해줍니다. 
* **GrayLog** 에서는 검색 로그들을 바탕으로 사용자에 맞는 가구 추천 및 검색어 추천을 진행합니다. 
* **ElasticSearch** 는 **Scrapy** 를 이용해 가져온 쇼핑사이트의 가구 데이터와 검색 텍스트를 바탕으로 검색을 진행합니다. 
* **Filter** 와 **Query** 를 통한 순위검색 및 단어위주 검색을 진행하고 그에대한 결과목록을 검색페이지 아래 순차적으로 나열하게됩니다. 
* 가구조아 어플리케이션의 내 근처 탭에 **SwiftLocation** 를 가져와 **SwiftLocation** 을 이용하여 **Google Map,Google Places API** 로 
  근처 가구점의 정보나 근처 유저의 위치를 확인 가능합니다. 
* 게시글 작성을 할때는 게시물을 올리기 전 **TensorFlow** 에 게시글 데이터를 보내어 비속어 및 홍보성 데이터를 분별하여 검토가 가능하게
  구성하였습니다.
* 사용자들의 관심 검색어의 파악등을 분석하기 위해 **Grafana** 시각화 오픈소스를 이용하여 **ElasticSearch** 에 저장되어있는 로그데이터를 
  **GrayLog** 에서
  가져와 **Grafana** 로 가져와 시각적으로 실시간 데이터를 파악할 수 있습니다.
