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
{:table: .aria-labeledby="caption"}

# 在 MQ Light API 和 Kafka 或 Kafka REST API 之间交换消息
{: #mql_exchange}

{{site.data.keyword.mql}} 消息存储在名为“MQLight”的单个底层 Kafka 主题中并经过编码，如下表中所详述。其他 API 类型（如 Kafka 或 Kafka REST）也可使用此编码通过 {{site.data.keyword.mql}} API 来与应用程序交换消息。

## Kafka 消息格式
{: #kafka_format notoc}

<table border='1'>
<caption>表 1. Kafka 消息格式</caption>
  <tr>
    <th> 键</th>
    <th> 值</th>
  </tr>
  <tr>
    <td> 可选（API 不予使用）<p></p>
	</td>
    <td>**1 字节**
	<p>		     MQ Light API 视觉焦点，始终为 0xFA。</p>
    <p><var class="keyword varname">**n**</var> **字节**</p>
    <p>		    AMQP 编码的消息（格式基于 AMQP 有线格式）。</p></td>
  </tr>
</table>


