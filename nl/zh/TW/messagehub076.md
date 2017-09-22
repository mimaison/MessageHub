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

# 為何要使用 {{site.data.keyword.mql}} API？
{: #why_mql}

{{site.data.keyword.mql}} API 提供了比 Kafka API 高的摘要層次。{{site.data.keyword.mql}} 容許以快速而可攜的方式在統一傳訊模型中撰寫應用程式，此模型同時支援佇列和發佈/訂閱傳訊模式。
{:shortdesc}

應用程式使用動態建立的目的地來交換訊息，您可以階層式地建構這些目的地（例如 <code>'/sports/football'</code>）、使用萬用字元（例如 <code>'/sports/#'</code>）將它們分組，以及用簡單的控制處理遞送保證與訊息過期。這讓您能直接明確地實作像是工作者卸載、事件通知及批次處理等情境。

除了使用 {{site.data.keyword.mql}} API 在其他應用程式之間傳送訊息，您也可以與使用 Kafka REST 或 Kafka API 的應用程式交換訊息。或者，您也可以使用內部部署的應用程式，搭配 {{site.data.keyword.IBM}} MQ。

