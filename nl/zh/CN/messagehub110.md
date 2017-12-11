---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-26"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 将 KSQL 与 Message Hub 配合使用
{: #ksql_using}

您可以将 [KSQL ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/confluentinc/ksql){:new_window} 与{{site.data.keyword.messagehub}} 配合使用以进行流处理。请完成以下步骤：

1. 创建 {{site.data.keyword.messagehub}} KSQL 配置文件。

    例如：
    ```
    bootstrap.servers=HOSTNAME:PORTNUMBER
    application.id=ksql_server_quickstart
    ksql.command.topic.suffix=commands
    listeners=http://localhost:8080
    security.protocol=SASL_SSL
    sasl.mechanism=PLAIN
    ssl.protocol=TLSv1.2
    ssl.enabled.protocols=TLSv1.2
    sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required username="USERNAME" password="PASSWORD";
    ksql.sink.replications.default=3
    ```
    确保您编辑以下行，以插入自己的数据：
	- <code>bootstrap.servers</code> - 插入**服务凭证**页面中列出的所有 Kafka 主机。要查找此信息，请转至 {{site.data.keyword.Bluemix_notm}} 中的 {{site.data.keyword.messagehub}} 实例，转至**服务凭证**选项卡，然后选择要使用的**凭证**。

	- <code>sasl.jaas.config</code> - 插入自己的用户名和密码对
	
2. 使用 {{site.data.keyword.Bluemix_notm}} 控制台中的 {{site.data.keyword.messagehub}} 仪表板，创建名为 <code>ksql__commands</code> 的主题，其具有单个分区和默认保留期。
3. 从 Docker 终端中，使用以下命令启动 KSQL：
<pre class="pre">/bin/ksql-cli local 
--<var class="keyword varname">properties-file</var> ./config/ksqlserver.properties
</pre>
4. 要填充数据，请在 <code>ksql-examples</code> 项目中，编辑 <code>io.confluent.ksql.datagen</code> 中的 <code>DataGen</code> 类。例如：
```
     Properties props = new Properties();
     props.put("bootstrap.servers", arguments.bootstrapServer);
     props.put("client.id", "KSQLDataGenProducer");
     props.put("security.protocol", "SASL_SSL");
     props.put("sasl.mechanism", "PLAIN");
     props.put("ssl.protocol", "TLSv1.2");
     props.put("ssl.enabled.protocols", "TLSv1.2");
     props.put("sasl.jaas.config", "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"USERNAME\" password=\"PASSWORD\";"); 
```
    {: codeblock}
5. 使用 {{site.data.keyword.Bluemix_notm}} 控制台中的 {{site.data.keyword.messagehub}} 仪表板，创建两个主题，每个主题分别具有一个分区：<code>users</code> 和 <code>pageviews</code>。

    然后，启动 <code>DataGen</code> 两次，如下所示：
	
    i. 使用 <code>bootstrap-server=HOSTNAME:PORTNUMBER quickstart=users format=json topic=users maxInterval=10000</code> 开始创建 <code>users</code> 事件。
	
    ii. 使用 <code>bootstrap-server=HOSTNAME:PORTNUMBER quickstart=pageviews format=delimited topic=pageviews maxInterval=10000</code> 开始创建 <code>pageviews</code> 事件。
	
	确保插入**服务凭证**页面中列出的所有 Kafka 主机，作为 <code>bootstrap-server</code> 的值。要查找此信息，请转至 {{site.data.keyword.Bluemix_notm}} 中的 {{site.data.keyword.messagehub}} 实例，转至**服务凭证**选项卡，然后选择要使用的**凭证**。


当您完成这些步骤时，可以运行 [KSQL 快速入门指南 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/confluentinc/ksql/tree/0.1.x/docs/quickstart#create-a-stream-and-table){:new_window} 中列出的所有查询

