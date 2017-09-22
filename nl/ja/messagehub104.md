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

# Kafka Java クライアントの使用
{: #kafka_using}

## Java Kafka API サンプルの使用、ダウンロード、および実行の方法
{: notoc}

Java&trade; Kafka API サンプルは、Kafka API を直接使用するプロデューサーとコンシューマーの例であり、Java で記述されています。このサンプルは、ローカルで実行するか、{{site.data.keyword.Bluemix_short}} 内で実行することができます。

サンプル・コードは [message-hub-samples GitHub プロジェクト ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window} にあります。このサンプルは、メッセージの送受信には Kafka API を使用しますが、メッセージの送信先およびメッセージの受信元のトピックの作成には {{site.data.keyword.messagehub}} 管理 API を使用します。

このサンプルのセットアップおよび実行について詳しくは、[README.md ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window} を参照してください。

このサンプルの実行方法の段階的な詳しい説明については、[{{site.data.keyword.messagehub}} 入門](/docs/services/MessageHub/index.html#getting_started_steps)を参照してください。

## Liberty for Java サンプルの使用、ダウンロード、および実行の方法
{: #liberty_sample notoc}

Liberty for Java サンプルは、Liberty ランタイムにデプロイされる単純なアプリケーションを実装します。このアプリケーションは、{{site.data.keyword.messagehub}} がメッセージの生成とコンシュームを行うために、Kafka API を使用します。
また、このアプリケーションは、管理のために使用できる Web フロントエンドを提供します。

サンプル・コードは [message-hub-samples GitHub プロジェクト ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-liberty-sample){:new_window} にあります。

## 0.9.x から 0.10.x への Kafka クライアントのマイグレーション方法
{: #kafka_migrate notoc}


Java クライアントを使用している場合、公開された 0.10.x Kafka クライアントを使用できるようになりました。0.9.x から最新の 0.10.x バージョン (現在は 0.10.2.1) に移行することを強くお勧めします。以下のステップを実行してください。

1. {{site.data.keyword.messagehub}} ログイン jar モジュールを削除します。
2. <code>jaas.conf</code> ファイルを次のように変更します。
    ```
        KafkaClient {
          org.apache.kafka.common.security.plain.PlainLoginModule required
          serviceName="kafka"
            username="<your username>"
            password="<your password>";
        };
    ```
    {: codeblock}

3. コンシューマーおよびプロデューサーのプロパティーに <code>sasl.mechanism=PLAIN</code> という行を追加します。


## sasl.jaas.config プロパティーの使用
{: #sasl_prop notoc}
0.10.2.1 以降の Kafka クライアントを使用している場合、JAAS ファイルの代わりに、クライアント構成に <code>sasl.jaas.config</code> プロパティーを使用できます。{{site.data.keyword.messagehub}} に接続するためには、<code>sasl.jaas.config</code> を次のように設定します。
<pre>
<code>    sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required \
    username="USERNAME" \
    password="PASSWORD";</code>
</pre>
{:codeblock}

ここで、USERNAME および PASSWORD は、{{site.data.keyword.Bluemix_notm}} の {{site.data.keyword.messagehub}} **「サービス資格情報」**タブからの値です。

<code>sasl.jaas.config</code> を使用する場合、同じ JVM で稼働している複数のクライアントはそれぞれ異なる資格情報を使用できます。詳しくは、[Configuring Kafka clients  ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://kafka.apache.org/documentation/#security_sasl_plain_clientconfig){:new_window} を参照してください。

## トピック管理用の API
{: #topic_admin notoc}

0.11 以降の Kafka クライアントまたは 0.10.2.0 以降の Kafka Streams を使用している場合、API を使用してトピックの作成と削除を行うことができます。トピック作成時に許可される設定には、いくつかの制限があります。現在のところ、変更できるのは以下の設定のみです。

<dl>
<dt>cleanup.policy</dt>
<dd><code>delete</code> (デフォルト)、<code>compact</code>、または <code>delete,compact</code> に設定してください。</dd>
<dt>retention.ms</dt>
<dd>デフォルトの保存期間は 24 時間です。最小は 1 時間、最大は 30 日間です。この値は、時間の倍数で指定してください。

<p>**注:**
クリーンアップ・ポリシーが <code>compact</code> のみである場合、自動的に <code>delete</code> が追加されますが、時間に基づく削除は無効にされます。トピック内のメッセージは、削除される前に 1 GB にまで圧縮されます。</p>
</dd>
</dl>

## Kafka Streams のサポート
{: #kafka_streams notoc}

Streams library 0.10.2.0 以降、トピック API はセットアップを必要とせずに {{site.data.keyword.messagehub}} とともに機能するようになりました。SASL 資格情報を <code>sasl.jaas.config</code> または JAAS ファイルを使用して指定し、<code>replication.factor</code> を 3 に設定してください。

以下に例を示します。

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

ここで、BOOTSTRAP_SERVERS、USERNAME、および PASSWORD は、{{site.data.keyword.Bluemix_notm}} の {{site.data.keyword.messagehub}} **「サービス資格情報」**タブからの値です。

<!--
new topic that includes content from existing topics about samples and migration
-->
