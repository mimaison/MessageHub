---

copyright:
  years: 2015, 2017
lastupdated: "2017-02-01"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Mit vorhandenen MQ Light-Anwendungen verbinden
{: #mql_exist_apps}

Sie können vorhandene Anwendungen mit dem Service verbinden, die entweder für {{site.data.keyword.IBM_notm}} MQ oder
für den {{site.data.keyword.mql}}-{{site.data.keyword.Bluemix_notm}}-Service ausgeführt werden. Die Apps
funktionieren weiter in der gewohnten Weise.
{:shortdesc}

Führen Sie die folgenden Prüfungen durch, um vorhandene Apps zu verbinden:

* Stellen Sie sicher, dass die App die neueste verfügbare {{site.data.keyword.mql}}-API-Clientversion für Ihre Sprache verwendet.
* Stellen Sie sicher, dass die aus der Umgebungsvariablen VCAP_SERVICES extrahierten Verbindungsdetails auf den Servicetyp <code>messagehub</code> verweisen und den Benutzernamen der Verbindung aus der Eigenschaft <code>credentials.user</code> abrufen und nicht aus der Eigenschaft <code>credentials.username</code>, sowie die Such-URL der Verbindung aus der Eigenschaft <code>credentials.mqlight_lookup_url</code> und nicht aus der Eigenschaft <code>credentials.connectionLookupURI</code>. Weitere Informationen finden Sie in [Umgebungsvariable VCAP_SERVICES](/docs/services/MessageHub/messagehub071.html).

	Beachten Sie, dass dieser Schritt automatisch ausgeführt wird, wenn Sie den Java&trade;-Client verwenden und 'null' für den Parameter 'endpointService' im Aufruf 'create()' angeben, damit der Client die Informationen selbstständig abruft.
	
* Ihre Anwendung muss Verbindungen über TLS Version 1.2 unterstützen. Die Umgebungsvariable VCAP_SERVICES enthält nicht mehr die Eigenschaft <code>credentials.nonTLSConnectionLookupURI</code> zum Erstellen einer Nicht-TLS-Verbindung.

Beachten Sie außerdem die folgenden Hinweise:

* Die Grenzwerte für Nachrichten sind mit {{site.data.keyword.messagehub}} konsistent, können jedoch von anderen Servern abweichen, die
die {{site.data.keyword.mql}}-API unterstützen. Weitere Informationen finden Sie in [Maximalwerte](/docs/services/MessageHub/messagehub083.html).
* JMS wird nicht unterstützt.
