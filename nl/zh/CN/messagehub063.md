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

# 如何连接和认证
{: #kafka_connect}


为了连接到 {{site.data.keyword.messagehub}}，Kafka API 使用 [VCAP_SERVICES 环境变量](/docs/services/MessageHub/messagehub071.html)中的  
```kafka_brokers_sasl
``` 
凭证以及
```
user
```
和

 ```password
```
 。
## 在非 Java 应用程序中进行连接和认证
{: #kafka_notjava notoc}

目前，{{site.data.keyword.messagehub}} 服务使用 SASL PLAIN 对客户机进行认证。凭证将随过加密连接传递。这是 Kafka 0.10.0.X 中添加的新功能。支持使用 SASL PLAIN 的 Kafka 0.10 的任何客户机都应该使用 {{site.data.keyword.messagehub}}。示例客户机如下所示：

* [librdkafka ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/edenhill/librdkafka/){:new_window}
* [confluent-kafka-python ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/confluentinc/confluent-kafka-python){:new_window}

如果使用的是更低版本 Kafka 0.9.0.0 的客户机，那么需要使用定制登录模块，此模块可从 [{{site.data.keyword.messagehub}} 登录模块 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/ibm-messaging/message-hub-samples/blob/master/kafka-0.9/message-hub-login-library/messagehub.login-1.0.0.jar){:new_window} 下载。

