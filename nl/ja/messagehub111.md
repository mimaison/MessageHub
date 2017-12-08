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

# {{site.data.keyword.messagehub}} での Kafka Streams の使用
{: #kafka_streams }

Streams library 0.10.2.0 以降、トピック API はセットアップを必要とせずに {{site.data.keyword.messagehub}} とともに機能するようになりました。SASL 資格情報を <code>sasl.jaas.config</code> または JAAS ファイルを使用して指定し、<code>replication.factor</code> を 3 に設定してください。

以下に例を示します。

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

ここで、BOOTSTRAP_SERVERS、USERNAME、および PASSWORD は、{{site.data.keyword.Bluemix_notm}} の {{site.data.keyword.messagehub}} **「サービス資格情報」**タブからの値です。

<!--
new topic that includes content from existing topics about samples and migration
-->
