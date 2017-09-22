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

# Utilizzo del client Node.js MQ Light 
{: #mql_node}


Per utilizzare l'API, aggiungi un riferimento all'ultima API client {{site.data.keyword.mql}} disponibile per Node.js nel seguente modo:

Aggiungi il seguente riferimento alla sezione delle dipendenze del tuo file <code>package.json</code>:

<pre class="pre"><code>"mqlight" : "1.0.x"</code></pre>
{: codeblock}

E aggiungi la seguente istruzione require al tuo file di
origine:

<pre class="pre"><code>var mqlight = require(‘mqlight’);</code></pre>
{: codeblock}

<!-- Comment from Andrew
Instructions for getting started, with links for more info
Simple send source and receive source in-line

-->


