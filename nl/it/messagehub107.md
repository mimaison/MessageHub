---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-27"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Che cos'è {{site.data.keyword.messagehub}}?

{{site.data.keyword.messagehub}} implementa la messaggistica di pubblicazione/sottoscrizione
utilizzando degli argomenti. A differenza di altri sistemi di messaggistica, {{site.data.keyword.messagehub}} fornisce gli argomenti ma non le code. {{site.data.keyword.messagehub}} offre anche delle
funzionalità aggiuntive come l'API {{site.data.keyword.mql}} e i bridge ad altri sistemi.

{{site.data.keyword.messagehub}} include tre API: l'API Kafka, l'API {{site.data.keyword.mql}} e l'API
REST Kafka. Per ulteriori informazioni sulla
creazione di applicazioni di messaggistica che utilizzano le API, vedi [Utilizzo di un client Kafka](/docs/services/MessageHub/messagehub050.html), [Utilizzo di un client API MQ Light](/docs/services/MessageHub/messagehub075.html) e [Utilizzo della API REST Kafka](/docs/services/MessageHub/messagehub025.html).

{{site.data.keyword.messagehub}} supporta inoltre
i bridge a una selezione di altri sistemi. Un bridge è un collegamento unidirezionale a un altro
sistema. Un bridge può prendere i messaggi dall'altro sistema e pubblicarli su un argomento o consumare
i messaggi da un argomento e inviarli all'altro sistema. In questo modo, puoi utilizzare {{site.data.keyword.messagehub}} per l'integrazione con altri sistemi senza dover scrivere il codice. Per ulteriori informazioni, vedi [Collegamento ad altri servizi utilizzando i bridge](/docs/services/MessageHub/messagehub088.html).

{{site.data.keyword.messagehub}} è basato sul progetto open-source
Apache Kafka, un backbone di messaggistica altamente scalabile e ad alte prestazioni
comprovato in molti ambienti di produzione. Per ulteriori informazioni, vedi [{{site.data.keyword.messagehub}} e Apache Kafka](/docs/services/MessageHub/messagehub073.html).
