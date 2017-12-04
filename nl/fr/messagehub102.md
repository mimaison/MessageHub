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

# Utilisation du client Node.js MQ Light 
{: #mql_node}


Pour utiliser l'API, ajoutez une référence à l'API du client {{site.data.keyword.mql}} pour Node.js la plus récente comme suit :

Ajoutez la référence suivante dans la section dependency du fichier <code>package.json</code> :

<pre class="pre"><code>"mqlight" : "1.0.x"</code></pre>
{: codeblock}

Ajoutez l'instruction require suivante à votre fichier source :

<pre class="pre"><code>var mqlight = require(‘mqlight’);</code></pre>
{: codeblock}

<!-- Comment from Andrew
Instructions for getting started, with links for more info
Simple send source and receive source in-line

-->


