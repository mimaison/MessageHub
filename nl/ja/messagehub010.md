---

copyright:
  years: 2015, 2017
lastupdated: "2017-02-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Message Hub について
{: #about}

{{site.data.keyword.messagehub_full}} は、アプリケーションおよびサービスが簡単かつ信頼できる方法で通信することを可能にする、スケーラブルで高スループットの分散型のメッセージング・サービスです。
{:shortdesc}

{{site.data.keyword.messagehub}} では、アプリケーションはメッセージを作成してトピックに送信することによって、データを送信します。メッセージを受信するには、アプリケーションはトピックをサブスクライブし、アプリケーションがトピックのメッセージをすべて受信するのか、アプリケーション間でメッセージを共有するのかのいずれかを選択します。
{{site.data.keyword.messagehub}} は、特定の順序でメッセージのホストと保守を行います。従来型のメッセージング・システムとは対照的に、{{site.data.keyword.messagehub}} は、トピックを提供しますが、キューは提供しません。ただし、{{site.data.keyword.messagehub}} では、受信するアプリケーション間でメッセージを共有する方法があり、それを使用すると動作はキューと似たものになります。

{{site.data.keyword.messagehub}} を使用することによって、以下のタスクを実行できます。

* マイクロサービス同士をつなぐ。
* バックエンド・ワーカー・プロセスに分担させることで負荷を軽減する。
* ストリーム・データを Analytics に接続して強力な洞察を実現する
* イベント・データを複数のアプリケーションにパブリッシュしてリアルタイムに対応する。
* 別のサービス (例えば、長期保管) にデータを転送する。
