---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-11"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Come effettuare la connessione e l'autenticazione
{: #kafka_connect}


Per stabilire una connessione a {{site.data.keyword.messagehub}},
l'API Kafka utilizza le credenziali  
```kafka_brokers_sasl
``` 
e
```
l'utente
```
e la

 ```password
```
 dalla
[variabile di ambiente VCAP_SERVICES](/docs/services/MessageHub/messagehub071.html).

## Connessione e autenticazione in un'applicazione diversa da Java
{: #kafka_notjava notoc}

Attualmente, il servizio {{site.data.keyword.messagehub}}
autentica i client utilizzando SASL PLAIN. Le credenziali vengono riportate tramite una connessione crittografata.
Questa è una nuova funzione aggiunta in Kafka 0.10.0.X. Qualsiasi client che supporti Kafka 0.10 con SASL PLAIN
dovrebbe funzionare con {{site.data.keyword.messagehub}}. I client di esempio sono i seguenti:

* [librdkafka ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/edenhill/librdkafka/){:new_window}
* [confluent-kafka-python ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/confluentinc/confluent-kafka-python){:new_window}

Se utilizzi il client Kafka 0.9.0.0 precedente, devi usare un modulo di login personalizzato che puoi
scaricare da [modulo di login {{site.data.keyword.messagehub}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/ibm-messaging/message-hub-samples/blob/master/kafka-0.9/message-hub-login-library/messagehub.login-1.0.0.jar){:new_window}.

