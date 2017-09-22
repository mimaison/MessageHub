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

# Che cos'è l'API MQ Light e in che cosa è differente?
{: #mqlight}

L'API {{site.data.keyword.mql}} fornisce un livello di astrazione
superiore per la messaggistica rispetto a Kafka, il che la rende più semplice da comprendere e da utilizzare
nelle tue applicazioni.
{:shortdesc}

La scelta tra l'utilizzo di un client Kafka o dell'API {{site.data.keyword.mql}} dipende dalla topologia di messaggistica che vuoi
creare:

* Con Kafka, utilizzi un numero ridotto di argomenti e puoi avere più partizioni per ogni argomento per una maggiore scalabilità. Puoi condividere i messaggi tra i consumatori utilizzando gruppi di consumatori, ma ogni consumatore deve essere in grado di mantenere il passo con la frequenza dei messaggi per le partizioni assegnate.
* Con l'API {{site.data.keyword.mql}}, puoi utilizzare un numero molto maggiore di argomenti e i nomi degli argomenti sono gerarchici (ad esempio: <code>‘/sports/football’</code> e <code>‘/sports/tiddlywinks’</code>). La condivisione dei messaggi tra i consumatori è molto più semplice. 

Gli argomenti nell'API {{site.data.keyword.mql}} non sono gli stessi
argomenti presenti in Kafka. Al contrario, l'API {{site.data.keyword.mql}} utilizza
un singolo argomento Kafka chiamato "MQLight" e tutti i messaggi inviati e ricevuti utilizzando l'API {{site.data.keyword.mql}} passano attraverso quel solo argomento Kafka.

{{site.data.keyword.mql}} è disponibile solo nelle seguenti regioni
{{site.data.keyword.Bluemix_notm}}: Stati Uniti Sud, Regno Unito e Sydney. L'API MQ Light non è disponibile nella regione Germania o in
{{site.data.keyword.Bluemix_notm}} dedicato.

<!-- begin PRODUCTION ONLY -->
Per ulteriori informazioni sulla scelta tra le API, vedi [Perché utilizzare l'API Kafka?](/docs/services/MessageHub/messagehub054.html), [Perché utilizzare l'API MQ Light?](/docs/services/MessageHub/messagehub076.html) e [Perché utilizzare l'API REST Kafka?](/docs/services/MessageHub/messagehub065.html).
<!-- end PRODUCTION ONLY -->
