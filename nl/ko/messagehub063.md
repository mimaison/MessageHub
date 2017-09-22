---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-11"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 연결 및 인증 방법
{: #kafka_connect}


{{site.data.keyword.messagehub}}에 연결하기 위해 Kafka API는 다음을 사용합니다. 
```kafka_brokers_sasl
``` 
신임정보 및
```
user
```
및

 ```password
```
 [VCAP_SERVICES 환경 변수](/docs/services/MessageHub/messagehub071.html)에서.

## Java 이외의 애플리케이션에서 연결 및 인증
{: #kafka_notjava notoc}

{{site.data.keyword.messagehub}} 서비스는 현재
SASL PLAIN을 사용하여 클라이언트를 인증합니다. 신임 정보는 암호화된 연결을 통해 계속 이어집니다.
이는 Kafka 0.10.0.X에 추가된 새 기능입니다. SASL PLAIN으로 Kafka 0.10을 지원하는 모든 클라이언트는
{{site.data.keyword.messagehub}}에 대해 작업해야 합니다. 클라이언트 예는 다음과 같습니다.

* [librdkafka ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/edenhill/librdkafka/){:new_window}
* [confluent-kafka-python ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/confluentinc/confluent-kafka-python){:new_window}

Kafka 0.9.0.0 이전의 클라이언트를 사용하는 경우, 사용자 정의 로그인 모듈을 사용해야 하며 [{{site.data.keyword.messagehub}} 로그인 모듈 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/ibm-messaging/message-hub-samples/blob/master/kafka-0.9/message-hub-login-library/messagehub.login-1.0.0.jar){:new_window}에서 다운로드할 수 있습니다.

