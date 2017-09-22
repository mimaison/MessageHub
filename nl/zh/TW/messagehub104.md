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

# 使用 Kafka Java client
{: #kafka_using}

## 如何使用、下載及執行 Java API 範例
{: notoc}

Java&trade; Kafka API 範例是以 Java 撰寫的範例生產者與消費者，它會直接使用 Kafka API。您可以在本端執行此範例，或是在 {{site.data.keyword.Bluemix_short}} 執行。

範例程式碼位於 [message-hub-samples GitHub 專案 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}。雖然範例使用
Kafka API 來傳送及接收訊息，範例會使用 {{site.data.keyword.messagehub}} 管理 API
來建立與它傳送及接收訊息的主題。

如需設定及執行範例的相關資訊，請參閱 [README.md ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}。

如需如何執行範例的詳細逐步演練，請參閱[開始使用 {{site.data.keyword.messagehub}}](/docs/services/MessageHub/index.html#getting_started_steps)。

## 如何使用、下載及執行 Liberty for Java 範例
{: #liberty_sample notoc}

Liberty for Java 範例會實作一個簡單的應用程式，部署至 Liberty 運行環境。應用程式使用 {{site.data.keyword.messagehub}} 的 Kafka API 來生產及取用訊息。應用程式也會提供 Web 前端，您可以用來進行管理。

範例程式碼位於 [message-hub-samples GitHub 專案 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-liberty-sample){:new_window}。

## 如何將 Kafka 用戶端從 0.9.x 移轉至 0.10.x
{: #kafka_migrate notoc}


如果您使用 Java 用戶端，現在可以使用公開提供的 0.10 x Kafka 用戶端。我們強烈鼓勵您從 0.9.x 移至最新的 0.10.x 版（目前為 0.10.2.1）。請完成下列步驟：

1. 刪除 {{site.data.keyword.messagehub}} 登入 jar 模組。
2. 將 <code>jaas.conf</code> 檔案變更如下：
    ```
        KafkaClient {
          org.apache.kafka.common.security.plain.PlainLoginModule required
          serviceName="kafka"
            username="<your username>"
            password="<your password>";
        };
    ```
    {: codeblock}

3. 將此行新增到您的消費者和生產者內容：<code>sasl.mechanism=PLAIN</code>


## 使用 sasl.jaas.config 內容
{: #sasl_prop notoc}
如果您使用 Kafka 用戶端 0.10.2.1 或更新版本，可以使用 <code>sasl.jaas.config</code> 內容進行用戶端配置，而不要使用 JAAS 檔案。若要連接至
{{site.data.keyword.messagehub}}，請如下所示設定 <code>sasl.jaas.config</code>：
<pre>
<code>    sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required \
    username="USERNAME" \
    password="PASSWORD";</code>
</pre>
{:codeblock}

其中 USERNAME 及 PASSWORD 是來自 {{site.data.keyword.Bluemix_notm}} 中 {{site.data.keyword.messagehub}} **服務認證**標籤的值。

如果您使用 <code>sasl.jaas.config</code>，在相同 JVM 中執行的用戶端可以使用不同的認證。如需相關資訊，請參閱
[Configuring Kafka clients ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://kafka.apache.org/documentation/#security_sasl_plain_clientconfig){:new_window}

## 主題管理用的 API
{: #topic_admin notoc}

如果您使用 Kafka 用戶端 0.11 或更新版本，或 Kafka Streams 0.10.2.0 或更新版本，可以使用 API 來建立及刪除主題。我們已對您建立主題時接受的設定做了一些限制。目前，您只能修改下列設定：

<dl>
<dt>cleanup.policy</dt>
<dd>設為 <code>delete</code>（預設值）、<code>compact</code> 或 <code>delete,compact</code></dd>
<dt>retention.ms</dt>
<dd>預設保留期間是 24 小時。最短 1 小時，最長 30 天。請以小時的倍數來指定此值。

<p>**附註：**如果清理原則是僅 <code>compact</code>，我們會自動新增 <code>delete</code> 但停用根據時間刪除。主題中的訊息在刪除之前最多可壓縮到 1 GB。</p>
</dd>
</dl>

## Kafka Streams 的支援
{: #kafka_streams notoc}

從 Streams 程式庫 0.10.2.0 開始，主題 API 現在可搭配 {{site.data.keyword.messagehub}} 運作，不需要設定。請使用 <code>sasl.jaas.config</code> 或 JAAS 檔案指定 SASL 認證，並將 <code>replication.factor</code> 設為 3。

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

其中 BOOTSTRAP_SERVERS、USERNAME 及 PASSWORD 是來自 {{site.data.keyword.Bluemix_notm}} 中 {{site.data.keyword.messagehub}} **服務認證**標籤的值。

<!--
new topic that includes content from existing topics about samples and migration
-->
