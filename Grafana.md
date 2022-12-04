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
