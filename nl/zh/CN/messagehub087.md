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

# 在三个 API 中进行选择
{: #choose_api}

{{site.data.keyword.messagehub}} 支持三个 API。下面的一些信息可帮助您选择最适用的 API：

## 为什么要使用 Kafka API？
{: #why_kafka notoc}

有一些原因可能促使您选择使用 Kafka API，而不是 {{site.data.keyword.messagehub}} 提供的其他界面。这些原因包括：
{:shortdesc}


* 可更轻松地将应用程序与支持 Kafka 的现有系统集成，例如 {{site.data.keyword.IBM}} {{site.data.keyword.streaminganalyticsshort}} 和 {{site.data.keyword.sparks}}。
* 与其他 API 相比，等待时间更短，吞吐量更高。
* 与 Kafka REST API 相比，所提供的 API 更为丰富。


## 为什么要使用 {{site.data.keyword.mql}} API？
{: #why_mql notoc}

{{site.data.keyword.mql}} API 提供的抽象级别高于 Kafka API。{{site.data.keyword.mql}} 支持采用统一消息传递模型以可移植方式快速编写应用程序，该模型支持排队和发布/预订消息传递模式。
{:shortdesc}

应用程序使用动态创建的目标来交换消息，对于这些目标，您可以采用分层结构（例如，<code>‘/sports/football’</code>），使用通配符分组（例如 <code>‘/sports/#’</code>），以及使用简单控件来控制传递保证和消息到期。
这样一来，您可以轻松实现多种场景，例如工作程序分流、事件通知和批处理。
除了使用 {{site.data.keyword.mql}} API 在其他应用程序之间发送消息外，还可以与使用 Kafka REST 或 Kafka API 的应用程序交换消息。或者，也可以将内部部署的应用程序用于 {{site.data.keyword.IBM_notm}} MQ。


## 为什么要使用 Kafka REST API？
{: #why_rest notoc}

Kafka REST API 是一个方便的接口，可在以下情况下使用：

* 开发人员想要快速着手使用 {{site.data.keyword.messagehub}}
* 在等待时间不是关键因素的某些吞吐量较低的用例中
* 用于调试和排查故障

Kafka REST API 并不是一个等待时间短的高吞吐量接口。对于这些类型的需求，我们建议使用 Kafka API 与 {{site.data.keyword.messagehub}} 建立连接。有关更多信息，请参阅[使用 Kafka 客户机](/docs/services/MessageHub/messagehub050.html#kafka_client)。












