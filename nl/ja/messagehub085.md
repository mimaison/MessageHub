---

copyright:
  years: 2015, 2017
lastupdated: "2017-02-08"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Bluemix Public 環境と Bluemix Dedicated 環境での Message Hub の相違点
{: #public_dedicated}

{{site.data.keyword.Bluemix}} は、アプリケーションをビルド、実行、および管理するためのクラウド・ベースのオープン標準プラットフォームです。{{site.data.keyword.Bluemix_notm}} は、パブリック・デプロイメント・モデルと専用デプロイメント・モデルを提供します。{{site.data.keyword.messagehub}} は、両方の環境で使用可能です。

## {{site.data.keyword.Bluemix_notm}} Public 環境
{: notoc}

{{site.data.keyword.Bluemix_notm}} Public は、使用量に応じて支払い、他のユーザーとインフラストラクチャーを共有する、経済的なパブリック・クラウド・サービスを提供します。

{{site.data.keyword.Bluemix_notm}} Public では、{{site.data.keyword.messagehub}} のコストは 2 つの要因で決まります。1 つは使用するパーティションの数、もう 1 つは送受信するメッセージの数です。トピックに保持されている間はメッセージ・データに対する課金はありませんが、各パーティションで保持されるデータには 1 GB までという上限があります。

詳しくは、[{{site.data.keyword.Bluemix_notm}} Public ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud-computing/bluemix/public){:new_window} を参照してください。


## {{site.data.keyword.Bluemix_notm}} Dedicated 環境
{: notoc}

{{site.data.keyword.Bluemix_notm}} Dedicated は、より隔離された環境を提供します。インフラストラクチャーは共有されず、{{site.data.keyword.IBM_notm}} によって管理される個別 SoftLayer アカウントでホストされます。この環境は、{{site.data.keyword.Bluemix_notm}} Public およびユーザー独自のネットワークに安全に接続されます。

{{site.data.keyword.messagehub}} の専用インスタンスでは、使用量に対してではなく、サービスに対して支払います。すべての組織とスペースを含めた環境全体で、最大 75 個のパーティションを持つことができます。クラスターでスペースが不足することがないように、各パーティションの上限は 10 GB になっています。

当サービスをモニターするための Kibana ダッシュボードおよび Grafana ダッシュボードは、{{site.data.keyword.Bluemix_notm}} Dedicated ではサポートされていません。

詳しくは、[{{site.data.keyword.Bluemix_notm}} Dedicated ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ibm.com/cloud-computing/bluemix/dedicated/){:new_window} を参照してください。


