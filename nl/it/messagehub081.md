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
{:table: .aria-labeledby="caption"}

# Scambio di messaggi tra l'API MQ Light e le API Kafka o REST Kafka
{: #mql_exchange}

I messaggi di {{site.data.keyword.mql}} vengono memorizzati in un singolo argomento Kafka sottostante denominato "MQLight" e sono codificati come descritto nella seguente tabella. Questa codifica può essere utilizzata anche da altri tipi di API, come Kafka o REST Kafka, per scambiare messaggi con le applicazioni che utilizzano
l'API {{site.data.keyword.mql}}.

## Formato dei messaggi Kafka
{: #kafka_format notoc}

<table border='1'>
<caption>Tabella 1. Formato dei messaggi Kafka</caption>
  <tr>
    <th> Chiave </th>
    <th> Valore </th>
  </tr>
  <tr>
    <td> Facoltativo (non utilizzato dall'API)
	<p></p>
	</td>
    <td>**1 byte**
	<p>		     Identificativo di struttura API MQ Light, che è sempre 0xFA.</p>
    <p><var class="keyword varname">**n**</var> **bytes**</p>
    <p>		    Messaggio con codifica AMQP (formattato in base al formato wire AMQP). </p></td>
  </tr>
</table>


