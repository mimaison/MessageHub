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

# Utilisation de l'API {{site.data.keyword.mql}} dans {{site.data.keyword.messagehub}}
{: #mql_how}


Pour utiliser l'API, ajoutez une référence à l'API du client {{site.data.keyword.mql}} la plus récente correspondant au langage choisi comme suit : 


## Java
{: #mql_java_how notoc}

Ajoutez la référence suivante dans le fichier <code>Maven pom</code> : 

```
<dependency>
    <groupId>com.ibm.mqlight</groupId>
    <artifactId>mqlight-api</artifactId>
    <version>LATEST</version>
</dependency>
```
{:codeblock}



## Node.js
{: #mql_node_how notoc}

Ajoutez la référence suivante dans la section dependency du fichier <code>package.json</code> :

<pre class="pre"><code>"mqlight" : "1.0.x"</code></pre>
{: codeblock}

Ajoutez l'instruction require suivante à votre fichier source : 

<pre class="pre"><code>var mqlight = require(‘mqlight’);</code></pre>
{: codeblock}


## Ruby
{: #mql_ruby_how notoc}

Ajoutez la référence suivante au fichier <code>Gemfile</code> :

```
gem 'mqlight', '~> 1.0'
```
{: codeblock}

<br>
Ajoutez l'instruction require suivante à votre fichier source :

```
require ‘mqlight’
```
{: codeblock}



## Python
{: #mql_python_how notoc}

Ajoutez la référence suivante dans le fichier <code>requirements.txt</code> :
 

```
git+git://github.com/mqlight/python-mqlight.git@readthedocs
```
{:codeblock}

<br>
Puis, ajoutez l'instruction import suivante dans le fichier source :

```
import mqlight
```
{:codeblock}


