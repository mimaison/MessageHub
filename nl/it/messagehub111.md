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

# Utilizzo di Kafka Streams con {{site.data.keyword.messagehub}}
{: #kafka_streams }

A partire dalla libreria Streams 0.10.2.0, le API di argomento ora funzionano con {{site.data.keyword.messagehub}} senza necessità di configurazione. Specifica le tue credenziali SASL utilizzando <code>sasl.jaas.config</code> o un file JAAS e imposta <code>replication.factor</code> su 3.

Ad esempio:

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

dove BOOTSTRAP_SERVERS, USERNAME e PASSWORD sono i valori indicati nella scheda **Credenziali del servizio** {{site.data.keyword.messagehub}} in
{{site.data.keyword.Bluemix_notm}}.

<!--
new topic that includes content from existing topics about samples and migration
-->
