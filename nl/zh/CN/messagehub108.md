---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.messagehub}} 常见问题解答
{: #faqs}

对有关 {{site.data.keyword.IBM}} {{site.data.keyword.messagehub}} 服务的常见问题的解答。

<!--17/10/17 - Karen: same info duplicated at messagehub104 -->
## 如何使用 Kafka API 来创建和删除主题？
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

## {{site.data.keyword.messagehub}} 为使用者偏移量主题设置保留时间窗口需要多长时间？
{: #offsets notoc}
{{site.data.keyword.messagehub}} 保留使用者偏移量 7 天。这对应于 Kafka 配置 offsets.retention.minutes。 

偏移量保留时间适用于整个系统范围，所以不能在单个主题级别对其进行设置。所有使用者组都只能获得 7 天的存储偏移量，即便所使用主题的日志保留时间已经增大到最长 30 天也是如此。 

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
