---

copyright:
  years: 2015, 2017
lastupdated: "2017-02-08"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Differenze tra Message Hub negli ambienti {{site.data.keyword.Bluemix_notm}} pubblico e dedicato
{: #public_dedicated}

{{site.data.keyword.Bluemix}} è una piattaforma
basata su cloud open standard per la creazione, esecuzione e gestione delle applicazioni. {{site.data.keyword.Bluemix_notm}} fornisce dei modelli di distribuzione
pubblici e dedicati. {{site.data.keyword.messagehub}} è disponibile in entrambi
gli ambienti.

## Ambiente {{site.data.keyword.Bluemix_notm}} pubblico
{: notoc}

{{site.data.keyword.Bluemix_notm}} pubblico fornisce un conveniente servizio
cloud pubblico in cui paghi per quello che usi e condividi l'infrastruttura con
gli altri.

In {{site.data.keyword.Bluemix_notm}} pubblico, il costo di
{{site.data.keyword.messagehub}} è determinato da due fattori: il
numero di partizioni che utilizzi e il numero di messaggi che invii e ricevi. Non viene applicato
alcun addebito per i dati dei messaggi conservati negli argomenti, ma i dati conservati in ogni partizione sono
limitati a 1 GB.

Per ulteriori informazioni, vedi [{{site.data.keyword.Bluemix_notm}} pubblico ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud-computing/bluemix/public){:new_window}.


## Ambiente {{site.data.keyword.Bluemix_notm}} dedicato
{: notoc}

{{site.data.keyword.Bluemix_notm}} dedicato fornisce un ambiente più
isolato in cui la tua infrastruttura non viene condivisa ed è ospitata in un account SoftLayer
separato gestito da {{site.data.keyword.IBM_notm}}. Questo ambiente è connesso in modo protetto a {{site.data.keyword.Bluemix_notm}} pubblico e alla tua rete.

In un'istanza dedicata di {{site.data.keyword.messagehub}}, paghi per il
servizio e non per la quantità di utilizzo. Puoi avere fino a 75 partizioni nell'intero
ambiente, incluso tutte le organizzazioni e tutti gli spazi. Ogni partizione è limitata a 10 GB per
garantire che il cluster non esaurisca lo spazio.

{{site.data.keyword.messagehub}} in dedicato può essere distribuito solo con {{site.data.keyword.Bluemix_notm}} dedicato, ma può essere resa disponibile una versione diffusa del nostro servizio pubblico se stai utilizzando altri ambienti dedicati.
I dashboard Kibana e Grafana per il monitoraggio del servizio non sono supportati in {{site.data.keyword.Bluemix_notm}} dedicato.

Per ulteriori informazioni, vedi [{{site.data.keyword.Bluemix_notm}} dedicato ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/cloud-computing/bluemix/dedicated/){:new_window}.


