---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-05"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# 已知限制
{: #restrictions}


## 每个 {{site.data.keyword.Bluemix_notm}} 空间的 {{site.data.keyword.messagehub}} 实例数
{: #instances_space notoc}

每个 {{site.data.keyword.Bluemix_notm}} 空间只能有一个 {{site.data.keyword.messagehub}} 实例。

##主题和分区
{: #topics_partitions notoc}

*  主题名称限制为最多 100 个字符。
*  一个主题的缺省分区数为一个。
*  每个 {{site.data.keyword.Bluemix_notm}} 空间的分区数限制为 100 个。要创建更多的分区，必须使用新的 {{site.data.keyword.Bluemix_notm}} 空间。

## 消息保留时间
{: #message_retention notoc}

缺省情况下，消息在 Kafka 中最多保留 24 小时，并且每个分区的上限是 1 GB。如果达到 1 GB 上限，那么将废弃最旧的消息以防超出限制。

使用用户界面或管理 API 创建主题时，可以更改消息保留时间的限制。时间限制最短为 1 小时，最长为 30 天。

## 在 Kafka 中创建和删除主题
{: #create_delete notoc}

在 Kafka 中，主题的创建和删除是异步操作，可能需要一些时间才能完成。建议避免采用依赖于快速创建和删除主题的使用模式，或依赖于快速删除并重新创建主题的使用模式。

## Kafka REST API
{: #trouble_rest notoc}

*  仅支持二进制嵌入格式的请求和响应。不支持 Avro 嵌入格式。
*  使用者实例不支持并行请求。只有接收到使用者实例的任何待处理请求的响应之后，才可以读取、落实或删除该使用者实例对应的请求。

## Kafka REST API 速率限制
{: #kafka_rate notoc}

使用 Kafka REST API 的应用程序可能会受每个 ApiKey 的速率限制的影响。达到此限制时，API 会使用以下 HTTP 错误进行响应：

<code>429 Too Many Requests</code>
{:screen}

如果看到此错误，请稍后重新提交请求。

## Kafka REST API 每日重新启动
{: #rest_restart notoc}

Kafka REST API 每天重新启动一次，重新启动需要很短的一段时间。在此时间段内，Kafka REST API 可能会变得不可用。如果发生此情况，建议重试请求。重新启动 REST API 后，必须重新创建 Kafka 使用者实例。否则，REST API 会返回以下 JSON：

```'{"error_code":40403,"message":"Consumer instance not found."}'
```
{:screen}

## Kafka 高级别使用者 API
{: #kafka_consumer notoc}

不能将 Apache Kafka 0.8.2 简单或高级别使用者 API 与 {{site.data.keyword.messagehub}} 配合使用。请改为使用新的 Kafka 0.9 使用者 API。
