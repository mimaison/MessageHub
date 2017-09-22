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

# Usando o cliente Ruby do MQ Light
{: #mql_how}


Para usar a API, inclua uma referência à API do cliente {{site.data.keyword.mql}} mais recente
disponível para Ruby como segue:

Inclua a referência a seguir no <code>Gemfile</code>:

```
gem 'mqlight', '~> 1.0'
```
{: codeblock}

E inclua a instrução de solicitação a seguir em seu arquivo de origem:

```
require ‘mqlight’
```
{: codeblock}

<!-- Comment from Andrew
Instructions for getting started, with links for more info
Simple send source and receive source in-line

-->


