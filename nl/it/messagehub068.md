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


#Sicurezza e riservatezza dei dati
{: #data_security}


{{site.data.keyword.IBM}} utilizza i seguenti metodi per aiutare a garantire la sicurezza e la
riservatezza dei tuoi dati:
{:shortdesc}

## Protocolli crittografici
{: #cryptographic notoc}


*  Le connessioni alle interfacce REST e native Kafka devono essere effettuate utilizzando TLS 1.2.
*  Le connessioni sono limitate alle seguenti suite di cifratura complesse:

      * ECDHE-RSA-AES128-GCM-SHA256
      * ECDHE-RSA-AES256-GCM-SHA384
      * DHE-RSA-AES128-GCM-SHA256
      * kEDH+AESGCM
      * ECDHE-RSA-AES128-SHA256
      * ECDHE-RSA-AES256-SHA384
      * DHE-RSA-AES128-SHA256
      * DHE-RSA-AES256-SHA256



*  Per accedere al dashboard
                        {{site.data.keyword.messagehub}},
                    devi utilizzare un browser che supporta TLS 1.2.
   
## Crittografia dei payload di messaggio
{: #encryption_payloads notoc}

I dati dei messaggi vengono crittografati per la trasmissione tra {{site.data.keyword.messagehub}} e i client per effetto di TLS. {{site.data.keyword.messagehub}} memorizza i dati dei messaggi inattivi
e i log dei messaggi su dischi crittografati.



