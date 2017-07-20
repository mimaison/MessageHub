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

# How to use the {{site.data.keyword.mql}} API in {{site.data.keyword.messagehub}}
{: #mql_how}


To use the API, add a reference to the latest available {{site.data.keyword.mql}} client API for your chosen language as follows:


## Java
{: #mql_java_how notoc}

Add the following reference to your ```Maven pom``` file:

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

Add the following reference to the dependency section of your ```package.json``` file:

<pre class="pre"><code>"mqlight" : "1.0.x"</code></pre>
{: codeblock}

And add the following require statement to your source
file:

<pre class="pre"><code>var mqlight = require(‘mqlight’);</code></pre>
{: codeblock}


## For Ruby
{: #mql_ruby_how notoc}

Add the following reference to the ```Gemfile```:

```
gem 'mqlight', '~> 1.0'
```
{: codeblock}

And add the following require statement to your source file:

```
require ‘mqlight’
```
{: codeblock}



## For Python
{: #mql_python_how notoc}

Add the following reference to your ```requirements.txt```
file:

```
git+git://github.com/mqlight/python-mqlight.git@readthedocs
```
{:codeblock}

<br>
And add the following import statement to your source file:

```
import mqlight
```
{:codeblock}


