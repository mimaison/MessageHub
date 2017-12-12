---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-10"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Kafka 클라이언트 사용
{: #kafka_using}

{{site.data.keyword.messagehub}}는 현재
Kafka 0.10.2.1을 기반으로 합니다. Kafka 클라이언트가 {{site.data.keyword.messagehub}}에 연결할 수 있는 가장 빠른 버전은 0.9.0.0이며
최신 버전은 0.10.2.1입니다. Kafka 클라이언트가 배치한 버전보다 이후 버전인 경우 {{site.data.keyword.messagehub}}에 Kafka 클라이언트를
연결할 수 없습니다.

Kafka 클라이언트는 여러 개의 언어로 존재하며 해당 언어 중 일부에 대한 지시사항이 제공됩니다. 다른 것을 사용할 수 있지만 신임 정보를 제공하기 위해서는 SASL PLAIN 지원이 필요합니다. 
