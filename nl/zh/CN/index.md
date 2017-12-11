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

# Message Hub 入门
{: #messagehub}

{{site.data.keyword.messagehub_full}} 是一种可扩展、分布式、高吞吐量的消息传递服务，支持应用程序和服务轻松、可靠地进行通信。
{:shortdesc}

使用 {{site.data.keyword.messagehub}}，可以完成以下任务：

* 将工作分流到后端工作程序进程
* 将流数据连接到分析以获得深刻的见解
* 将事件数据注入到多个应用程序以实时作出反应
* 将数据传输到其他服务中，如长期存储

要开始使用 {{site.data.keyword.messagehub}} 并开始发送和接收消息，可以使用 Java™ 样本。样本显示生产者如何使用主题将消息发送给使用者。同一个样本程序用于使用消息和生成消息。

![Java 样本概览图](getting_started_sample.gif "显示消息流的 Java 样本概览图。")


请完成以下步骤：
{: #getting_started_steps}
 
1. 创建 {{site.data.keyword.messagehub}} 服务实例：

  a. 使用 Web 用户界面登录到 {{site.data.keyword.Bluemix_notm}}。 
  
  b. 单击**目录**。
  
  c. 在**应用程序服务**部分中，单击 **{{site.data.keyword.messagehub}}**。这将打开 {{site.data.keyword.messagehub}} 服务实例页面。
  
  d. 在**连接至**菜单中，使该服务保持未绑定状态，并输入服务和凭证的名称。可以使用缺省值。
  
  e. 单击**创建**。

2. 如果还没有以下必备软件，请进行安装：

    * [git ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git-scm.com/){:new_window}
	* [Gradle ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://gradle.org/){:new_window}
    * Java 7 或更高版本
 
3. 通过在命令行中运行以下命令，克隆 message-hub-samples Git 存储库：

    <pre class="pre">
    git clone https://github.com/ibm-messaging/message-hub-samples.git
    </pre>
	{: codeblock}

4. 通过运行以下命令，将目录切换到 Java 控制台样本：

    <pre class="pre">
    cd message-hub-samples/kafka-java-console-sample
    </pre>
	{: codeblock}

5. 运行以下构建命令：

    <pre class="pre">
    gradle clean && gradle build
    </pre>
	{: codeblock}

6. 通过运行以下命令，在控制台上启动使用者：

    <pre class="pre">java -jar build/libs/kafka-java-console-sample-2.0.jar 
	<var class="keyword varname">kafka_brokers_sasl</var> <var class="keyword varname">kafka_admin_url</var> <var class="keyword varname">api_key</var> -consumer</pre>
    {: codeblock}
    
    样本使用名为 `kafka-java-console-sample-topic` 的主题。如果该主题尚不存在，样本会使用 {{site.data.keyword.messagehub}} 管理 API 进行创建。为了发送和接收消息，该样本会使用 Apache Kafka Java API。

    要找到 *kafka_brokers_sasl*、*kafka_admin_url* 和 *api_key* 的值，请转至 {{site.data.keyword.Bluemix_notm}} 中的 {{site.data.keyword.messagehub}} 实例，转至**服务凭证**选项卡，然后选择要使用的**凭证**。
    
	**重要信息**：*kafka_brokers_sasl* 必须为单个字符串，并且必须用引号将其括起。例如：

    <pre class="pre">
    "host1:port1,host2:port2"
    </pre>
	{: codeblock}

    建议使用所选**凭证**中列出的所有 Kafka 主机。

7. 通过运行以下命令，在控制台上启动生产者：
   
    <pre class="pre">java -jar build/libs/kafka-java-console-sample-2.0.jar 
	<var class="keyword varname">kafka_brokers_sasl</var> <var class="keyword varname">kafka_admin_url</var> <var class="keyword varname">api_key</var> -producer</pre>
 {: codeblock}
  
8. 现在，应该会看到生产者发送的消息显示在使用者中。下面是部分样本输出：

    ```
    [2016-11-30 17:30:53,492] INFO Running in local mode. (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:53,492] INFO Updating JAAS configuration (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:53,506] INFO Kafka Endpoints: kafka01-prod01.messagehub.services.us-south.bluemix.net:9093,kafka02-prod01.messagehub.services.us-south.bluemix.net:9093,kafka03-prod01.messagehub.services.us-south.bluemix.net:9093,kafka04-prod01.messagehub.services.us-south.bluemix.net:9093,kafka05-prod01.messagehub.services.us-south.bluemix.net:9093 (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:53,506] INFO Admin REST Endpoint: https://kafka-admin-prod01.messagehub.services.us-south.bluemix.net:443 (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:53,506] INFO Creating the topic kafka-java-console-sample-topic (com.messagehub.samples.MessageHubConsoleSample)
    (com.messagehub.samples.MessageHubConsoleSample)e :{}
    [2016-11-30 17:30:54,947] INFO Admin REST Listing Topics: [{"name":"kafka-java-console-sample-topic","partitions":1,"retentionMs":"86400000","markedForDeletion":false}] (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:55,952] INFO [Partition(topic = kafka-java-console-sample-topic, partition = 0, leader = 0, replicas = [0,1,4,], isr = [0,4,1,]] (com.messagehub.samples.ConsumerRunnable)
    [2016-11-30 17:30:55,953] INFO class com.messagehub.samples.ConsumerRunnable is starting. (com.messagehub.samples.ConsumerRunnable)
    [2016-11-30 17:30:57,023] INFO [Partition(topic = kafka-java-console-sample-topic, partition = 0, leader = 0, replicas = [0,1,4,], isr = [0,4,1,]] (com.messagehub.samples.ProducerRunnable)
    [2016-11-30 17:30:57,024] INFO MessageHubConsoleSample will run until interrupted. (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:57,024] INFO class com.messagehub.samples.ProducerRunnable is starting. (com.messagehub.samples.ProducerRunnable)
    [2016-11-30 17:30:58,018] INFO Message produced, offset: 0 (com.messagehub.samples.ProducerRunnable)
    [2016-11-30 17:30:58,956] INFO No messages consumed (com.messagehub.samples.ConsumerRunnable)
    [2016-11-30 17:31:00,301] INFO Message consumed: ConsumerRecord(topic = kafka-java-console-sample-topic, partition = 0, offset = 1, CreateTime = 1480527060022, checksum = 1906962734, serialized key size = 3, serialized value size = 25, key = key, value = This is a test message #1) (com.messagehub.samples.ConsumerRunnable)
    [2016-11-30 17:31:00,397] INFO Message produced, offset: 1 (com.messagehub.samples.ProducerRunnable)
    [2016-11-30 17:31:02,550] INFO Message consumed: ConsumerRecord(topic = kafka-java-console-sample-topic, partition = 0, offset = 2, CreateTime = 1480527062401, checksum = 3801731428, serialized key size = 3, serialized value size = 25, key = key, value = This is a test message #2) (com.messagehub.samples.ConsumerRunnable)
    ```
	{: codeblock}
	
9. 样本会无限期运行，直到您将其停止。要停止该进程，请运行类似下面的命令：<code>Ctrl+C</code>


要了解有关使用 Python 运行 {{site.data.keyword.messagehub}} 样本的更多信息，请参阅 [Python 控制台样本应用程序 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/messaging/2017/02/09/new-message-hub-sample-python-console-application/){:new_window}。还可以在 [{{site.data.keyword.messagehub}} 样本 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/ibm-messaging/message-hub-samples){:new_window} 中找到用于演示其他 API 和功能的样本。

要观看相关视频以了解如何获取针对 {{site.data.keyword.messagehub}} 运行的 Java 样本，请参阅 [{{site.data.keyword.messagehub}} - Getting started with IBM's Kafka in the cloud ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.youtube.com/watch?v=tt-bLtFzC_4){:new_window}。

