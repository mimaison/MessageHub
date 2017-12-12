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

# {{site.data.keyword.messagehub}}와 함께 Kafka 스트림 사용
{: #kafka_streams }

스트림 라이브러리 0.10.2.0부터, 토픽 API는 이제 설정 없이 {{site.data.keyword.messagehub}}에 대한 작업을 수행할 수 있습니다. <code>sasl.jaas.config</code> 또는 JAAS 파일을 사용하여 SASL 신임 정보를 지정하고 <code>replication.factor</code>를 3으로 설정하십시오.

예를 들어, 

<pre>
<code>
    props.put(StreamsConfig.REPLICATION_FACTOR_CONFIG, "3");
    props.put(StreamsConfig.BOOTSTRAP_SERVERS_CONFIG, BOOTSTRAP_SERVERS);
    props.put("security.protocol","SASL_SSL");
    props.put("sasl.mechanism","PLAIN");
    props.put("ssl.protocol","TLSv1.2");
    props.put("ssl.enabled.protocols","TLSv1.2");
    props.put("sasl.jaas.config","org.apache.kafka.common.security.plain.PlainLoginModule required username=\"USERNAME\" password=\"PASSWORD\";");
</code>
</pre>
{:codeblock}

여기서 BOOTSTRAP_SERVERS, USERNAME 및 PASSWORD는 {{site.data.keyword.Bluemix_notm}}의 {{site.data.keyword.messagehub}} **서비스 신임 정보** 탭에 있는 값입니다.

<!--
new topic that includes content from existing topics about samples and migration
-->
