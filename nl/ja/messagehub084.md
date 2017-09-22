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

# 0.9.x から 0.10.x への Kafka クライアントのマイグレーション方法
{: #kafka_migrate}


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


