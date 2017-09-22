---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# MQ Light API의 개념 및 차이점
{: #mqlight}

{{site.data.keyword.mql}} API에서는 Kafka와 비교하여 메시징에 대해 더 상위 레벨의 추상을 제공하며, 이는 사용자의 애플리케이션에서 학습하고 사용하는 것을 더 쉽게 해줍니다.
{:shortdesc}

Kafka 클라이언트 또는 {{site.data.keyword.mql}} API 사용 중에서 선택하는 것은
빌드하려는 메시징 토폴로지에 좌우됩니다. 

* Kafka로 적은 수의 토픽을 사용하여 추가 확장성을 위해 각 토픽에 여러 개의 파티션이 생기도록 할 수 있습니다. 이용자 그룹을 사용하여 이용자들 간에서 메시지를 공유할 수 있지만, 각 이용자가 지정된 파티션에 대한 메시지의 비율과 맞출 수 있어야 합니다. 
* {{site.data.keyword.mql}} API로 훨씬 더 많은 수의 토픽을 사용할 수 있으며 토픽 이름은 계층 구조(예: <code>‘/sports/football’</code> 및 <code>‘/sports/tiddlywinks’</code>)입니다. 이용자들 사이에서 메시지를 공유하는 것이 훨씬 더 간단합니다. 

{{site.data.keyword.mql}} API의 토픽은 Kafka 토픽과 같지 않습니다. 그 대신, {{site.data.keyword.mql}} API는
"MQLight"로 이름 지정된 단일 Kafka 토픽을 사용하며 {{site.data.keyword.mql}} API를 사용하여 보내고 받은 모든 메시지가 그 하나의 Kafka 토픽을 통해 이동합니다. 

{{site.data.keyword.mql}}는 다음 {{site.data.keyword.Bluemix_notm}} 지역(미국 남부, 영국 및 시드니)에서만 사용 가능합니다. MQ Light API는 독일 지역 또는 {{site.data.keyword.Bluemix_notm}} 데디케이티드에서는 사용할 수 없습니다. 

<!-- begin PRODUCTION ONLY -->
API 중에서 선택하기에 대한 자세한 정보는 [Kafka API를 사용하는 이유](/docs/services/MessageHub/messagehub054.html), [MQ Light API를 사용하는 이유](/docs/services/MessageHub/messagehub076.html) 및 [Kafka REST API를 사용하는 이유](/docs/services/MessageHub/messagehub065.html)를 참조하십시오.
<!-- end PRODUCTION ONLY -->
