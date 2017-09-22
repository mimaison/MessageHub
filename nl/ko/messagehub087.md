---

copyright:
  years: 2015, 2017
lastupdated: "2017-01-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 세 개의 API 중에서 선택
{: #choose_api}

{{site.data.keyword.messagehub}}는 세 개의 API를 지원합니다. 다음은 가장 적합한 API를 선택하는 데 도움이 되는 정보입니다. 

## Kafka API를 사용하는 이유
{: #why_kafka notoc}

{{site.data.keyword.messagehub}}에서 제공하는 기타 인터페이스가 아닌
Kafka API를 사용하도록 선택해야 하는 몇 가지 이유가 있습니다. 이러한 이유에는 다음이 포함됩니다.
{:shortdesc}


* Kafka 지원이 되는 기존 시스템(예: {{site.data.keyword.IBM}} {{site.data.keyword.streaminganalyticsshort}} 및 {{site.data.keyword.sparks}})과 사용자의 앱을 통합하는 것이 더 쉽습니다.
* 다른 API보다 처리량이 더 많고 대기 시간은 더 짧습니다. 
* Kafka REST API보다 훨씬 다양한 기능을 갖춘 API를 제공합니다. 


## {{site.data.keyword.mql}} API를 사용하는 이유
{: #why_mql notoc}

{{site.data.keyword.mql}} API에서는 Kafka API보다 더 상위 레벨의 추상을 제공합니다. {{site.data.keyword.mql}}는 큐 및 발행/구독 메시징 패턴을 모두 지원하는 통합된 메시징 모델에서 앱을 신속하고 이식 가능하게 작성할 수 있도록 합니다.
{:shortdesc}

앱은 동적으로 작성된 대상을 사용하여 메시지를 교환하며,
이를 통해 계층적으로 구조화하고(예: <code>‘/sports/football’</code>), 와일드카드를 사용하여 그룹화하고(예: 
<code>‘/sports/#’</code>) 전달 보증 및 메시지 만료에 대한 단순 제어를 할 수 있습니다.
이를 사용하여 작업자 오프로드, 이벤트 알림 및 일괄처리와 같은 시나리오를 간단히 구현할 수 있습니다.

{{site.data.keyword.mql}} API를 사용하여 다른 앱 간에 메시지를 보낼 뿐만 아니라, Kafka REST 또는 Kafka API를 사용하는 앱과 메시지를 교환할 수도 있습니다. 그렇지 않으면 {{site.data.keyword.IBM_notm}} MQ와 온프레미스로 앱을 사용할 수도 있습니다.


## Kafka REST API를 사용하는 이유
{: #why_rest notoc}

Kafka REST API는 다음 상황에서 사용할 수 있는 편리한 인터페이스입니다. 

* 개발자가 {{site.data.keyword.messagehub}}의 사용을 빠르게 시작하기 원하는 경우
* 대기 시간이 중요한 요인이 아닌 낮은 처리량의 특정 유스 케이스에서
* 디버깅 및 결함 발견을 위해서

Kafka REST API는 높은 처리량과 낮은 대기 시간 인터페이스를 위한 것이 아닙니다. 이러한 유형의 요구사항은 {{site.data.keyword.messagehub}}와의 연결에 Kafka API를 사용하도록 권장합니다. 자세한 정보는 [Kafka 클라이언트 사용](/docs/services/MessageHub/messagehub050.html#kafka_client)을 참조하십시오.












