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

# 使用 KSQL 搭配 Message Hub
{: #ksql_using}

您可以使用 [KSQL ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/confluentinc/ksql){:new_window} 搭配 {{site.data.keyword.messagehub}} 以進行串流處理。請完成下列步驟：

1. 建立 {{site.data.keyword.messagehub}} KSQL 配置檔。

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
    確定您編輯下列幾行以插入自己的資料：
	- <code>bootstrap.servers</code> - 插入**服務認證**頁面中列出的所有 Kafka 主機。若要找到此資訊，請移至 {{site.data.keyword.Bluemix_notm}} 中的 {{site.data.keyword.messagehub}} 實例、移至**服務認證**標籤，然後選取您想要使用的**認證**。
	- <code>sasl.jaas.config</code> - 插入您自己的使用者名稱及密碼配對
	
2. 使用 {{site.data.keyword.Bluemix_notm}} 主控台中的 {{site.data.keyword.messagehub}} 儀表板建立稱為 <code>ksql__commands</code> 的主題，它具有單一分割區和預設保留期間。
3. 從 Docker 終端機，使用下列指令啟動 KSQL：
<pre class="pre">/bin/ksql-cli local 
--<var class="keyword varname">properties-file</var> ./config/ksqlserver.properties
</pre>
4. 若要移入資料，請在 <code>ksql-examples</code> 專案的 <code>io.confluent.ksql.datagen</code> 中編輯 <code>DataGen</code> 類別。例如：
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
5. 使用 {{site.data.keyword.Bluemix_notm}} 主控台中的 {{site.data.keyword.messagehub}} 儀表板建立兩個主題，並各有一個分割區：<code>users</code> 及 <code>pageviews</code>。

    然後啟動 <code>DataGen</code> 兩次，如下所示：
	
    i. 使用 <code>bootstrap-server=HOSTNAME:PORTNUMBER quickstart=users format=json topic=users maxInterval=10000</code> 開始建立 <code>users</code> 事件。
	
    ii. 使用 <code>bootstrap-server=HOSTNAME:PORTNUMBER quickstart=pageviews format=delimited topic=pageviews maxInterval=10000</code> 開始建立 <code>pageviews</code> 事件。
	
	確定您將**服務認證**頁面中列出的所有 Kafka 主機，插入為 <code>bootstrap-server</code> 的值。若要找到此資訊，請移至 {{site.data.keyword.Bluemix_notm}} 中的 {{site.data.keyword.messagehub}} 實例、移至**服務認證**標籤，然後選取您想要使用的**認證**。

當您完成這些步驟之後，可以執行 [KSQL Quick Start Guide ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/confluentinc/ksql/tree/0.1.x/docs/quickstart#create-a-stream-and-table){:new_window} 列出的所有查詢

