---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-05"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Bekannte Einschränkungen
{: #restrictions}


## Anzahl der {{site.data.keyword.messagehub}}-Instanzen für jeden {{site.data.keyword.Bluemix_notm}}-Bereich
{: #instances_space notoc}

Es darf nur eine {{site.data.keyword.messagehub}}-Instanz für jeden {{site.data.keyword.Bluemix_notm}}-Bereich geben.

##Topics und Partitionen
{: #topics_partitions notoc}

*  Topicnamen sind auf ein Maximum von 100 Zeichen begrenzt.
*  Die Standardanzahl von Partitionen für ein Topic ist '1'.
*  Für jeden {{site.data.keyword.Bluemix_notm}}-Bereich gilt ein Grenzwert von 100 Partitionen. Für die
Erstellung weiterer Partitionen müssen Sie einen neuen {{site.data.keyword.Bluemix_notm}}-Bereich verwenden.

## Aufbewahrungsdauer für Nachrichten
{: #message_retention notoc}

In Kafka werden Nachrichten standardmäßig bis zu 24 Stunden aufbewahrt und jede Partition wird auf
1 GB begrenzt. Wenn die Obergrenze von 1 GB erreicht ist, werden die ältesten Nachrichten gelöscht, damit
der Grenzwert eingehalten wird.

Die Aufbewahrungsdauer für Nachrichten können Sie beim Erstellen eines Topics
in der Benutzerschnittstelle oder mit der Verwaltungs-API ändern. Das Zeitlimit muss im Bereich von 1 Stunde (Minimalwert) bis
30 Tage (Maximalwert) liegen.

## Topics in Kafka erstellen und löschen
{: #create_delete notoc}

Das Erstellen und das Löschen von Topics in Kafka erfolgt durch asynchrone Operationen, deren
Ausführung einige Zeit dauern kann. Es wird empfohlen, auf Verwendungsmuster zu verzichten,
die auf das schnelle Erstellen und Löschen von Topics angewiesen sind oder auf das schnelle Löschen
und erneute Erstellen von Topics.

## Kafka-REST-API
{: #trouble_rest notoc}

*  Nur das eingebettete Binärformat wird für Anforderungen und Antworten unterstützt. Das eingebettete Avro-Format wird nicht unterstützt.
*  Gleichzeitige Anforderungen werden für eine Konsumenteninstanz nicht unterstützt.
   Lese-, Commit- oder Löschanforderungen, die sich auf eine Konsumenteninstanz beziehen,
sollten erst gesendet werden, wenn für alle ausstehenden Anforderungen dieser Instanz entsprechende Antworten empfangen wurden.

## Ratenbegrenzung in der Kafka-REST-API
{: #kafka_rate notoc}

Für Anwendungen, die die Kafka-REST-API verwenden, können Ratenbegrenzungen
für jeden API-Schlüssel (ApiKey) gelten. Wenn eine solche Begrenzung auftritt,
reagiert die API mit dem folgenden HTTP-Fehler:

<code>429 Too Many Requests</code>
{:screen}

Wenn dieser Fehler angezeigt wird, warten Sie etwas und übergeben Sie die Anforderung erneut.

## Täglicher Neustart der Kafka-REST-API
{: #rest_restart notoc}

Die Kafka-REST-API wird einmal pro Tag für einen kurzen Zeitraum
erneut  gestartet. In diesem Zeitraum ist die Kafka-REST-API möglicherweise
nicht verfügbar. In diesem Fall wird empfohlen, dass Sie Ihre Anforderung
wiederholen. Nach dem Neustart der REST-API müssen Sie Ihre Kafka-Konsumenteninstanzen
erneut erstellen. In diesem Fall gibt die
REST-API den folgenden JSON-Code zurück:

```'{"error_code":40403,"message":"Consumer instance not found."}'
```
{:screen}

## Allgemeine Kafka-Konsumenten-API
{: #kafka_consumer notoc}

Die einfache oder allgemeine Apache Kafka-Konsumenten-API der Version 0.8.2 kann nicht mit {{site.data.keyword.messagehub}} verwendet werden. Verwenden Sie stattdessen die neue Konsumenten-API von Kafka 0.9.
