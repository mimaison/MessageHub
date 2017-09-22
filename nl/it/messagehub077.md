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

# Abilitazione dell'API {{site.data.keyword.mql}} in {{site.data.keyword.messagehub}}
{: #mql_enable}


**Prima di poter utilizzare l'API, devi creare in modo esplicito un argomento Kafka denominato "MQLight" in quanto tutti i messaggi passano attraverso l'argomento "MQLight". Questo argomento deve avere una singola partizione. La creazione di questo argomento abilita l'API MQ Light per la tua istanza del servizio. **  Per ulteriori informazioni su come creare gli argomenti in {{site.data.keyword.messagehub}}, vedi [Gestione degli argomenti](/docs/services/MessageHub/messagehub070.html).

L'argomento "MQLight" è utilizzato dall'API MQ Light per memorizzare i dati di messaggi e per interagire con altri client Kafka. Tieni presente che quando si crea
questo argomento, vengono applicati dei costi alla tariffa standard descritta nel piano di pagamento dei servizi.

Per disabilitare l'API MQ Light, elimina l'argomento "MQLight". Ricorda che all'eliminazione dell'argomento vengono eliminati tutti i dati.
