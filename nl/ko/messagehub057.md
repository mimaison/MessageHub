---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-05"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# 알려진 제한사항
{: #restrictions}


## 각 {{site.data.keyword.Bluemix_notm}} 영역에 대한 {{site.data.keyword.messagehub}} 인스턴스의 수 
{: #instances_space notoc}

각 {{site.data.keyword.Bluemix_notm}} 영역에 대해 하나의 {{site.data.keyword.messagehub}} 인스턴스만
포함할 수 있습니다. 

##토픽 및 파티션
{: #topics_partitions notoc}

*  토픽 이름은 최대 100자로 제한됩니다. 
*  토픽의 기본 파티션 수는 하나입니다. 
*  각 {{site.data.keyword.Bluemix_notm}} 영역에는 파티션의 수가 100개로 제한됩니다. 더 많은 파티션을 작성하려면,
새 {{site.data.keyword.Bluemix_notm}} 영역을 사용해야 합니다. 

## 메시지 보유
{: #message_retention notoc}

기본적으로 메시지는 Kafka에서 각 파티션당 최대 1GB까지 최대 24시간 동안 보존됩니다. 1GB 한계에 도달하면 한계를 넘지 않도록 가장 오래된 메시지가 삭제됩니다. 

사용자 인터페이스 또는 관리 API 중 하나를 사용하여 토픽을 작성할 때 메시지 보유에 대한 시간 한계를
변경할 수 있습니다. 시간 한계는 최소 1시간이며 최대 30일입니다. 

## Kafka에서 토픽 작성 및 삭제
{: #create_delete notoc}

Kafka에서 토픽 작성 및 삭제는 비동기 작업으로 완료하는 데 약간의 시간이 소요될 수
있습니다. 토픽의 빠른 작성 및 삭제 또는 토픽의 빠른 삭제 및 재작성에 의존하는
사용법 패턴은 피하는 것이 좋습니다. 

## Kafka REST API
{: #trouble_rest notoc}

*  요청 및 응답에 2진 임베디드 형식만 지원됩니다. Avro 임베디드 형식은 지원되지 않습니다. 
*  동시 요청은 이용자 인스턴스에 대해 지원되지 않습니다. 이용자 인스턴스에 해당하는 읽기, 커미트 또는 삭제 요청은 해당 인스턴스의 미해결 요청에 대한 응답을 수신한 후에만 전송해야 합니다. 

## Kafka REST API 비율 제한사항
{: #kafka_rate notoc}

Kafka REST API를 사용하는 애플리케이션은 각 ApiKey에 대한 비율 제한 대상이 될 수 있습니다. 이 제한이 발생할 때 API는 다음과 같은 HTTP 오류로 응답합니다. 

<code>429 Too Many Requests</code>
{:screen}

이 오류가 발생하는 경우 잠시 대기한 후에 요청을 다시 제출하십시오.

## Kafka REST API 일별 다시 시작
{: #rest_restart notoc}

Kafka REST API는 단기간 동안 하루에 한 번 다시 시작합니다. 이 기간 동안에 Kafka REST API를
사용하지 못하게 될 수 있습니다. 이런 상황이 발생하는 경우, 요청을 재시도하십시오. REST API가 다시 시작된 후에
Kafka 이용자 인스턴스를 재작성해야 합니다. 이런 경우, REST API는 다음과 같은 JSON을 리턴합니다. 

```'{"error_code":40403,"message":"Consumer instance not found."}'
```
{:screen}

## Kafka 상위 레벨 이용자 API
{: #kafka_consumer notoc}

Apache Kafka 0.8.2 단순 또는 상위 레벨 이용자 API는
{{site.data.keyword.messagehub}}와 함께 사용할 수 없습니다. 대신 새로운 Kafka 0.9 이용자 API를 사용하십시오. 
