---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-05"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# 既知の制約事項
{: #restrictions}


## 各 {{site.data.keyword.Bluemix_notm}} スペースでの {{site.data.keyword.messagehub}} のインスタンス数
{: #instances_space notoc}

各 {{site.data.keyword.Bluemix_notm}} スペースで持つことができる {{site.data.keyword.messagehub}} インスタンスは 1 つのみです。

##トピックおよびパーティション
{: #topics_partitions notoc}

*  トピック名は最大 100 文字に制限されています。
*  トピックのデフォルトのパーティション数は 1 つです。
*  各 {{site.data.keyword.Bluemix_notm}} スペースのパーティションは 100 までに制限されています。それより多くのパーティションを作成するには、新しい {{site.data.keyword.Bluemix_notm}} スペースを使用する必要があります。

## メッセージの保存
{: #message_retention notoc}

デフォルトでは、Kafka ではメッセージは最大 24 時間保存され、各パーティションは 1 GB が上限です。この 1 GB という上限に達したら、この限界を超えないよう、最も古いメッセージが破棄されます。

ユーザー・インターフェースまたは管理 API のいずれかを使用して、トピックを作成するときにメッセージ保存の時間制限を変更できます。時間制限は、最小 1 時間、最大 30 日間です。

## Kafka でのトピックの作成および削除
{: #create_delete notoc}

Kafka では、トピックの作成および削除は非同期操作であり、完了するのに時間がかかることがあります。トピックの迅速な作成および削除に依存する使用パターンや、トピックの迅速な削除および再作成に依存する使用パターンを避けることをお勧めします。

## Kafka REST API
{: #trouble_rest notoc}

*  要求と応答では、バイナリー埋め込み形式のみがサポートされます。Avro 埋め込み形式はサポートされていません。
*  コンシューマー・インスタンスに同時要求はサポートされません。
コンシューマー・インスタンスに対応する読み取り、コミット、または削除の要求は、必ず、そのインスタンスの未完了要求の応答が受信されてから送信してください。


## Kafka REST API 速度制限
{: #kafka_rate notoc}

Kafka REST API を使用しているアプリケーションは、各 ApiKey の速度制限の対象となることがあります。この制限を超えると、API は次の HTTP エラーで応答します。

<code>429 Too Many Requests</code>
{:screen}

このエラーが表示されたら、待機してから要求を再サブミットしてください。

## Kafka REST API 日次再始動
{: #rest_restart notoc}

Kafka REST API は、短い期間中、1 日に一度再始動されます。この期間中には、Kafka REST API が利用不可になることがあります。これが起こった場合、要求を再試行することをお勧めします。REST API が再始動された後、Kafka コンシューマー・インスタンスの再作成が必要になります。この場合、REST API は次の JSON を返します。

```'{"error_code":40403,"message":"Consumer instance not found."}'
```
{:screen}

## Kafka ハイレベル・コンシューマー API
{: #kafka_consumer notoc}

Apache Kafka 0.8.2 の単純コンシューマー API または ハイレベル・コンシューマー API を {{site.data.keyword.messagehub}} で使用することはできません。代わりに、新しい Kafka 0.9 コンシューマー API を使用してください。
