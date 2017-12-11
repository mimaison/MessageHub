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

# Utilizzo della API REST Kafka
{: #rest_using}

L'API REST Kafka fornisce un'interfaccia RESTful a un cluster Kafka. Puoi facilmente produrre e consumare i messaggi e completare le attività di gestione utilizzando
l'API. Per i documenti di riferimento, vedi [Documentazione di Confluent Platform ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://docs.confluent.io/2.0.0/){:new_window}. Solo il formato integrato binario è supportato per le richieste e le risposte in {{site.data.keyword.messagehub}}. I formati incorporati Avro e JSON non sono supportati.

Se stai utilizzando CURL, puoi utilizzare un esempio come il seguente per produrre:
<pre class="pre"><code>
curl -X POST -H "X-Auth-Token:<var class="keyword varname">APIKEY</var>" -H "Content-Type: application/vnd.kafka.binary.v1+json" <var class="keyword varname">kafka-rest endpoint</var>/topics/<var class="keyword varname">topic name</var> -d 

'
{
  "records": [
    {
      "value": "<var class="keyword varname">A base 64 encoded value string</var>"
    }
  ]
}
'
</code></pre>
{: codeblock}

Se stai utilizzando CURL, puoi utilizzare un esempio come il seguente per utilizzare: 
<pre class="pre"><code>
curl -X GET -H "X-Auth-Token:<var class="keyword varname">APIKEY</var>" -H "Accept: application/vnd.kafka.binary.v1+json" <var class="keyword varname">kafka-rest endpoint</var>/topics/<var class="keyword varname">topic name</var>/partitions/<var class="keyword varname">partition ID</var>/messages?offset=<var class="keyword varname">offset to start from</var>
</code></pre>
{: codeblock}


Per CURL, puoi anche adattare gli esempi di codice
descritti in [Confluent docs ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://docs.confluent.io/2.0.0/){:new_window} aggiungendo la seguente riga alla riga di comando:
<pre class="pre">-H "X-Auth-Token: <var class="keyword varname">APIKEY</var>"</pre>
{: codeblock}


<!-- Comment from Andrew
basic introduction, definitely including health warning
-->

