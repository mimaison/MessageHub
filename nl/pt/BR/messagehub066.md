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

# Como conectar e autenticar
{: #rest_connect}

Para conectar-se ao {{site.data.keyword.messagehub}}, a API de REST do Kafka usa as
credenciais <code>api_key</code> e <code>kafka_rest_url</code> da
[variável de ambiente VCAP_SERVICES](/docs/services/MessageHub/messagehub071.html).

Para autenticar com a API REST do {{site.data.keyword.messagehub}} Kafka, você
                deve especificar o <code>api_key</code> no cabeçalho X-Auth-Token de suas
                solicitações.
