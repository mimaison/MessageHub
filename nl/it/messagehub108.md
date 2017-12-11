---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.messagehub}} - Domande frequenti
{: #faqs}

Risposte alle domande più frequenti sul servizio {{site.data.keyword.IBM}} {{site.data.keyword.messagehub}}.

<!--17/10/17 - Karen: same info duplicated at messagehub104 -->
## Come posso utilizzare le API Kafka per creare ed eliminare gli argomenti?
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

## Per quanto tempo {{site.data.keyword.messagehub}} imposta la finestra di conservazione del log per l'argomento degli offset del consumatore?
{: #offsets notoc}
{{site.data.keyword.messagehub}} conserva gli offset del consumatore per 7 giorni. Questo corrisponde alla configurazione Kafka offsets.retention.minutes. 

a conservazione di offset avviene a livello di sistema, pertanto non puoi impostarla a livello di un singolo argomento. Tutti i gruppi di consumatori ottengono solo 7 giorni di offset memorizzati anche se utilizzano un argomento con una conservazione del log che è stata aumentata fino al massimo di 30 giorni.  

## Che cos'è il comportamento di disponibilità di {{site.data.keyword.messagehub}}?
{: #availability notoc}

Se scrivi applicazioni {{site.data.keyword.messagehub}}, utilizza queste informazioni per comprendere quale sia il normale comportamento di disponibilità di {{site.data.keyword.messagehub}} e cosa deve essere gestito dalle tue applicazioni.

### API
{: #api_availability notoc}

Come parte del normale funzionamento di {{site.data.keyword.messagehub}}, i nodi dei cluster Kafka vengono riavviati occasionalmente.
In alcuni casi, le tue applicazioni riconosceranno quando il cluster riassegna risorse. Scrivi le tue applicazioni in modo che siano resilienti
a queste modifiche e che possano riconnettersi e ritentare le operazioni.

### Bridge {{site.data.keyword.messagehub}}
{: #bridge_availability notoc}

Scrivi le tue applicazioni per gestire la possibilità che i bridge possano riavviarsi di volta in volta.
