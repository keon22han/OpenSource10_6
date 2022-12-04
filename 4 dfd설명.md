![](https://github.com/hs-1971193-keonheehan/OpenSource10_6/raw/keonheehan/10_6DFD%EB%8D%B0%EC%9D%B4%ED%84%B0%ED%9D%90%EB%A6%84%EB%8F%84.JPG?raw=true)

## 데이터흐름도

먼저, 사용자가 SpringBoot기반으로 제작한 페이지에 접속을 하면 페이지에서 GUI를 제공합니다. 
로그인창이 뜨고, SpringSecurity와 다른 Oauth2(오어쓰2) 서비스 제공자와의 서비스 연동을 통해 소셜 로그인을 하여 웹서버에 접속이 가능합니다. 
이때 접속한 사용자의 접속 정보, 아이디 정보 등은 ** MongoDB ** 에 저장됩니다. 
어플리케이션의 가구 검색창에서 특정 단어를 검색하면 GrayLog에서 ElasticSearch로 검색 로그를 전달해줍니다. 이때 GrayLog에서는 검색 로그들을 바탕으로 사용자에 맞는 가구 추천 및 검색어 추천을 진행합니다. 다시 올라가서 ElasticSearch는 Scrapy를 이용해 가져온 쇼핑사이트의 가구 데이터와 검색 텍스트를 바탕으로 검색을 진행합니다. 이때 Filter와 Query를 통한 순위검색 및 단어위주 검색을 진행하고. 그에대한 결과목록을 검색페이지 아래 순차적으로 나열하게됩니다. 가구조아 어플리케이션의 내 근처 탭을 누르면 지도가 나오는데, 이때는 SwiftLocation을 이용하여 Google Map,Google Places API로 근처 가구점의 정보나 근처 유저의 위치를 확인 가능합니다. 게시글 작성을 할때는 게시물을 올리기 전 TensorFlow에 게시글 데이터를 보내어 비속어 및 홍보성 데이터를 분별하여 검토가 가능하게 구성하였습니다.
마지막으로 사용자들의 관심 검색어의 파악등을 분석하기 위해 Grafana시각화 오픈소스를 이용하여 ElasticSearch에 저장되어있는 로그데이터를 GrayLog에서 가져와 Grafana 로 가져와 시각적으로 실시간 데이터를 파악할 수 있습니다.

## 목차
1. 서비스 설명
	1.1....사회적 배경
	1.2....가구조아의 특징

2. 유사 서비스 분석
	2.1....오늘의 집
	2.2....집꾸미기

3. 오픈소스 소개
	3.1....SpringBoot
	3.2....SpringSecurity
	3.3....GrayLog
	3.4....ElasticSearch
	3.5....Scrapy
	3.6....TensorFlow
	3.7....Grafana
	3.8....SwiftLocation(Google Maps Platform)
	3.9....MongoDB

4. DFD
	4.1....DFD 
	4.2....DFD 설명