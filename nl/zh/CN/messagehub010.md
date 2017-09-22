---

copyright:
  years: 2015, 2017
lastupdated: "2017-02-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 关于 Message Hub
{: #about}

{{site.data.keyword.messagehub_full}} 是一种可扩展、分布式、高吞吐量的消息传递服务，支持应用程序和服务轻松、可靠地进行通信。
{:shortdesc}

在 {{site.data.keyword.messagehub}} 中，应用程序通过创建消息并将其发送到主题来发送数据。要接收消息，应用程序可预订主题，并选择是接收该主题的所有消息还是在应用程序之间共享消息。
{{site.data.keyword.messagehub}} 按有序的顺序托管和维护消息。与传统消息传递系统相比，{{site.data.keyword.messagehub}} 提供的是主题，而不是队列。但是，{{site.data.keyword.messagehub}} 提供了多种方式在接收应用程序之间共享消息，因此行为上与队列类似。

可以使用 {{site.data.keyword.messagehub}} 来完成以下任务：

* 将微服务连线在一起。
* 将工作分流到后端工作程序进程。
* 将流数据连接到分析以获得深刻的见解。
* 将事件数据发布到多个应用程序以实时作出反应。
* 将数据传输到其他服务中。例如，传输到长期存储器。
