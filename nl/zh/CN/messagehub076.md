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

# 为什么要使用 {{site.data.keyword.mql}} API？
{: #why_mql}

{{site.data.keyword.mql}} API 提供的抽象级别高于 Kafka API。{{site.data.keyword.mql}} 支持采用统一消息传递模型以可移植方式快速编写应用程序，该模型支持排队和发布/预订消息传递模式。
{:shortdesc}

应用程序使用动态创建的目标来交换消息，对于这些目标，您可以采用分层结构（例如，<code>‘/sports/football’</code>），使用通配符分组（例如 <code>‘/sports/#’</code>），以及使用简单控件来控制传递保证和消息到期。
这样一来，您可以轻松实现多种场景，例如工作程序分流、事件通知和批处理。
除了使用 {{site.data.keyword.mql}} API 在其他应用程序之间发送消息外，还可以与使用 Kafka REST 或 Kafka API 的应用程序交换消息。或者，也可以将内部部署的应用程序用于 {{site.data.keyword.IBM}} MQ。

