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

# Über Bridges mit anderen Services verbinden
{: #bridges}

Bridges sind unidirektionale Verbindungen zwischen {{site.data.keyword.messagehub}} und anderen Services. Sie ermöglichen
das Lesen von Daten aus {{site.data.keyword.messagehub}} und das Schreiben der Daten in andere
Services oder das Lesen von Daten aus anderen Services und das Schreiben der Daten in {{site.data.keyword.messagehub}}.
{:shortdesc}

Die Verwendung von Bridges in {{site.data.keyword.messagehub}} bietet einige wichtige Vorteile:  

* Bridges können administrativ definiert werden, ohne Anwendungscode zu schreiben.
* Der Lebenszyklus jeder Bridge wird vom {{site.data.keyword.messagehub}}-Service überwacht und verwaltet. Wenn in einer Bridge beispielsweise ein Fehler auftritt, wird sie von {{site.data.keyword.messagehub}} automatisch neu gestartet.
* Bridges werden in die {{site.data.keyword.Bluemix_short}}-Plattform integriert. Beispielsweise werden die von Bridges generierten Protokollierungs- und Überwachungsdaten an das Kibana- und an das Grafana-Dashboard weitergeleitet.

Bridges sind besonders in den beiden folgenden gängigen Anwendungsszenarios hilfreich:

* Daten aus mindestens einer Datenquelle in {{site.data.keyword.messagehub}} übernehmen
* Daten aus {{site.data.keyword.messagehub}} in einen anderen Service übertragen (z. B. in den Langzeitspeicher)

## {{site.data.keyword.messagehub}}-Bridges
{: notoc}

* Die beiden folgenden Bridge-Typen werden bereitgestellt:  
  - {{site.data.keyword.objectstorageshort}}-Bridge zum Übertragen von {{site.data.keyword.messagehub}}-Daten in eine Instanz des [Object Storage-Service ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/services/ObjectStorage/index.html){:new_window}.
  - MQ-Bridge zum Übertragen von Nachrichtendaten aus {{site.data.keyword.IBM}} MQ in ein Topic in {{site.data.keyword.messagehub}}. Künftig sollen noch weitere Bridge-Typen unterstützt werden.
* Gegenwärtig sind Bridges in allen {{site.data.keyword.Bluemix_notm}} Public-Umgebungen verfügbar. In {{site.data.keyword.Bluemix_short}} Dedicated stehen keine Bridges zur Verfügung.
* Zum Verwalten von Bridges können die beiden folgenden Methoden verwendet werden:
  - Eine [REST-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/ibm-messaging/message-hub-docs){:new_window}, d. h. eine Erweiterung der vorhandenen {{site.data.keyword.messagehub}}-Verwaltungs-API. Beispiele für die Verwendung von 'curl' bei der Verwaltung des Lebenszyklus von Bridges finden Sie unter [message-hub-docs ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/ibm-messaging/message-hub-docs){:new_window}. Bei der Weiterentwicklung von Bridges sind Änderungen an dieser REST-API möglich. Es ist vorgesehen, diese API noch stabiler zu gestalten.
  - Das {{site.data.keyword.messagehub}}-Dashboard in der {{site.data.keyword.Bluemix_notm}}-Konsole.
* Sie können maximal zwei Bridges eines beliebigen Typs einer Instanz des {{site.data.keyword.messagehub}}-Service zuordnen. Bei der Weiterentwicklung von Bridges wird auch diese Begrenzung immer wieder überprüft.
* Über die zugehörigen Messaging-Operationen hinaus fallen keine weiteren Gebühren für die Verwendung von Bridges an.
* Die {{site.data.keyword.objectstorageshort}}-Bridge verwendet das Zeilenvorschubzeichen als Trennzeichen beim Verketten der Nachrichten, die als Daten in {{site.data.keyword.objectstorageshort}} geschrieben werden. Dies führt zur Inkompatibilität mit Nachrichten, die eingebettete Zeilenvorschubzeichen oder binäre Nachrichtendaten enthalten. 
* Die gegenwärtig von der {{site.data.keyword.objectstorageshort}}-Bridge verwendeten Namenskonventionen für Objekte, werden möglicherweise noch geändert. 
* Die MQ-Bridge unterstützt nicht die Verwendung von SSL/TLS für den Schutz und die Integrität bei der Datenübertragung zwischen der Bridge und dem MQ-Warteschlangenmanager. Es ist vorgesehen, Unterstützung für die Verwendung von SSL/TLS in der Bridge hinzuzufügen. 

Sie können den [{{site.data.keyword.SecureGatewayfull}}-Service ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/services/SecureGateway/secure_gateway.html){:new_window} jedoch verwenden, um Ihre Daten
durch einen sicheren Tunnel zwischen {{site.data.keyword.Bluemix_notm}}
und einem {{site.data.keyword.SecureGateway}}-Client zu senden, den Sie lokal installieren
können. In dieser Konfiguration wird die Datenübertragung an beiden Enden des Tunnels nicht durch
SSL/TLS geschützt.
