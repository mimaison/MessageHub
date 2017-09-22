---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# ブリッジの使用による他のサービスへのリンク
{: #bridges}

ブリッジは、{{site.data.keyword.messagehub}} と別のサービスとの間の単一方向のリンクです。ブリッジによって、{{site.data.keyword.messagehub}} からデータを読み取って別のサービスに書き込むか、または、別のサービスからデータを読み取って {{site.data.keyword.messagehub}} に書き込むことが可能になります。
{:shortdesc}

{{site.data.keyword.messagehub}} ブリッジを使用することの主な利点は次のとおりです。  

* ブリッジを管理的に定義できるため、アプリケーション・コードを書く必要がありません。
* 各ブリッジのライフサイクルは、{{site.data.keyword.messagehub}} サービスによってモニターおよび管理されます。例えば、あるブリッジでエラーが発生した場合、そのブリッジは {{site.data.keyword.messagehub}} によって自動的に再始動されます。
* ブリッジは {{site.data.keyword.Bluemix_short}} プラットフォームと統合されます。例えば、ブリッジによって生成されたロギングおよびモニタリング情報は、Kibana ダッシュボードおよび Grafana ダッシュボードに転送されます。

ブリッジが役立つ一般的なシナリオとして次の 2 つがあります。

* 1 つ以上のデータ・ソースから {{site.data.keyword.messagehub}} へデータを取り込む。
* {{site.data.keyword.messagehub}} から別のサービス (例えば、長期保管) へデータを転送する。

## {{site.data.keyword.messagehub}} ブリッジ
{: notoc}

* 以下の 2 つのタイプのブリッジが提供されています。 
  - {{site.data.keyword.objectstorageshort}} ブリッジ。これは、{{site.data.keyword.messagehub}} データを [Object Storage サービス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/services/ObjectStorage/index.html){:new_window} のインスタンスへ転送します。
  - MQ ブリッジ。これは、{{site.data.keyword.IBM}} MQ からメッセージ・データを取り出し、{{site.data.keyword.messagehub}} のトピックへ転送します。将来は、より広範囲のブリッジのサポートが予定されています。
* 現在のところ、ブリッジはすべての {{site.data.keyword.Bluemix_notm}} パブリック環境で使用可能です。{{site.data.keyword.Bluemix_short}} Dedicated ではブリッジは使用可能ではありません。
* 次の 2 つの方法でブリッジを管理できます。
  - 既存 {{site.data.keyword.messagehub}} 管理 API の拡張である [REST API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/ibm-messaging/message-hub-docs){:new_window} を使用する。curl を使用してブリッジのライフサイクルを管理する方法の例が [message-hub-docs ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/ibm-messaging/message-hub-docs){:new_window} にあります。ブリッジの開発は継続中であるため、この REST API は変更される可能性があります。この API は安定化される予定です。
  - {{site.data.keyword.Bluemix_notm}} コンソールで {{site.data.keyword.messagehub}} ダッシュボードを使用する。
* 任意のタイプの最大 2 つのブリッジを、{{site.data.keyword.messagehub}} サービスの 1 つのインスタンスと関連付けることができます。ブリッジの開発は継続中であるため、この制限は引き続き検討の対象となります。
* ブリッジでのメッセージング操作以外にはブリッジ使用に対する追加料金はありません。
* {{site.data.keyword.objectstorageshort}} ブリッジは、データを {{site.data.keyword.objectstorageshort}} に書き込むときに、区切り文字として改行文字を使用してメッセージを連結します。したがって、改行文字が埋め込まれたメッセージおよびバイナリー・メッセージ・データには、このブリッジは不適切です。
* {{site.data.keyword.objectstorageshort}} ブリッジによって現在使用されているオブジェクト命名規則は、将来変更される可能性があります。
* MQ ブリッジは、データがブリッジと MQ キュー・マネージャーとの間で転送されるときに、データのプライバシーおよび保全性を保護するための SSL/TLS の使用をサポートしていません。SSL/TLS 使用のサポートがブリッジに追加される計画があります。 

しかし、[{{site.data.keyword.SecureGatewayfull}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/services/SecureGateway/secure_gateway.html){:new_window} サービスを使用して、{{site.data.keyword.Bluemix_notm}} とオンプレミスにインストールできる {{site.data.keyword.SecureGateway}} クライアントとの間のセキュア・トンネルを介してデータを送信することができます。この構成では、トンネルのどちらの終端でも通信は SSL/TLS を使用して保護されてはいません。
