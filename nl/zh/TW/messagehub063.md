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

# 如何連接及鑑別
{: #kafka_connect}


為了連接至 {{site.data.keyword.messagehub}}，Kafka API 會使用 <code>kafka_brokers_sasl</code> 認證，以及來自 [VCAP_SERVICES 環境變數](/docs/services/MessageHub/messagehub071.html)的 <code>user</code> 及 <code>password</code>。

<!--17/10/17 - Karen: following info duplicated at messagehub104 -->
## 使用 sasl.jaas.config 內容（在 Java 應用程式中進行連接及鑑別）
{: #kafka_java notoc}
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

若為較早的 Kafka 用戶端，您必須使用 JAAS 配置檔來指定認證。此機制較不方便，因此我們建議使用改用 <code>sasl.jaas.config</code> 內容。

## 在非 Java 的應用程式中進行連接及鑑別
{: #kafka_notjava notoc}

{{site.data.keyword.messagehub}} 服務目前使用 SASL PLAIN over TLS 來鑑別用戶端。認證會在已加密的連線上傳送。這是 Kafka 0.10.0.X 中新增的特性。下列範例是名為 <code>consumer.properties</code> 的範例配置檔：

```
key.deserializer=org.apache.kafka.common.serialization.StringDeserializer
value.deserializer=org.apache.kafka.common.serialization.StringDeserializer
#
client.id=kafka-java-console-sample-consumer
group.id=kafka-java-console-sample-group
#
security.protocol=SASL_SSL
sasl.mechanism=PLAIN
sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required username="USERNAME" password="PASSWORD";
ssl.protocol=TLSv1.2
ssl.enabled.protocols=TLSv1.2
ssl.endpoint.identification.algorithm=HTTPS
#
# please read the Kafka docs about this setting
auto.offset.reset=latest
```
{: codeblock}

支援 Kafka 0.10 與 SASL PLAIN 的任何用戶端都應該能搭配 {{site.data.keyword.messagehub}}。範例用戶端如下所示：

* [librdkafka ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/edenhill/librdkafka/){:new_window} 
* [confluent-kafka-python ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/confluentinc/confluent-kafka-python){:new_window} 

如果您使用較早的 Kafka 0.9.0.0 用戶端，您需要使用自訂登入模組，這可以從 [{{site.data.keyword.messagehub}} 登入模組 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/ibm-messaging/message-hub-samples/blob/master/kafka-0.9/message-hub-login-library/messagehub.login-1.0.0.jar){:new_window} 下載。 

