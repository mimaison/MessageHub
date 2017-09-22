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

# 0.9.x에서 0.10.x로 Kafka 클라이언트를 마이그레이션하는 방법
{: #kafka_migrate}


Java 클라이언트를 사용하는 경우, 이제 공개적으로 사용 가능한 0.10.x Kafka 클라이언트를 사용할 수 있습니다. 0.9.x에서
최신 0.10.x 버전(현재는 0.10.2.1)으로 이동하시기 바랍니다. 다음 단계를 완료하십시오. 

1. {{site.data.keyword.messagehub}} 로그인 jar 모듈을 삭제하십시오.
2. <code>jaas.conf</code> 파일을 다음으로 변경하십시오. 
    ```
        KafkaClient {
          org.apache.kafka.common.security.plain.PlainLoginModule required
          serviceName="kafka"
            username="<your username>"
            password="<your password>";
        };
    ```
    {: codeblock}

3. 다음 행을 이용자 및 제작자 특성에 추가하십시오. <code>sasl.mechanism=PLAIN</code>


