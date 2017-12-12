---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-03"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Kafka Java 클라이언트 사용
{: #kafka_using}

## Kafka API 샘플 사용, 다운로드 및 실행 방법
{: notoc}

Java&trade; Kafka API 샘플은 Java로 작성된 제작자 및 이용자 예제이며, Kafka API를 직접 사용합니다. 이 샘플을 로컬에서 또는 {{site.data.keyword.Bluemix_short}}에서 실행할 수 있습니다.

샘플 코드는 [message-hub-samples GitHub 프로젝트 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}에 있습니다. 이 샘플은 {{site.data.keyword.messagehub}} 관리 API를 사용하여 메시지를 보내고 받는 대상 토픽을 작성합니다. 

샘플 설정 및 실행에 대한 자세한 정보는 [README.md ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}를 참조하십시오.

샘플 실행 방법에 대한 세부사항 둘러보기는 [{{site.data.keyword.messagehub}} 시작하기](/docs/services/MessageHub/index.html#getting_started_steps)를 참조하십시오.

## Liberty for Java 샘플 사용, 다운로드 및 실행 방법
{: #liberty_sample notoc}

Liberty for Java 샘플은 Liberty 런타임에 배치된 단순한 애플리케이션을 구현합니다. 애플리케이션은 {{site.data.keyword.messagehub}}에서 메시지를 생성하고 이용하도록 Kafka API를 사용합니다.
또한, 애플리케이션은 관리에 사용할 수 있는 웹 프론트 엔드를 제공합니다. 

[message-hub-samples GitHub 프로젝트 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-liberty-sample){:new_window}에서 샘플 코드를 찾을 수 있습니다.

## 0.9.x에서 0.10.x로 Kafka 클라이언트를 마이그레이션하는 방법
{: #kafka_migrate notoc}


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

<!--
17/10/17 - Karen: following info duplicated at messagehub063 
-->

## sasl.jaas.config 특성 사용
{: #sasl_prop notoc}
Kafka 클라이언트를 0.10.2.1 이상에서 사용 중인 경우 JAAS 파일 대신 클라이언트 구성에 <code>sasl.jaas.config</code> 특성을 사용할 수 있습니다. {{site.data.keyword.messagehub}}에 연결하려면 <code>sasl.jaas.config</code>를 다음과 같이 설정하십시오. 
<pre>
<code>    sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required \
    username="USERNAME" \
    password="PASSWORD";</code>
</pre>
{:codeblock}

여기서 USERNAME 및 PASSWORD는 {{site.data.keyword.Bluemix_notm}}의 {{site.data.keyword.messagehub}} **서비스 신임 정보** 탭에 있는 값입니다. 

<code>sasl.jaas.config</code>를 사용하는 경우 동일한 JVM에서 실행 중인 클라이언트가 다른 신임 정보를 사용할 수 있습니다. 자세한 정보는
[Kafka 클라이언트 구성 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://kafka.apache.org/documentation/#security_sasl_plain_clientconfig){:new_window}을 참조하십시오.

초기 Kafka 클라이언트에서 신임 정보를 지정하려면 JAAS 구성 파일을 사용해야 합니다. 이 메커니즘의 편의성이 부족하므로, 대신 <code>sasl.jaas.config</code> 특성을 사용하는 것이 좋습니다. 

<!-- 
17/10/17 - Karen: following info duplicated at messagehub108
 -->

## 토픽 관리용 API
{: #topic_admin notoc}

Kafka 클라이언트를 0.11 이상에서 사용 중이거나 Kafka 스트림을 0.10.2.0 이상에서 사용 중인 경우, API를 사용하여 토픽을 작성하고 삭제할 수 있습니다. 토픽 작성 시 허용되는 설정에 대한 제한사항이 있습니다. 현재는 다음 설정만 수정할 수 있습니다. 

<dl>
<dt>cleanup.policy</dt>
<dd><code>delete</code>(기본값), <code>compact</code> 또는 <code>delete,compact</code>로 설정하십시오.</dd>
<dt>retention.ms</dt>
<dd>기본 보존 기간은 24시간입니다. 최소 1시간이며 최대 30일입니다. 이 값을 시간 배수로 지정하십시오.

<p>**참고:**
정리 정책이 <code>compact</code> 전용인 경우, <code>delete</code>를 자동으로 추가하지만 시간에 따라 삭제가 사용 불가능합니다. 토픽의 메시지는 삭제되기 전에 최대 1GB로 압축됩니다. </p>
</dd>
</dl>

<!--
new topic that includes content from existing topics about samples and migration
-->
