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

# Vorgehensweise zum Verbinden und Authentifizieren
{: #kafka_connect}


Um eine Verbindung zu {{site.data.keyword.messagehub}} herzustellen, verwendet
die Kafka-API die Berechtigungsnachweise 
```kafka_brokers_sasl
``` 
sowie den Benutzer
```
und das Kennwort
```

 ```password
```
 aus
[Umgebungsvariable VCAP_SERVICES](/docs/services/MessageHub/messagehub071.html).

## Verbinden und Authentifizieren in einer Nicht-Java-Anwendung
{: #kafka_notjava notoc}

Der {{site.data.keyword.messagehub}}-Service in der gegenwärtigen
Version authentifiziert Clients mithilfe von SASL PLAIN. Berechtigungsnachweise werden über eine verschlüsselte Verbindung übertragen.
Diese neue Funktion wurde in Kafka 0.10.0.X hinzugefügt. Jeder Client, der Kafka 0.10 mit SASL PLAIN unterstützt,
sollte auch mit {{site.data.keyword.messagehub}} verwendet werden können. Dies gilt beispielsweise für die folgenden Clients:

* [librdkafka ![Symbol für externen Link](../../icons/launch-glyph.svg "External link icon")](https://github.com/edenhill/librdkafka/){:new_window}
* [confluent-kafka-python ![Symbol für externen Link](../../icons/launch-glyph.svg "External link icon")](https://github.com/confluentinc/confluent-kafka-python){:new_window}

Wenn Sie die frühere Kafka-Clientversion 0.9.0.0 nutzen, müssen Sie ein angepasstes Anmeldemodul verwenden, das
Sie von [{{site.data.keyword.messagehub}}-Anmeldemodul ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/ibm-messaging/message-hub-samples/blob/master/kafka-0.9/message-hub-login-library/messagehub.login-1.0.0.jar){:new_window} herunterladen können.

