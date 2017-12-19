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

# Utilización de Kafka Streams con {{site.data.keyword.messagehub}}
{: #kafka_streams }

A partir de la biblioteca Streams 0.10.2.0, el tema de API funciona con {{site.data.keyword.messagehub}} sin necesidad de configuración. Especifique sus credenciales SASL utilizando <code>sasl.jaas.config</code> o un archivo JAAS y establezca <code>replication.factor</code> en 3.

Por ejemplo:

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

donde BOOTSTRAP_SERVERS, USERNAME y PASSWORD son los valores del separador {{site.data.keyword.messagehub}} **Credenciales de servicio** en {{site.data.keyword.Bluemix_notm}}.

<!--
new topic that includes content from existing topics about samples and migration
-->
