---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-05"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Limitazioni note
{: #restrictions}


## Numero di istanze {{site.data.keyword.messagehub}}
                per ciascuno spazio {{site.data.keyword.Bluemix_notm}}
{: #instances_space notoc}

Puoi avere solo una singola istanza {{site.data.keyword.messagehub}} per ciascuno spazio {{site.data.keyword.Bluemix_notm}}.

##Argomenti e partizioni
{: #topics_partitions notoc}

*  I nomi argomento sono limitati a un massimo di 100 caratteri.
*  Il numero predefinito di partizioni per un argomento è uno.
*  Ogni spazio {{site.data.keyword.Bluemix_notm}} ha un limite di 100 partizioni. Per creare
                    più partizioni, devi utilizzare un nuovo spazio {{site.data.keyword.Bluemix_notm}}.

## Conservazione dei messaggi
{: #message_retention notoc}

Per impostazione predefinita, i messaggi vengono conservati in Kafka per un massimo di 24 ore e
ciascuna partizione ha un limite massimo di 1 GB. Se viene raggiunto il limite massimo di 1 GB, i messaggi vengono eliminati per restare entro il limite.

Puoi modificare il limite di tempo per la conservazione dei messaggi quando
crei un argomento utilizzando l'interfaccia utente o
l'API di amministrazione. Il limite di tempo è pari a un minimo di un'ora e
a un massimo di 30 giorni.

## Creazione ed eliminazione di argomenti in Kafka
{: #create_delete notoc}

In Kafka, la creazione e l'eliminazione di argomenti sono delle operazioni asincrone
il cui completamento potrebbe richiedere un certo tempo. Si consiglia di evitare
i modelli di utilizzo che si basano sulla creazione ed eliminazione rapida
di argomenti o sull'eliminazione e ricreazione rapida di argomenti.

## API REST Kafka
{: #trouble_rest notoc}

*  Solo il formato integrato binario è supportato per le richieste e le risposte. Il formato integrato Avro
                non è supportato.
*  Le richieste simultanee non sono supportate per un'istanza consumatore.
   Le richieste di lettura, commit o
                    eliminazione corrispondenti a un'istanza consumatore devono essere inviate solo dopo
                    che è stata ricevuta una risposta per eventuali richieste in sospeso di tale istanza.

## Limite di frequenza per l'API REST Kafka
{: #kafka_rate notoc}

Le applicazioni che utilizzano l'API REST Kafka possono essere soggette a un limite di
frequenza per ogni ApiKey. Quando si verifica questo limite, l'API
risponde con il seguente errore HTTP:

<code>429 Too Many Requests</code>
{:screen}

Se visualizzi questo errore, attendi e invia nuovamente la richiesta.

## Riavvio giornaliero per l'API REST Kafka
{: #rest_restart notoc}

L'API REST Kafka si riavvia una volta al giorno per un breve periodo di
tempo. Durante questo periodo, l'API REST Kafka potrebbe non essere
disponibile. Se ciò accade, si consiglia di ritentare la
richiesta. Una volta riavviata l'API REST, dovrai ricreare
le tue istanze consumatore Kafka. In questo caso,
l'API REST restituisce il seguente JSON:

```'{"error_code":40403,"message":"Consumer instance not found."}'
```
{:screen}

## API consumatore di alto livello Kafka
{: #kafka_consumer notoc}

Non è possibile utilizzare l'API semplice o consumatore di alto livello Apache Kafka 0.8.2 con {{site.data.keyword.messagehub}}. Utilizza invece la nuova API consumatore Kafka 0.9.
