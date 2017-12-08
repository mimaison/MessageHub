---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.messagehub}} 常見問題 (FAQ)
{: #faqs}

{{site.data.keyword.IBM}} {{site.data.keyword.messagehub}} 服務常見問題的回答。

<!--17/10/17 - Karen: same info duplicated at messagehub104 -->
## 如何使用 Kafka API 建立及刪除主題？
{: #topic_admin notoc}

如果您使用 Kafka 用戶端 0.11 或更新版本，或 Kafka Streams 0.10.2.0 或更新版本，可以使用 API 來建立及刪除主題。我們已對您建立主題時接受的設定做了一些限制。目前，您只能修改下列設定：

<dl>
<dt>cleanup.policy</dt>
<dd>設為 <code>delete</code>（預設值）、<code>compact</code> 或 <code>delete,compact</code></dd>
<dt>retention.ms</dt>
<dd>預設保留期間是 24 小時。最短 1 小時，最長 30 天。請以小時的倍數來指定此值。

<p>**附註：**如果清理原則是僅 <code>compact</code>，我們會自動新增 <code>delete</code> 但停用根據時間刪除。主題中的訊息在刪除之前最多可壓縮到 1 GB。</p>
</dd>
</dl>

## {{site.data.keyword.messagehub}} 為消費者偏移主題所設定的日誌保留時間範圍有多長？
{: #offsets notoc}
{{site.data.keyword.messagehub}} 會保留消費者偏移 7 天。這對應於 Kafka 配置 offsets.retention.minutes。 

偏移保留屬於系統層面，因此您不能在個別主題層次設定。所有消費者群組只會得到 7 天的儲存偏移，即使是使用已增加到最長 30 天日誌保留的主題。 

## {{site.data.keyword.messagehub}} 的可用性行為為何？
{: #availability notoc}

如果您撰寫 {{site.data.keyword.messagehub}} 應用程式，請使用此資訊來瞭解正常的 {{site.data.keyword.messagehub}} 可用性行為為何，以及預期您的應用程式要處理的內容。

### API
{: #api_availability notoc}

在 {{site.data.keyword.messagehub}} 的日常作業中，Kafka 叢集的節點有時會重新啟動。在某些情況下，您的應用程式會知道，因為叢集會重新指派資源。請將您的應用程式撰寫成對於這些變更具復原力，且能夠重新連接並重試作業。

### {{site.data.keyword.messagehub}} 橋接器
{: #bridge_availability notoc}

請將您的應用程式撰寫成可以處理橋接器會偶爾重新啟動的可能性。
