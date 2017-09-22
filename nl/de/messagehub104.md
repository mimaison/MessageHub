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

# Kafka-Java-Client verwenden
{: #kafka_using}

## Java-Kafka-API-Beispiel verwenden, herunterladen und ausführen
{: notoc}

Das Java&trade;-Kafka-API-Beispiel ist ein in Java geschriebenes Beispiel für einen Producer und einen Consumer unter Verwendung der Kafka-API. Dieses Beispiel kann lokal oder in {{site.data.keyword.Bluemix_short}} ausgeführt werden.

Der Beispielcode befindet sich im [GitHub-Projekt 'message-hub-samples' ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}. Obwohl das Beispiel die Kafka-API zum Senden und Empfangen von Nachrichten nutzt, verwendet es die {{site.data.keyword.messagehub}}-Verwaltungs-API zum Erstellen des Topics, an das es Nachrichten sendet und von dem es Nachrichten empfängt.

Weitere Informationen zum Einrichten und Ausführen des Beispiels finden Sie in der Datei [README.md ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}.

Eine schrittweise Anleitung zum Ausführen des Beispiels finden Sie in [Einführung in {{site.data.keyword.messagehub}}](/docs/services/MessageHub/index.html#getting_started_steps).

## Liberty for Java-Beispiel verwenden, herunterladen und ausführen
{: #liberty_sample notoc}

Das Liberty for Java-Beispiel implementiert eine einfache Anwendung, die in der Liberty-Laufzeitumgebung bereitgestellt wird. Die Anwendung verwendet die Kafka-API für {{site.data.keyword.messagehub}} zum Erstellen und Verarbeiten von Nachrichten.
Die Anwendung stellt darüber hinaus ein Web-Front-End bereit, das Sie für die Verwaltung verwenden können.

Den zugehörigen Beispielcode finden Sie im [GitHub-Projekt 'message-hub-samples' ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-liberty-sample){:new_window}.

## Vorgehensweise bei der Migration des Kafka-Clients von Version 0.9.x auf Version 0.10.x
{: #kafka_migrate notoc}


Wenn Sie mit den Java-Clients arbeiten, können Sie jetzt die
offiziell verfügbaren Kafka-Clients der Version 0.10.x verwenden. Es wird dringend
empfohlen, von der Version 0.9.x auf den aktuellen Stand der Version 0.10.x
umzustellen (die neueste Version ist 0.10.2.1). Führen Sie die folgenden Schritte aus: 

1. Löschen Sie das JAR-Modul für die {{site.data.keyword.messagehub}}-Anmeldung.
2. Ändern Sie Ihre Datei <code>jaas.conf</code> wie folgt: 
    ```
        KafkaClient {
          org.apache.kafka.common.security.plain.PlainLoginModule required
          serviceName="kafka"
            username="<your username>"
            password="<your password>";
        };
    ```
    {: codeblock}

3. Fügen Sie die folgende Zeile in Ihren Eigenschaften 'consumer' und 'producer' hinzu: <code>sasl.mechanism=PLAIN</code>.


## Eigenschaft 'sasl.jaas.config' verwenden
{: #sasl_prop notoc}
Wenn Sie einen Kafka-Client der Version 0.10.2.1 oder höher verwenden, können Sie die Eigenschaft <code>sasl.jaas.config</code> anstelle einer JAAS-Datei
für die Clientkonfiguration verwenden. Um eine Verbindung zu {{site.data.keyword.messagehub}} herzustellen, legen Sie
<code>sasl.jaas.config</code> wie folgt fest: 
<pre>
<code>    sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required \
    username="USERNAME" \
    password="PASSWORD";</code>
</pre>
{:codeblock}

Dabei sind USERNAME und PASSWORD die Werte aus Ihrer {{site.data.keyword.messagehub}}-Registerkarte **Serviceberechtigungsnachweise** in {{site.data.keyword.Bluemix_notm}}.

Wenn Sie <code>sasl.jaas.config</code> verwenden, können Clients, die in derselben JVM ausgeführt werden, verschiedene Berechtigungsnachweise verwenden. Weitere
Informationen finden Sie unter [Kafka-Clients konfigurieren ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://kafka.apache.org/documentation/#security_sasl_plain_clientconfig){:new_window}.

## APIs für die Topicverwaltung
{: #topic_admin notoc}

Wenn Sie einen Kafka-Client der Version 0.11 oder höher verwenden oder Kafka Streams Version 0.10.2.0 oder höher, können Sie APIs verwenden, um Topics zu erstellen oder zu löschen. Für die zulässigen Einstellungen beim Erstellen von Topics gelten bestimmte Einschränkungen. Gegenwärtig können Sie nur die folgenden Einstellungen ändern:

<dl>
<dt>cleanup.policy</dt>
<dd>Zulässige Werte sind <code>delete</code> (Standardwert), <code>compact</code> oder <code>delete,compact</code></dd>
<dt>retention.ms</dt>
<dd>Der Standardaufbewahrungszeitraum ist 24 Stunden. Der Mindestwert ist 1 Stunde und der Höchstwert ist
30 Tage. Geben Sie den Wert in Stunden an.

<p>**Anmerkung:**
Wenn für die Bereinigungsrichtlinie (cleanup.policy) nur der Wert <code>compact</code> angegeben ist, wird automatisch der Wert <code>delete</code>
hinzugefügt, aber die Löschfunktion wird auf Zeitbasis inaktiviert. Die Nachrichten in dem Topic werden bis 1 GB komprimiert. Die Löschfunktion wird
erst beim Überschreiten dieses Werts aktiviert.</p>
</dd>
</dl>

## Unterstützung für Kafka Streams
{: #kafka_streams notoc}

Ab Version 0.10.2.0 der Streams-Bibliothek können die Topic-APIs jetzt ohne weitere Konfigurationsschritte zusammen mit {{site.data.keyword.messagehub}} verwendet werden. Geben Sie Ihre SASL-Berechtigungsnachweise in <code>sasl.jaas.config</code> oder in einer JAAS-Datei an und legen Sie für <code>replication.factor</code> den Wert 3 fest.

Beispiel:

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

Dabei sind BOOTSTRAP_SERVERS, USERNAME und PASSWORD die Werte aus Ihrer {{site.data.keyword.messagehub}}-Registerkarte **Serviceberechtigungsnachweise** in
{{site.data.keyword.Bluemix_notm}}.

<!--
new topic that includes content from existing topics about samples and migration
-->
