---

copyright:
  years: 2015, 2017
lastupdated: "2017-01-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 3 つの API からの選択
{: #choose_api}

{{site.data.keyword.messagehub}} は 3 つの API をサポートします。ここでは、最適な API を選択する際に役立つ情報を示します。

## Kafka API を使用する理由
{: #why_kafka notoc}

{{site.data.keyword.messagehub}} で提供されている他のインターフェースよりも Kafka API を使用することを選択するのにはいくつかの理由があります。これらの理由としては以下のようなものがあります。
{:shortdesc}


* Kafka サポートがある既存のシステム (例えば、{{site.data.keyword.IBM}} {{site.data.keyword.streaminganalyticsshort}} および {{site.data.keyword.sparks}}) にアプリを統合するのが容易です。
* 他の API より待ち時間が短く、高いスループットが提供されます。
* Kafka REST API より優れた API が提供されます。


## {{site.data.keyword.mql}} API を使用する理由
{: #why_mql notoc}

{{site.data.keyword.mql}} API は、Kafka API よりも高いレベルの抽象化を提供します。{{site.data.keyword.mql}} は、キューおよびパブリッシュ/サブスクライブの両メッセージ・パターンをサポートする統一メッセージング・モデルでアプリを素早くポータブルに作成することを可能にします。
{:shortdesc}

アプリは、動的に作成される宛先を使用してメッセージを交換します。
宛先は、階層的に構成する (例えば、<code>‘/sports/football’</code>)、ワイルドカードを使用してグループ化する (例えば、
<code>‘/sports/#’</code>) ことができ、送達保証とメッセージ期限についての単純な制御機能を持たせることもできます。
これを利用して、ワーカーの負荷軽減、イベント通知、およびバッチ処理などのシナリオを容易に実装できます。

{{site.data.keyword.mql}} API を使用して他のアプリとの間でメッセージを送信するだけでなく、Kafka REST API または Kafka API を使用するアプリともメッセージを交換できます。あるいは、{{site.data.keyword.IBM_notm}} MQ でオンプレミスのアプリを使用することもできます。


## Kafka REST API を使用する理由
{: #why_rest notoc}

Kafka REST API は、以下のシチュエーションで使用できる便利なインターフェースです。


* 開発者が {{site.data.keyword.messagehub}} を使用してすぐに開始したい場合
* 待ち時間は重要なファクターではなく、スループットが低い一部のユース・ケース
* デバッグおよび障害検出の目的

Kafka REST API は、スループットが高く待ち時間が短いインターフェースを目的としたものではありません。
こうしたタイプの要件がある場合、Kafka API を使用して {{site.data.keyword.messagehub}} と相互に接続することをお勧めします。詳細については、[Kafka クライアントの使用](/docs/services/MessageHub/messagehub050.html#kafka_client)を参照してください。












