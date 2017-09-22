---

copyright:
  years: 2015, 2017
lastupdated: "2017-01-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 在三個 API 之間抉擇
{: #choose_api}

{{site.data.keyword.messagehub}} 支援三個 API。下列資訊可協助您選擇最合適的一個：

## 為何要使用 Kafka API？
{: #why_kafka notoc}

有一些理由，讓您可能選擇使用 Kafka API，而不使用 {{site.data.keyword.messagehub}} 提供的其他介面。這些理由包括：
{:shortdesc}


* 可以更輕鬆地整合應用程式與具有 Kafka 支援的現有系統，例如 {{site.data.keyword.IBM}} {{site.data.keyword.streaminganalyticsshort}} 及 {{site.data.keyword.sparks}}。
* 它提供比其他 API 低的延遲時間，以及更高的傳輸量。
* 它提供比 Kafka REST API 豐富的 API。


## 為何要使用 {{site.data.keyword.mql}} API？
{: #why_mql notoc}

{{site.data.keyword.mql}} API 提供了比 Kafka API 高的摘要層次。{{site.data.keyword.mql}} 容許以快速而可攜的方式在統一傳訊模型中撰寫應用程式，此模型同時支援佇列和發佈/訂閱傳訊模式。
{:shortdesc}

應用程式使用動態建立的目的地來交換訊息，您可以階層式地建構這些目的地（例如 <code>'/sports/football'</code>）、使用萬用字元（例如 <code>'/sports/#'</code>）將它們分組，以及用簡單的控制處理遞送保證與訊息過期。這讓您能直接明確地實作像是工作者卸載、事件通知及批次處理等情境。

除了使用 {{site.data.keyword.mql}} API 在其他應用程式之間傳送訊息，您也可以與使用 Kafka REST 或 Kafka API 的應用程式交換訊息。或者，您也可以使用內部部署的應用程式，搭配 {{site.data.keyword.IBM_notm}} MQ。


## 為何要使用 Kafka REST API？
{: #why_rest notoc}

Kafka REST API 是可用於下列狀況的便利介面：

* 開發人員想要使用 {{site.data.keyword.messagehub}} 快速開始進行時
* 在延遲時間不是重要因素的特定低傳輸量使用案例中。
* 對於除錯及錯誤搜尋

Kafka REST API 不能當作高傳輸量、低延遲時間的介面。對於這些類型的需求，建議您使用 Kafka API 與 {{site.data.keyword.messagehub}} 相互連接。如需相關資訊，請參閱[使用 Kafka 用戶端](/docs/services/MessageHub/messagehub050.html#kafka_client)。












