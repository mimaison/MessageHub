---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 什麼是 MQ Light API，它有什麼不同？
{: #mqlight}

{{site.data.keyword.mql}} API 提供了比 Kafka API 高的傳訊摘要層次，如此可更容易學習，且更容易運用在您的應用程式中。
{:shortdesc}

使用 Kafka 用戶端或是 {{site.data.keyword.mql}} API 之間的選擇，取決於您想要建置的傳訊拓蹼：

* 使用 Kafka，您會使用少量的主題，且可以針對每個主題有多個分割區，獲得額外的可擴充性。您可以使用消費者群組在消費者之間共用訊息，但每個消費者必須能夠跟上指派給他的分割區訊息速率。
* 使用 {{site.data.keyword.mql}} API，您可以使用大量的主題，且主題名稱為階層式（例如：<code>'/sports/football'</code> 及 <code>'/sports/tiddlywinks'</code>）。在消費者之間共用訊息簡單了許多。

{{site.data.keyword.mql}} API 中的主題與 Kafka 主題不同。相反地，{{site.data.keyword.mql}} API 會使用稱為 "MQLight"
的單一 Kafka 主題，使用 {{site.data.keyword.mql}} API 傳送和接收的所有訊息會通過那一個 Kafka 主題。

{{site.data.keyword.mql}} 僅適用於下列 {{site.data.keyword.Bluemix_notm}} 地區：美國南部、英國和雪梨。MQ Light API 無法用於德國地區或「{{site.data.keyword.Bluemix_notm}} 專用」。

<!-- begin PRODUCTION ONLY -->
如需在 API 之間選擇的相關資訊，請參閱[為何要使用 Kafka API？](/docs/services/MessageHub/messagehub054.html)、[為何要使用 MQ Light API？](/docs/services/MessageHub/messagehub076.html)及[為何要使用 Kafka REST API？](/docs/services/MessageHub/messagehub065.html)。
<!-- end PRODUCTION ONLY -->
