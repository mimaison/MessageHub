---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-27"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.messagehub}} 개념

{{site.data.keyword.messagehub}}는 토픽을 사용하여 발행/구독
메시징을 구현합니다. 다른 메시징 시스템과 다르게 {{site.data.keyword.messagehub}}는 토픽을 제공하지만 큐에 저장하지 않습니다. 또한, {{site.data.keyword.messagehub}}는
{{site.data.keyword.mql}} API와 같은 추가 기능 및 다른 시스템에 대한 브릿지를 제공합니다. 

{{site.data.keyword.messagehub}}에는 세 개의 API(Kafka API, {{site.data.keyword.mql}} API 및
Kafka REST API)가 있습니다. API를 사용하여 메시징 애플리케이션 작성하기에 대한 자세한 정보는
[Kafka 클라이언트 사용](/docs/services/MessageHub/messagehub050.html), [MQ Light API 클라이언트 사용](/docs/services/MessageHub/messagehub075.html) 및 [Kafka REST API 사용](/docs/services/MessageHub/messagehub025.html)을 참조하십시오.

{{site.data.keyword.messagehub}}는 다른 시스템의 선택사항에
브릿지를 지원하기도 합니다. 브릿지는 다른 시스템에 대한 단방향
링크입니다. 브릿지는 다른 시스템에서 메시지를 가져와서 그 메시지를 토픽에 공개하거나
토픽에서 메시지를 이용해서 그 메시지를 다른 시스템에 보낼 수 있습니다. 이런 식으로 {{site.data.keyword.messagehub}}를 사용하여 코드를 작성하지 않고 다른 시스템과 통합할 수 있습니다. 자세한 정보는 [브릿지를 사용하여 다른 서비스에 링크](/docs/services/MessageHub/messagehub088.html)를 참조하십시오.

{{site.data.keyword.messagehub}}는 고도로 확장 가능하고, 많은 프로덕션 환경에서 고성능 메시징 백본이 증명된 오픈 소스
Apache Kafka 프로젝트를 기반으로 합니다. 자세한 정보는 [{{site.data.keyword.messagehub}} 및 Apache Kafka](/docs/services/MessageHub/messagehub073.html)를 참조하십시오.
