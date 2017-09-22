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

# {{site.data.keyword.messagehub}} 常见问题解答
{: #faqs}

对有关 {{site.data.keyword.IBM}} {{site.data.keyword.messagehub}} 服务的常见问题的解答。

## Kafka offsets.retention.minutes 的缺省值是多少？
{: #offsets notoc}
缺省值为 7 天。 

偏移量保留时间适用于整个系统范围，所以不能在单个主题级别对其进行设置。所有使用者组都只能获得 7 天的存储偏移量，即便其主题已经增大到最长日志保留时间 30 天。 

## {{site.data.keyword.messagehub}} 的可用性行为如何？
{: #availability notoc}

编写 {{site.data.keyword.messagehub}} 应用程序时，请使用此信息来了解正常的 {{site.data.keyword.messagehub}} 可用性行为以及您预期应用程序处理的内容。

### API
{: #api_availability notoc}

作为 {{site.data.keyword.messagehub}} 日常操作的一部分，Kafka 集群的节点有时会重新启动。
在某些情况下，应用程序将识别到集群重新分配了资源。编写应用程序时，使其能够迅速从这些更改中恢复，能够重新连接并重试操作。

### {{site.data.keyword.messagehub}} 网桥
{: #bridge_availability notoc}

编写应用程序时，使其能够处理网桥可能不时重新启动的情况。
