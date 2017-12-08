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

# {{site.data.keyword.messagehub}} に関するよくある質問
{: #faqs}

{{site.data.keyword.IBM}} {{site.data.keyword.messagehub}} サービスに関する一般的な質問と回答。

<!--17/10/17 - Karen: same info duplicated at messagehub104 -->
## Kafka API を使用してトピックの作成と削除を行うにはどうしたらよいか?
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

## {{site.data.keyword.messagehub}} がコンシューマー・オフセット・トピックのためにログ保存ウィンドウを設定する期間はどれだけの長さか?
{: #offsets notoc}
{{site.data.keyword.messagehub}} はコンシューマー・オフセットを 7 日間保存します。これは Kafka 構成 offsets.retention.minutes に対応します。 

オフセット保存はシステム全体が対象であるため、個々のトピック・レベルで設定することはできません。すべてのコンシューマー・グループは、ログ保存を最大 30 日に増やしたトピックを使用する場合でも、保管されるオフセットは 7 日間のみです。 

## {{site.data.keyword.messagehub}} の可用性の性質は?
{: #availability notoc}

{{site.data.keyword.messagehub}} アプリケーションを作成する場合、以下の情報を使用して、{{site.data.keyword.messagehub}} の通常の可用性がどのような性質なのか、および、アプリケーションに要求される処理内容を理解してください。

### API
{: #api_availability notoc}

{{site.data.keyword.messagehub}} の通常の操作の一環として、Kafka クラスターのノードが再始動されることがあります。
場合によっては、クラスターがリソースを再割り当てすると、アプリケーションはそれを認識します。そういった変更に対して回復的であり、再接続して操作を再試行できるように、アプリケーションを作成してください。

### {{site.data.keyword.messagehub}} ブリッジ
{: #bridge_availability notoc}

ブリッジが再始動する可能性を処理できるようにアプリケーションを作成してください。
