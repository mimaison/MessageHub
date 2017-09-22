---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.messagehub}} に関するよくある質問
{: #faqs}

{{site.data.keyword.IBM}} {{site.data.keyword.messagehub}} サービスに関する一般的な質問と回答。

## Kafka offsets.retention.minutes のデフォルト値は何ですか?
{: #offsets notoc}
デフォルト値は 7 日間です。 

オフセット保存はシステム全体が対象であるため、個々のトピック・レベルで設定することはできません。すべてのコンシューマー・グループは、グループのトピックでのログ保存が最大 30 日に増やされた場合でも、7 日間のみの保管されたオフセットを取得します。 

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
