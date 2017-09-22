---

copyright:
  years: 2015, 2017
lastupdated: "2017-01-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Auswählen der geeigneten API
{: #choose_api}

{{site.data.keyword.messagehub}} unterstützt drei APIs. Die nachfolgenden Informationen sollen Ihnen helfen, die geeignete API für Ihre Zwecke auszuwählen:

## Gründe für die Verwendung der Kafka-API
{: #why_kafka notoc}

Es gibt einige Gründe, warum Sie die Kafka-API den anderen von {{site.data.keyword.messagehub}} bereitgestellten Schnittstellen vorziehen könnten. Zu diesen Gründen zählen:
{:shortdesc}


* Ihre App kann einfacher in vorhandene Systeme integriert werden, für die Kafka-Unterstützung bereitgestellt wird (z. B. {{site.data.keyword.IBM}} {{site.data.keyword.streaminganalyticsshort}} und {{site.data.keyword.sparks}}).
* Sie bietet eine niedrigere Latenz und einen höheren Durchsatz als die anderen APIs.
* Sie bietet eine umfassendere API als die Kafka-REST-API.


## Gründe für die Verwendung der {{site.data.keyword.mql}}-API
{: #why_mql notoc}

Die {{site.data.keyword.mql}}-API stellt eine höhere Abstraktionsebene
bereit als die Kafka-API. {{site.data.keyword.mql}} ermöglicht eine schnelle Erstellung
portierbarer Apps in einem Unified Messaging-Modell, das sowohl Messaging-Systeme mit
Warteschlangen als auch mit Publish/Subscribe unterstützt.
{:shortdesc}

Für den Austausch von Nachrichten zwischen Apps werden dynamisch erstellte Ziele verwendet, die
hierarchisch strukturiert (z. B. <code>‘/sport/fussball’</code>) und durch Platzhalter gruppiert
werden können (z. B. 
<code>‘/sports/#’</code>). Außerdem können einfache Steuerelemente für Bereitstellungszusicherung und Nachrichtenablauf verwendet werden.
Mit diesen Funktionen können Sie Szenarios wie das Auslagern von Verarbeitungsprozessen sowie Ereignisbenachrichtigung und
Stapelverarbeitung direkt und ohne Umwege implementieren.

Neben dem Senden von Nachrichten zwischen anderen Apps kann die {{site.data.keyword.mql}}-API auch für den Nachrichtenaustausch mit Apps genutzt werden, die Kafka-REST oder Kafka-APIs verwenden. Alternativ können Sie Apps auch lokal mit {{site.data.keyword.IBM_notm}} MQ verwenden.


## Gründe für die Verwendung der Kafka-REST-API
{: #why_rest notoc}

Die Kafka-REST-API ist eine praktische Schnittstelle, die in den folgenden Situationen verwendet werden kann:  

* Wenn ein Entwickler schnell mit der Verwendung von {{site.data.keyword.messagehub}} beginnen möchte.
* In bestimmten Anwendungsfällen mit niedrigem Durchsatz, bei denen die Latenz kein kritischer Faktor ist.
* Bei der Fehlerbehebung und Fehlersuche.

Die Kafka-REST-API ist nicht konzipiert als Schnittstelle für hohen Durchsatz und niedrige Latenz.​Für solche Anforderungen wird empfohlen, die Kafka-API für die Verbindung zu und von {{site.data.keyword.messagehub}} zu verwenden. Weitere Informationen finden Sie in [Kafka-Client verwenden](/docs/services/MessageHub/messagehub050.html#kafka_client).












