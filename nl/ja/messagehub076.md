---

copyright:
  years: 2015, 2017
lastupdated: "2016-11-22"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.mql}} API を使用する理由
{: #why_mql}

{{site.data.keyword.mql}} API は、Kafka API よりも高いレベルの抽象化を提供します。{{site.data.keyword.mql}} は、キューおよびパブリッシュ/サブスクライブの両メッセージ・パターンをサポートする統一メッセージング・モデルでアプリを素早くポータブルに作成することを可能にします。
{:shortdesc}

アプリは、動的に作成される宛先を使用してメッセージを交換します。
宛先は、階層的に構成する (例えば、<code>‘/sports/football’</code>)、ワイルドカードを使用してグループ化する (例えば、
<code>‘/sports/#’</code>) ことができ、送達保証とメッセージ期限についての単純な制御機能を持たせることもできます。
これを利用して、ワーカーの負荷軽減、イベント通知、およびバッチ処理などのシナリオを容易に実装できます。

{{site.data.keyword.mql}} API を使用して他のアプリとの間でメッセージを送信するだけでなく、Kafka REST API または Kafka API を使用するアプリともメッセージを交換できます。あるいは、{{site.data.keyword.IBM}} MQ でオンプレミスのアプリを使用することもできます。

