---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-27"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# What is {{site.data.keyword.messagehub}}?

{{site.data.keyword.messagehub}} implements publish/subscribe
messaging using topics. Unlike other messaging systems, {{site.data.keyword.messagehub}} provides topics but not queues. {{site.data.keyword.messagehub}} also offers
additional capabilities such as bridges to other systems.

{{site.data.keyword.messagehub}} is based on the open-source
Apache Kafka project, a highly scalable, high-performing messaging backbone proven in many
production environments. For more information, see [{{site.data.keyword.messagehub}} and Apache Kafka](/docs/services/MessageHub/messagehub073.html).
Apache Kafka tools usually work directly with Message Hub, although you do need to provide additional configuration since connections to Message Hub always authenticate using credentials.

{{site.data.keyword.messagehub}} has three APIs: the Kafka API, the Kafka REST API and the {{site.data.keyword.mql}} API.
In most cases, the Kafka API is the best choice. For more information about
creating messaging applications using the APIs, see [Using a Kafka client](/docs/services/MessageHub/messagehub050.html), , and [Using the Kafka REST API](/docs/services/MessageHub/messagehub025.html), and [Using an MQ Light API client](/docs/services/MessageHub/messagehub075.html).

{{site.data.keyword.messagehub}} also
supports bridges to a selection of other systems. A bridge is a unidirectional link to another
system. A bridge can take messages from the other system and publish them onto a topic, or consume
messages from a topic and send them to the other system. In this way, you can use {{site.data.keyword.messagehub}} to integrate with other systems without writing code. For more information, see [Linking to other services using bridges](/docs/services/MessageHub/messagehub088.html).
