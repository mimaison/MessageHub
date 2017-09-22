---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-03"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 使用 Kafka Java 客户机
{: #kafka_using}

## 如何使用、下载和运行 Java Kafka API 样本
{: notoc}

Java&trade; Kafka API 样本是用 Java 编写的示例生产者和使用者，此样本直接使用 Kafka API。可以在本地或在 {{site.data.keyword.Bluemix_short}} 中运行此样本。

样本代码位于 [message-hub-samples GitHub 项目 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window} 中。虽然该样本使用 Kafka API 来发送和接收消息，但该样本使用 {{site.data.keyword.messagehub}} 管理 API 来创建主题，以便向该主题发送消息和从该主题接收消息。

有关设置和运行此样本的更多信息，请参阅 [README.md ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}。

有关如何运行样本的详细说明，请参阅 [{{site.data.keyword.messagehub}} 入门](/docs/services/MessageHub/index.html#getting_started_steps)。

## 如何使用、下载和运行 Liberty for Java 样本
{: #liberty_sample notoc}

Liberty for Java 样本实现部署到 Liberty 运行时上的简单应用程序。应用程序将 Kafka API 用于 {{site.data.keyword.messagehub}} 来生成和使用消息。应用程序还提供了一个可用于管理的 Web 前端。

可以在 [message-hub-samples GitHub 项目 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-liberty-sample){:new_window} 中找到样本代码。

## 如何将 Kafka 客户机从 0.9.x 迁移到 0.10.x
{: #kafka_migrate notoc}


如果使用的是 Java 客户机，那么现在可以使用公共可用的 0.10.x Kafka 客户机。强烈建议您从 0.9.x 迁移到最新的 0.10.x 版本（当前为 0.10.2.1）。请完成以下步骤：

1. 删除 {{site.data.keyword.messagehub}} 登录 JAR 模块。
2. 将 <code>jaas.conf</code> 文件更改为以下内容：
    ```
        KafkaClient {
          org.apache.kafka.common.security.plain.PlainLoginModule required
          serviceName="kafka"
            username="<your username>"
            password="<your password>";
        };
    ```
    {: codeblock}

3. 将以下行添加到使用者和生产者属性：<code>sasl.mechanism=PLAIN</code>


## 使用 sasl.jaas.config 属性
{: #sasl_prop notoc}
如果使用的是 0.10.2.1 或更高版本的 Kafka 客户机，那么可以使用 <code>sasl.jaas.config</code> 属性进行客户机配置，而不使用 JAAS 文件。要连接到 {{site.data.keyword.messagehub}}，请按如下所示设置 <code>sasl.jaas.config</code>：
<pre>
<code>    sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required \
    username="USERNAME" \
    password="PASSWORD";</code>
</pre>
{:codeblock}

其中，USERNAME 和 PASSWORD 是 {{site.data.keyword.Bluemix_notm}} 的 {{site.data.keyword.messagehub}} **服务凭证**选项卡中的值。

如果使用 <code>sasl.jaas.config</code>，那么在同一 JVM 中运行的客户机可以使用不同的凭证。有关更多信息，请参阅[配置 Kafka 客户机 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://kafka.apache.org/documentation/#security_sasl_plain_clientconfig){:new_window}。

## 用于主题管理的 API
{: #topic_admin notoc}

如果使用的是 0.11 或更高版本的 Kafka 客户机，或者 0.10.2.0 或更高版本的 Kafka Streams，那么可以使用 API 来创建和删除主题。我们已经对创建主题时允许使用的设置施加了一些限制。当前，只能修改以下设置：

<dl>
<dt>cleanup.policy</dt>
<dd>设置为 <code>delete</code>（缺省值）、<code>compact</code> 或 <code>delete,compact</code></dd>
<dt>retention.ms</dt>
<dd>缺省保留期为 24 小时。最小值为 1 小时，最大值为 30 天。请将此值指定为小时的倍数。

<p>**注**：如果清除策略仅为 <code>compact</code>，那么会自动添加 <code>delete</code>，但会根据时间来禁用删除。在删除主题中的消息之前，会将其压缩到最高 1 GB。</p>
</dd>
</dl>

## 支持 Kafka Streams
{: #kafka_streams notoc}

从 Streams 库 0.10.2.0 开始，现在主题 API 使用 {{site.data.keyword.messagehub}} 时，无需进行任何设置。请使用 <code>sasl.jaas.config</code> 或 JAAS 文件指定 SASL 凭证，并将 <code>replication.factor</code> 设置为 3。

例如：

<pre>
<code>
    props.put(StreamsConfig.REPLICATION_FACTOR_CONFIG, "3");
    props.put(StreamsConfig.BOOTSTRAP_SERVERS_CONFIG, BOOTSTRAP_SERVERS);
    props.put("security.protocol","SASL_SSL");
    props.put("sasl.mechanism","PLAIN");
    props.put("ssl.protocol","TLSv1.2");
    props.put("ssl.enabled.protocols","TLSv1.2");
    props.put("sasl.jaas.config","org.apache.kafka.common.security.plain.PlainLoginModule required username=\"USERNAME\" password=\"PASSWORD\";");
</code>
</pre>
{:codeblock}

其中，BOOTSTRAP_SERVERS、USERNAME 和 PASSWORD 是 {{site.data.keyword.Bluemix_notm}} 的 {{site.data.keyword.messagehub}} **服务凭证**选项卡中的值。

<!--
new topic that includes content from existing topics about samples and migration
-->
