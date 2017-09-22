---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}



# Fehler an das {{site.data.keyword.messagehub}}-Team melden
{: #report_problem}

Wenn ein Problem mit {{site.data.keyword.messagehub}} auftritt, überprüfen Sie zunächst die Seite 'Status' in [{{site.data.keyword.Bluemix_notm}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://status.ng.bluemix.net/){:new_window}. 

Wenn Sie Unterstützung vom {{site.data.keyword.messagehub}}-Team benötigen, sammeln Sie bitte möglichst viele der folgenden Informationen:
{:shortdesc}

1. In welcher {{site.data.keyword.Bluemix_notm}}-Region wird Ihre {{site.data.keyword.messagehub}}-Instanz bereitgestellt (z. B. 'Vereinigte Staaten (Süden)' oder 'Vereintes Königreich')? 
2. In welcher Schnittstelle treten Probleme auf (REST, Kafka, AMQP oder Bridges)?
3. Wann ist das Problem zum ersten Mal aufgetreten (Datum, genaue Uhrzeit und Zeitzone)? Wie lange war Ihre App zu diesem Zeitpunkt bereits aktiv?
4. Tritt das Problem weiterhin auf? Können Sie das Problem erneut hervorrufen?
5. Wie lautet die Instanz-ID des von Ihnen verwendeten {{site.data.keyword.messagehub}}-Service?
Sie finden diese ID im Feld "instance_id" in der JSON-Umgebungsvariablen VCAP_SERVICES.
6. Welcher Kafka- oder REST-Client wird von Ihrer Anwendung verwendet? Wie lauten die zugehörigen Versionsdetails?
7. Wie lauten die Details Ihrer Clientkonfiguration?
8. Verfügen Sie über Ausschnitte des Anwendungsprotokolls, in denen das Problem angegeben ist?
9. Welches Problem haben Sie bemerkt? Welche Topics, Client-IDs und Gruppen-IDs sind betroffen?
10. Wie wirkt sich das Problem auf Ihren Service aus?















