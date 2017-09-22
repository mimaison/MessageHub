---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.messagehub}} 常見問題 (FAQ)
{: #faqs}

{{site.data.keyword.IBM}} {{site.data.keyword.messagehub}} 服務常見問題的回答。

## Kafka offsets.retention.minutes 的預設值為何？
{: #offsets notoc}
預設值是 7 天。 

偏移保留屬於系統層面，因此您不能在個別主題層次設定。所有消費者群組只會得到 7 天的儲存偏移，即使它們的主題已增加到最長 30 天的日誌保留。 

## {{site.data.keyword.messagehub}} 的可用性行為為何？
{: #availability notoc}

如果您撰寫 {{site.data.keyword.messagehub}} 應用程式，請使用此資訊來瞭解正常的 {{site.data.keyword.messagehub}} 可用性行為為何，以及預期您的應用程式要處理的內容。

### API
{: #api_availability notoc}

在 {{site.data.keyword.messagehub}} 的日常作業中，Kafka 叢集的節點有時會重新啟動。在某些情況下，您的應用程式會知道，因為叢集會重新指派資源。請將您的應用程式撰寫成對於這些變更具復原力，且能夠重新連接並重試作業。

### {{site.data.keyword.messagehub}} 橋接器
{: #bridge_availability notoc}

請將您的應用程式撰寫成可以處理橋接器會偶爾重新啟動的可能性。
