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

# 如何連接及鑑別
{: #rest_connect}

為了連接至 {{site.data.keyword.messagehub}}，Kafka REST API 會使用來自 [VCAP_SERVICES 環境變數](/docs/services/MessageHub/messagehub071.html)的 <code>api_key</code> 及 <code>kafka_rest_url</code> 認證。

若要向 {{site.data.keyword.messagehub}} Kafka REST API 進行鑑別，您必須在要求的 X-Auth-Token 標頭中指定 <code>api_key</code>。
