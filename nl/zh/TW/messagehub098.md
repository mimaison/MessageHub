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

# 使用 MQ Light API 搭配 Message Hub 需要些什麼嗎？
{: #mql_reqs}

使用 {{site.data.keyword.mql}} API 搭配 {{site.data.keyword.messagehub}} 時有下列需求： 

**您必須明確地建立名為 "MQLight" 的 Kafka 主題，然後才能使用 API，因為所有訊息都會通過 "MQLight" 主題。這個主題必須具有單一分割區。建立這個主題會為您的服務實例啟用 MQ Light API**如需如何在 {{site.data.keyword.messagehub}} 建立主題的相關資訊，請參閱[管理主題](/docs/services/MessageHub/messagehub070.html)。

MQ Light API 使用 "MQLight" 主題來儲存其訊息資料，以及與其他 Kafka 用戶端互動。注意，建立這個主題之後，它會依服務付款方案中所概述的標準費率產生費用。

若要停用 MQ Light API，請刪除 "MQLight" 主題。請注意，刪除主題時會破壞所有資料。
