---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-26"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 關於 Message Hub
{: #about}

{{site.data.keyword.messagehub_full}} 是一個可擴充的分散式高傳輸量傳訊服務，它讓應用程式及服務能輕鬆而可靠地進行通訊。
{:shortdesc}

在 {{site.data.keyword.messagehub}} 中，應用程式會藉由建立訊息並傳送給主題來傳送資料。為了接收訊息，應用程式會訂閱主題，並選擇接收主題的所有訊息或在它們之間共用訊息。{{site.data.keyword.messagehub}} 會以有序的序列來管理及維護訊息。相對於傳統傳訊系統，{{site.data.keyword.messagehub}} 提供主題，但不提供佇列。不過，{{site.data.keyword.messagehub}} 提供了方法在接收端應用程式之間共用訊息，這樣結果會有類似於佇列的行為。

您可以使用 {{site.data.keyword.messagehub}} 來完成下列作業：

* 將工作卸載至後端工作者處理程序。
* 連接串流資料與分析，以實現強大的見解。
* 將事件資料提發佈多個應用程式，以便即時回應。
* 將資料傳送到另一個服務。例如，傳送到長期儲存空間。
