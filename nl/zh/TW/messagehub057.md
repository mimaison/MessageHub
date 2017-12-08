---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-05"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# 已知限制
{: #restrictions}


##主題及分割區
{: #topics_partitions notoc}

*  主題名稱限制最多為 100 個字元。
*  一個主題的預設分割區數目是一 (1)。
*  每個 {{site.data.keyword.Bluemix_notm}} 空間有 100 個分割區的限制。若要建立更多分割區，您必須使用新的 {{site.data.keyword.Bluemix_notm}} 空間。

## 訊息保留
{: #message_retention}

依預設，訊息在 Kafka 中的保留時間為最長 24 小時，每個分割區的上限為 1 GB。如果到達 1 GB 的限制，將會捨棄最舊的訊息，以維持在限制之內。

當您以使用者介面或管理 API 建立主題時，可以變更訊息保留的時間限制。時間限制為最短一小時，最長 30 天。

## 在 Kafka 中建立及刪除主題
{: #create_delete notoc}

在 Kafka 中，主題建立及刪除是非同步作業，可能需要一些時間才能完成。建議您避免使用依賴快速建立及刪除主題的模式，或是使用依賴快速刪除並重建主題的模式。

## Kafka REST API
{: #trouble_rest notoc}

*  要求及回應只支援二進位內嵌格式。不支援 Avro 及 JSON 內嵌格式。
*  消費者實例不支援並行要求。對應於消費者實例的讀取、確定或刪除要求，應該只能在收到該實例之任何未完成要求的回應之後傳送。

## Kafka REST API 速率限制
{: #kafka_rate notoc}

使用 Kafka REST API 的應用程式，可能受限於每個 ApiKey 的速率限制。發生此限制時，API 會回應下列 HTTP 錯誤：

<code>429 要求太多</code>
{:screen}

如果您看到此錯誤，請稍候，然後重新提交要求。

## Kafka REST API 每日重新啟動
{: #rest_restart notoc}

Kafka REST API 每天會重新啟動一次，需要一小段時間。在此期間內，Kafka REST API 可能變成無法使用。如果發生這種情況，建議您重試要求。REST API 重新啟動之後，您需要重建 Kafka 消費者實例。如果是這種情況，REST API 會傳回下列 JSON：

```'{"error_code":40403,"message":"Consumer instance not found."}'
```
{:screen}

## Kafka 高階消費者 API
{: #kafka_consumer notoc}

您無法使用 Apache Kafka 0.8.2 簡單或高階消費者 API 與 {{site.data.keyword.messagehub}} 搭配。相反地，您可以使用最早版本的受支援 Kafka 消費者 API，也就是 0.9。
 
