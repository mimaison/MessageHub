---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.messagehub}} - Domande frequenti
{: #faqs}

Risposte alle domande più frequenti sul servizio {{site.data.keyword.IBM}} {{site.data.keyword.messagehub}}.

## Qual è il valore predefinito per offsets.retention.minutes di Kafka?
{: #offsets notoc}
Il valore predefinito è 7 giorni. 

La conservazione di offset avviene a livello di sistema, pertanto non puoi impostarla a livello di un singolo argomento. Tutti i gruppi di consumatori ottengono solo 7 giorni di offset memorizzati anche se il loro argomento è stato aumentato fino al massimo 30 giorni di conservazione dei log. 

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
