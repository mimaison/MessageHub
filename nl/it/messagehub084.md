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

# Come eseguire la migrazione del client Kafka da 0.9.x a 0.10.x
{: #kafka_migrate}


Se utilizzi i client Java, adesso puoi usare
i client Kafka 0.10.x disponibili pubblicamente. Si consiglia vivamente di passare dalla versione 0.9.x alla
versione più recente 0.10.x (attualmente 0.10.2.1). Completa la seguente procedura:

1. Elimina il modulo jar di login {{site.data.keyword.messagehub}}.
2. Modifica il tuo file <code>jaas.conf</code> nel seguente modo:
    ```
        KafkaClient {
          org.apache.kafka.common.security.plain.PlainLoginModule required
          serviceName="kafka"
            username="<il tuo nome utente>"
            password="<la tua password>";
        };
    ```
    {: codeblock}

3. Aggiungi questa riga alle proprietà di consumatore e produttore: <code>sasl.mechanism=PLAIN</code>


