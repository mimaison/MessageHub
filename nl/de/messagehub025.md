---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-26"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Kafka-REST-API verwenden
{: #rest_using}

Die Kafka-REST-API stellt eine REST-konforme Schnittstelle zu einem Kafka-Cluster bereit. Mithilfe der API können Sie ohne großen Aufwand Nachrichten erstellen und verarbeiten sowie Verwaltungstasks ausführen. Referenzinformationen finden Sie in den Dokumenten für [Confluent Platform ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://docs.confluent.io/2.0.0/){:new_window}. Nur das eingebettete Binärformat wird für Anforderungen und Antworten in {{site.data.keyword.messagehub}} unterstützt. Die eingebetteten Avro- und JSON-Formate werden nicht unterstützt.

Wenn Sie mit CURL arbeiten, können Sie für die Erstellung ein Beispiel wie das folgende verwenden:
<pre class="pre"><code>
curl -X POST -H "X-Auth-Token:<var class="keyword varname">API-Schlüssel</var>" -H "Content-Type: application/vnd.kafka.binary.v1+json" <var class="keyword varname">Kafka-REST-Endpunkt</var>/topics/<var class="keyword varname">Topicname</var> -d

'
{
  "records": [
    {
      "value": "<var class="keyword varname">Base 64-codierte Wertzeichenfolge</var>"
    }
  ]
}
'
</code></pre>
{: codeblock}

Wenn Sie mit CURL arbeiten, können Sie für die Verarbeitung ein Beispiel wie das folgende verwenden:
<pre class="pre"><code>
curl -X GET -H "X-Auth-Token:<var class="keyword varname">API-Schlüssel</var>" -H "Accept: application/vnd.kafka.binary.v1+json" <var class="keyword varname">Kafka-REST-Endpunkt</var>/topics/<var class="keyword varname">Topicname</var>/partitions/<var class="keyword varname">Partitions-ID</var>/messages?offset=<var class="keyword varname">Startoffset</var>
</code></pre>
{: codeblock}


Für CURL können Sie auch die Codebeispiele anpassen, die in den
[Confluent-Dokumenten![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://docs.confluent.io/2.0.0/){:new_window} beschrieben sind, indem Sie die folgende Zeile zur Befehlszeile hinzufügen:
<pre class="pre">-H "X-Auth-Token: <var class="keyword varname">API-Schlüssel</var>"</pre>
{: codeblock}


<!-- Comment from Andrew
basic introduction, definitely including health warning
-->

