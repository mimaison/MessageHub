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

# 接続および認証の方法
{: #kafka_connect}


{{site.data.keyword.messagehub}} に接続するために、Kafka API は、 
```kafka_brokers_sasl
``` 
資格情報と、
```
ユーザー
```
および

 ```password
```
 を [VCAP_SERVICES 環境変数](/docs/services/MessageHub/messagehub071.html) から使用します。

## Java 以外のアプリケーションでの接続および認証
{: #kafka_notjava notoc}

{{site.data.keyword.messagehub}} サービスは、現在は SASL PLAIN を使用してクライアントを認証します。資格情報は、暗号化された接続を介して伝送されます。
これは、Kafka 0.10.0.X で追加された新機能です。SASL PLAIN と Kafka 0.10 をサポートするクライアントであれば、{{site.data.keyword.messagehub}} で機能します。以下にクライアントの例を示します。

* [librdkafka ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/edenhill/librdkafka/){:new_window}
* [confluent-kafka-python ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/confluentinc/confluent-kafka-python){:new_window}

以前の Kafka 0.9.0.0 クライアントを使用している場合、
[{{site.data.keyword.messagehub}} ログイン・モジュール ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/ibm-messaging/message-hub-samples/blob/master/kafka-0.9/message-hub-login-library/messagehub.login-1.0.0.jar){:new_window} からダウンロードできる、カスタム・ログイン・モジュールを使用する必要があります。

