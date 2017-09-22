---

copyright:
  years: 2015, 2017
lastupdated: "2017-02-08"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 在 Bluemix Public 和 Bluemix Dedicated 环境中 Message Hub 的差异
{: #public_dedicated}

{{site.data.keyword.Bluemix}} 是一种基于云的开放标准平台，用于构建、运行和管理应用程序。{{site.data.keyword.Bluemix_notm}} 提供公共和专用部署模型。{{site.data.keyword.messagehub}} 在这两种环境中均可用。

## {{site.data.keyword.Bluemix_notm}} Public 环境
{: notoc}

{{site.data.keyword.Bluemix_notm}} Public 提供了经济的公共云服务，在其中您按使用内容付费，并与其他人共享基础架构。

在 {{site.data.keyword.Bluemix_notm}} Public 中，{{site.data.keyword.messagehub}} 的开销由两个因素决定：您使用的分区数；以及您发送和接收的消息数。对于保留在主题上的消息数据，不会收费，但每个分区保留的数据上限为 1 GB。

有关更多信息，请参阅 [{{site.data.keyword.Bluemix_notm}} Public ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud-computing/bluemix/public){:new_window}。


## {{site.data.keyword.Bluemix_notm}} Dedicated 环境
{: notoc}

{{site.data.keyword.Bluemix_notm}} Dedicated 提供的是隔离性更强的环境，在其中基础架构不共享，而是在 {{site.data.keyword.IBM_notm}} 管理的单独 SoftLayer 帐户中进行托管。此环境以安全方式连接到 {{site.data.keyword.Bluemix_notm}} Public 和您自己的网络。

在 {{site.data.keyword.messagehub}} 的专用实例中，您是按服务付费，而不是按服务使用量付费。您在整个环境（包括所有组织和空间）中最多可以拥有 75 个分区。每个分区的上限为 10 GB，以确保集群不会耗尽空间。

{{site.data.keyword.Bluemix_notm}} Dedicated 中不支持用于监视服务的 Kibana 和 Grafana 仪表板。

有关更多信息，请参阅 [{{site.data.keyword.Bluemix_notm}} Dedicated ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/cloud-computing/bluemix/dedicated/){:new_window}。


