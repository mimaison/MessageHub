---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-11"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 如何連接及鑑別
{: #kafka_connect}


為了連接至 {{site.data.keyword.messagehub}}，Kafka API 會使用 `kafka_brokers_sasl`
認證，以及來自 [VCAP_SERVICES 環境變數](/docs/services/MessageHub/messagehub071.html)的
`user` 及 `password`。

## 在非 Java 的應用程式中進行連接及鑑別
{: #kafka_notjava notoc}

{{site.data.keyword.messagehub}} 服務目前使用 SASL PLAIN 來鑑別用戶端。認證會在已加密的連線上傳送。這是 Kafka 0.10.0.X 中新增的特性。支援 Kafka 0.10 與 SASL PLAIN
的任何用戶端都應該能搭配 {{site.data.keyword.messagehub}}。範例用戶端如下所示：

* [librdkafka ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/edenhill/librdkafka/){:new_window} 
* [confluent-kafka-python ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/confluentinc/confluent-kafka-python){:new_window} 

如果您使用較早的 Kafka 0.9.0.0 用戶端，您需要使用自訂登入模組，這可以從 [{{site.data.keyword.messagehub}} 登入模組 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/ibm-messaging/message-hub-samples/blob/master/kafka-0.9/message-hub-login-library/messagehub.login-1.0.0.jar){:new_window} 下載。 

