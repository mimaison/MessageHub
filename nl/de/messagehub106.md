---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Merkmale der MQ Light-API
{: #mqlight}

Die {{site.data.keyword.mql}}-API stellt eine höhere Abstraktionsebene für das Messaging
bereit als Kafka, d. h. sie ist leichter zu erlernen und in Ihren Anwendungen einfacher zu verwenden.
{:shortdesc}

Das Auswahlkriterium für die Verwendung eines Kafka-Clients oder der {{site.data.keyword.mql}}-API ist
die zu erstellende Messaging-Topologie: 

* Mit Kafka erstellen Sie eine kleine Anzahl von Topics, die eine Vielzahl von Partitionen für jedes Topic enthalten können, um eine hohe Skalierbarkeit zu erzielen. Mithilfe von Consumergruppen können Consumer Nachrichten zwar gemeinsam nutzen, doch jeder Consumer muss darauf achten, dass die zugeordnete Nachrichtenrate auch tatsächlich verarbeitet werden kann.
* Mit der {{site.data.keyword.mql}}-API können Sie eine große Anzahl von Topics mit hierarchisch strukturierten Topicnamen verwenden (z. B. <code>‘/sports/football’</code> und <code>‘/sports/tiddlywinks’</code>). Dies vereinfacht die gemeinsame Nutzung von Nachrichten zwischen Consumern erheblich.

Die Topics in der {{site.data.keyword.mql}}-API unterscheiden sich von
den Kafka-Topics. In der {{site.data.keyword.mql}}-API wird ein einziges Kafka-Topic
mit der Bezeichnung "MQLight" verwendet. Alle über die {{site.data.keyword.mql}}-API gesendeten
und empfangenen Nachrichten durchlaufen dieses eine Kafka-Topic.

Die {{site.data.keyword.mql}}-API ist nur in den folgenden
{{site.data.keyword.Bluemix_notm}}-Regionen verfügbar: 'Vereinigte Staaten (Süden)', 'Vereintes Königreich' und 'Sydney'. Die MQ Light-API ist weder in der Region 'Deutschland' noch in
{{site.data.keyword.Bluemix_notm}} Dedicated verfügbar.

<!-- begin PRODUCTION ONLY -->
Weitere Informationen zum Auswählen der geeigneten API finden Sie in [Gründe für die Verwendung der Kafka-API](/docs/services/MessageHub/messagehub054.html), [Gründe für die Verwendung der MQ Light-API](/docs/services/MessageHub/messagehub076.html) und [Gründe für die Verwendung der Kafka-REST-API](/docs/services/MessageHub/messagehub065.html).
<!-- end PRODUCTION ONLY -->
