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

# Vorgehensweise zum Verbinden und Authentifizieren
{: #rest_connect}

Um eine Verbindung zu {{site.data.keyword.messagehub}} herzustellen, verwendet die Kafka-REST-API die Berechtigungsnachweise <code>api_key</code> und <code>kafka_rest_url</code>
aus [Umgebungsvariable VCAP_SERVICES](/docs/services/MessageHub/messagehub071.html).

Um sich bei der Kafka-REST-API von {{site.data.keyword.messagehub}} zu authentifizieren, müssen Sie die Berechtigung <code>api_key</code> im X-Auth-Token-Header Ihrer Anforderungen angeben.
