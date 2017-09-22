---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-27"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.messagehub}} 是什麼？

{{site.data.keyword.messagehub}} 使用主題來實作發佈/訂閱傳訊。不像其他傳訊系統，{{site.data.keyword.messagehub}} 提供主題，但不提供佇列。{{site.data.keyword.messagehub}} 也將其他功能，例如
{{site.data.keyword.mql}} API 及橋接器，提供給其他系統。

{{site.data.keyword.messagehub}} 有三個 API：Kafka API、{{site.data.keyword.mql}} API 及
Kafka REST API。如需使用 API 建立傳訊應用程式的相關資訊，請參閱[使用 Kafka 用戶端](/docs/services/MessageHub/messagehub050.html)、[使用 MQ Light API 用戶端](/docs/services/MessageHub/messagehub075.html)及[使用 Kafka REST API](/docs/services/MessageHub/messagehub025.html)。

{{site.data.keyword.messagehub}} 也支援對於其他精選系統的橋接器。橋接器是通往另一個系統的單向鏈結。橋接器可以從另一個系統取得訊息然後發佈到主題，或是從主題取用訊息然後傳送到另一個系統。如此，您可以使用
{{site.data.keyword.messagehub}} 和其他系統整合，而不需撰寫程式碼。如需相關資訊，請參閱[使用橋接器鏈結至其他服務](/docs/services/MessageHub/messagehub088.html)。

{{site.data.keyword.messagehub}} 是以開放程式碼的 Apache Kafka 專案為基礎，這是一個高度可擴充、高效能的傳訊骨幹，在許多正式作業環境已經過證實。如需相關資訊，請參閱 [{{site.data.keyword.messagehub}} 和 Apache Kafka](/docs/services/MessageHub/messagehub073.html)。
