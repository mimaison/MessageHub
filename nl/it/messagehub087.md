---

copyright:
  years: 2015, 2017
lastupdated: "2017-01-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Scelta fra le tre API
{: #choose_api}

{{site.data.keyword.messagehub}} supporta tre API. Ecco alcune informazioni per aiutarti a scegliere quella più appropriata:

## Perché utilizzare l'API Kafka?
{: #why_kafka notoc}

Ci sono alcuni motivi per cui si potrebbe scegliere di utilizzare l'API Kafka rispetto alle altre interfacce
           fornite da {{site.data.keyword.messagehub}}. I motivi includono i seguenti:
{:shortdesc}


* È più facile integrare la tua applicazione con i sistemi esistenti che hanno il supporto Kafka, ad esempio {{site.data.keyword.IBM}} {{site.data.keyword.streaminganalyticsshort}} e {{site.data.keyword.sparks}}.
* Offre una latenza più bassa e una velocità effettiva superiore rispetto alle altre API.
* Offre un'API più articolata dell'API REST Kafka.


## Perché utilizzare l'API {{site.data.keyword.mql}}?
{: #why_mql notoc}

L'API {{site.data.keyword.mql}} fornisce un livello di astrazione
superiore rispetto all'API Kafka. {{site.data.keyword.mql}} consente di scrivere le applicazioni in modo rapido e portabile in un modello di messaggistica unificata che supporta i modelli di accodamento e di pubblicazione/sottoscrizione. 
{:shortdesc}

Le applicazioni scambiano messaggi utilizzando destinazioni create in modo
dinamico, che puoi strutturare in forma gerarchica (ad esempio, <code>‘/sports/football’</code>), raggruppare usando caratteri jolly (ad esempio,
<code>‘/sports/#’</code>) e dotare di semplici controlli per l'assicurazione di consegna e la scadenza del messaggio.
Ciò ti consente di implementare scenari come lo scaricamento del carico di lavoro, la notifica evento e l'elaborazione batch in modo diretto.

Oltre a inviare messaggi tra applicazioni diverse utilizzando l'API {{site.data.keyword.mql}}, puoi anche scambiare messaggi con le applicazioni che utilizzano le API REST o Kafka. In alternativa, puoi anche utilizzare le applicazioni in loco con {{site.data.keyword.IBM_notm}} MQ.


## Perché utilizzare l'API REST Kafka?
{: #why_rest notoc}

L'API REST Kafka è una pratica interfaccia che può essere utilizzata nelle
            seguenti situazioni:

* Laddove uno sviluppatore vuole iniziare rapidamente a utilizzare {{site.data.keyword.messagehub}}
* In alcuni casi d'uso a bassa velocità effettiva dove la latenza non è un fattore critico
* Per eseguire il debug e la ricerca di malfunzionamenti

L'API REST Kafka non è stata concepita per essere un'interfaccia ad elevata velocità effettiva e a bassa latenza.Per questi tipi di requisiti, si consiglia di utilizzare l'API Kafka per la connessione da e verso {{site.data.keyword.messagehub}}. Per ulteriori informazioni, vedi [Utilizzo di un client Kafka](/docs/services/MessageHub/messagehub050.html#kafka_client).












