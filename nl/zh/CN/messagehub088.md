---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-01"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 使用网桥链接到其他服务
{: #bridges}

网桥是 {{site.data.keyword.messagehub}} 与其他服务之间的单向链接。网桥支持从 {{site.data.keyword.messagehub}} 读取数据并写入其他服务，或从其他服务读取数据并写入 {{site.data.keyword.messagehub}}。

{:shortdesc}

使用 {{site.data.keyword.messagehub}} 网桥的主要优点如下：  

* 可以通过管理方式定义网桥，因此无需编写应用程序代码。
* 每个网桥的生命周期由 {{site.data.keyword.messagehub}} 服务进行监视和管理。例如，如果网桥遇到错误，那么 {{site.data.keyword.messagehub}} 会自动重新启动网桥。
* 网桥与 {{site.data.keyword.Bluemix_short}} 平台集成。例如，网桥生成的日志记录和监视信息将定向到 Kibana 和 Grafana 仪表板。

在以下两个常见场景中，您可能会发现网桥非常有用：

* 使用来自一个或多个数据源的数据并将其传输到 {{site.data.keyword.messagehub}}。
* 将来自 {{site.data.keyword.messagehub}} 的数据传输到其他服务。例如，传输到长期存储器。

## {{site.data.keyword.messagehub}} 网桥
{: notoc}

* 我们提供了以下两种类型的网桥： 
  - MQ 网桥，用于获取来自 {{site.data.keyword.IBM}} MQ 的消息数据，并将其传输到 {{site.data.keyword.messagehub}} 中的主题。未来，我们打算支持更广泛的网桥。
  - {{site.data.keyword.objectstorageshort}} 网桥，用于将 {{site.data.keyword.messagehub}} 数据传输到 [Object Storage 服务 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/services/ObjectStorage/index.html){:new_window} 的实例。
* 目前，网桥在所有 {{site.data.keyword.Bluemix_notm}} Public 环境中可用。但网桥在 {{site.data.keyword.Bluemix_short}} Dedicated 中不可用。
* 可以通过以下两种方式来管理网桥：
  - 使用 [REST API ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/ibm-messaging/message-hub-docs){:new_window}，这是现有 {{site.data.keyword.messagehub}} 管理 API 的扩展。还可以在 [message-hub-docs ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/ibm-messaging/message-hub-docs){:new_window} 上找到有关如何使用 curl 来管理网桥生命周期的示例。随着网桥的继续开发，我们可能会更改此 REST API。我们打算使此 API 保持稳定。
  - 使用 {{site.data.keyword.Bluemix_notm}} 控制台中的 {{site.data.keyword.messagehub}} 仪表板。
* 可以将任意类型的最多两个网桥与一个 {{site.data.keyword.messagehub}} 服务实例相关联。随着网桥的继续开发，我们可能会继续复查此限制。
* 将网桥用于除消息传递操作以外的情况，不会发生额外费用。
* MQ 网桥不支持使用 SSL/TLS 来保护数据隐私和完整性，因为数据是在网桥和 MQ 队列管理器之间传输的。我们打算添加对 SSL/TLS 用于网桥的支持。 
* {{site.data.keyword.objectstorageshort}} 网桥在将数据写入 {{site.data.keyword.objectstorageshort}} 时，使用换行符作为分隔符来连接消息。这会导致网桥不适用于包含嵌入式换行符的消息以及二进制消息数据。
* {{site.data.keyword.objectstorageshort}} 网桥当前使用的对象命名约定在未来可能会更改。

不过，您可以使用 [{{site.data.keyword.SecureGatewayfull}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/services/SecureGateway/secure_gateway.html){:new_window} 服务，通过 {{site.data.keyword.Bluemix_notm}} 与可采用内部部署方式安装的 {{site.data.keyword.SecureGateway}} 客户机之间的安全通道来发送数据。在此配置中，通道任一端的通信均未使用 SSL/TLS 进行保护。
