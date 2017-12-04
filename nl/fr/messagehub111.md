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

# Utilisation de Kafka Streams avec {{site.data.keyword.messagehub}}
{: #kafka_streams }

Depuis la bibliothèque Streams 0.10.2.0, les API de sujet fonctionnent avec {{site.data.keyword.messagehub}} sans qu'aucune configuration ne soit requise. Spécifiez vos données d'identification SASL à l'aide de <code>sasl.jaas.config</code> ou d'un fichier JAAS et définissez <code>replication.factor</code> sur 3.

Par exemple :

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

Où BOOTSTRAP_SERVERS, USERNAME et PASSWORD correspondent aux valeurs issues de l'onglet **Données d'identification pour le service** {{site.data.keyword.messagehub}} dans {{site.data.keyword.Bluemix_notm}}.

<!--
new topic that includes content from existing topics about samples and migration
-->
