---

copyright:
  years: 2015, 2017
lastupdated: "2017-02-08"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Unterschiede in Message Hub zwischen Bluemix Public- und Bluemix Dedicated-Umgebungen
{: #public_dedicated}

{{site.data.keyword.Bluemix}} ist eine nach offenen Standards konzipierte cloudbasierte Plattform
zum Erstellen, Ausführen und Verwalten von Anwendungen. {{site.data.keyword.Bluemix_notm}} stellt öffentliche
und dedizierte Implementierungsmodelle bereit. {{site.data.keyword.messagehub}} ist in beiden
Umgebungen verfügbar. 

## {{site.data.keyword.Bluemix_notm}} Public-Umgebung
{: notoc}

{{site.data.keyword.Bluemix_notm}} Public stellt einen ökonomischen Public Cloud-Service
bereit, der nach tatsächlicher Nutzung abgerechnet wird und die gemeinsame Nutzung der Infrastruktur
mit anderen Benutzern ermöglicht.

In {{site.data.keyword.Bluemix_notm}} Public basieren die Kosten für
{{site.data.keyword.messagehub}} auf zwei Faktoren: auf der Anzahl der Partitionen, die Sie verwenden,
und auf der Anzahl der Nachrichten, die Sie senden und empfangen. Die Speicherung der Nachrichtendaten
in den Topics erfolgt ohne zusätzliche Kosten bis zu einer Obergrenze von 1 GB pro Partition.

Weitere Informationen finden Sie unter [{{site.data.keyword.Bluemix_notm}} Public ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/cloud-computing/bluemix/public){:new_window}.


## {{site.data.keyword.Bluemix_notm}} Dedicated-Umgebung
{: notoc}

{{site.data.keyword.Bluemix_notm}} Dedicated stellt eine stärker isolierte Umgebung
bereit, in der Ihre Infrastruktur nicht zur gemeinsamen Nutzung freigegeben und in einem separaten
und von {{site.data.keyword.IBM_notm}} verwalteten SoftLayer-Konto gehostet wird.
Diese Umgebung ist über eine sichere Verbindung mit {{site.data.keyword.Bluemix_notm}} Public und mit Ihrem eigenen Netz verbunden.

In einer dedizierten Instanz von {{site.data.keyword.messagehub}} wird der Service an sich
in Rechnung gestellt und nicht der Umfang der Nutzung. Sie können innerhalb der Umgebung bis zu 75 Partitionen
nutzen, einschließlich aller Organisationen und Bereiche. Für jede Partition gilt eine Obergrenze von 10 GB, um sicherzustellen, dass
der vorhandene Speicherplatz im Cluster nicht überschritten wird. 

Die Kibana- und Grafana-Dashboards zum Überwachen des Service werden in {{site.data.keyword.Bluemix_notm}} Dedicated nicht unterstützt.

Weitere Informationen finden Sie unter [{{site.data.keyword.Bluemix_notm}} Dedicated ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/cloud-computing/bluemix/dedicated/){:new_window}.


