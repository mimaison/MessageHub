---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-03"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Utilizzo del client Java Kafka
{: #kafka_using}

## Come utilizzare, scaricare ed eseguire l'esempio di API Kafka Java
{: notoc}

L'esempio di API Kafka Java&trade; consiste in un produttore e consumatore di esempio scritto in Java, che utilizza direttamente l'API Kafka. Puoi eseguire questo esempio in locale o in {{site.data.keyword.Bluemix_short}}.

Il codice di esempio si trova nel [progetto GitHub message-hub-samples ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}. Anche se l'esempio utilizza l'API Kafka per inviare e ricevere messaggi, l'esempio utilizza l'API di amministrazione {{site.data.keyword.messagehub}} per creare l'argomento a cui invia i messaggi e da cui riceve i messaggi.

Per ulteriori informazioni sulla configurazione e sull'esecuzione dell'esempio, vedi il file [README.md ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}.

Per una procedura dettagliata su come eseguire l'esempio, vedi [Introduzione a {{site.data.keyword.messagehub}}](/docs/services/MessageHub/index.html#getting_started_steps).

## Come utilizzare, scaricare ed eseguire l'esempio di Liberty for Java
{: #liberty_sample notoc}

L'esempio di Liberty for Java implementa una semplice applicazione distribuita sul runtime Liberty. L'applicazione utilizza l'API Kafka per {{site.data.keyword.messagehub}} per produrre e consumare messaggi.
L'applicazione offre anche un frontend web che puoi utilizzare per le attività di amministrazione.

Puoi trovare il codice di esempio nel [progetto GitHub message-hub-samples ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-liberty-sample){:new_window}.

## Come eseguire la migrazione del client Kafka da 0.9.x a 0.10.x
{: #kafka_migrate notoc}


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

<!--
17/10/17 - Karen: following info duplicated at messagehub063 
-->

## Utilizzo della proprietà sasl.jaas.config
{: #sasl_prop notoc}
Se utilizzi un client Kafka alla versione 0.10.2.1 o successiva, per la configurazione del client puoi usare la proprietà <code>sasl.jaas.config</code> anziché un file JAAS. Per stabilire una connessione a {{site.data.keyword.messagehub}}, imposta <code>sasl.jaas.config</code> come segue:
<pre>
<code>    sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required \
    username="USERNAME" \
    password="PASSWORD";</code>
</pre>
{:codeblock}

dove USERNAME e PASSWORD sono i valori indicati nella scheda **Credenziali del servizio** {{site.data.keyword.messagehub}} in {{site.data.keyword.Bluemix_notm}}.

Se utilizzi <code>sasl.jaas.config</code>, i client in esecuzione nella stessa JVM possono utilizzare credenziali diverse. Per ulteriori informazioni, vedi
[Configurazione dei client Kafka ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://kafka.apache.org/documentation/#security_sasl_plain_clientconfig){:new_window}

Per un precedente client Kafka, devi utilizzare un file di configurazione JAAS per specificare le credenziali. Questo meccanismo è meno conveniente quindi ti raccomandiamo invece di utilizzare la proprietà <code>sasl.jaas.config</code>.

<!-- 
17/10/17 - Karen: following info duplicated at messagehub108
 -->

## API per l'amministrazione degli argomenti
{: #topic_admin notoc}

Se utilizzi un client Kafka alla versione 0.11 o successiva, oppure Kafka Streams alla versione 0.10.2.0 o successiva, puoi utilizzare le API per creare ed eliminare gli argomenti. Abbiamo posto alcune restrizioni sulle impostazioni consentite quando crei gli argomenti. Attualmente, puoi modificare solo le seguenti impostazioni:

<dl>
<dt>cleanup.policy</dt>
<dd>Imposta su <code>delete</code> (predefinito), <code>compact</code> o <code>delete,compact</code></dd>
<dt>retention.ms</dt>
<dd>Il periodo di conservazione predefinito è 24 ore. Il minimo è 1 ora e il massimo è
30 giorni. Specifica questo valore come multipli di ore.

<p>**Nota:**
se la politica di cleanup è solo <code>compact</code>, aggiungiamo automaticamente <code>delete</code> ma disabilitiamo l'eliminazione in base al tempo. I messaggi nell'argomento vengono compattati fino a 1 GB prima di essere eliminati.</p>
</dd>
</dl>

<!--
new topic that includes content from existing topics about samples and migration
-->
