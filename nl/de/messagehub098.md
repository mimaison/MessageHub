---

copyright:
  years: 2015, 2017
lastupdated: "2016-11-22"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Voraussetzungen für die Verwendung der MQ Light-API mit Message Hub
{: #mql_reqs}

Die folgenden Voraussetzungen sind für die Verwendung der {{site.data.keyword.mql}}-API mit {{site.data.keyword.messagehub}} erforderlich: 

**Sie müssen explizit ein Kafka-Topic mit dem Namen "MQLight" erstellen, damit die API verwendet werden kann, da alle Nachrichten das Topic "MQLight" durchlaufen. Dieses Topic muss eine einzige Partition enthalten. Durch das Erstellen dieses Topics wird die MQ Light-API für Ihre Serviceinstanz aktiviert.** Weitere Informationen zum Erstellen von Topics in {{site.data.keyword.messagehub}} finden Sie unter [Topics verwalten](/docs/services/MessageHub/messagehub070.html).

Das Topic "MQLight" wird von der MQ Light-API  für die Speicherung der zugehörigen Nachrichtendaten und für die Interaktion mit anderen Kafka-Clients verwendet. Beachten Sie, dass ab der Erstellung dieses Topics
Gebühren gemäß dem im Zahlungsplan für Services angegebenen Standardsatz fällig werden.

Um die MQ Light-API zu inaktivieren, löschen Sie das Topic "MQLight". Beim Löschen des Topics werden auch alle zugehörigen Daten gelöscht.
