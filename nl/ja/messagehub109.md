---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-19"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}



# {{site.data.keyword.messagehub}} チームへの問題の報告
{: #report_problem}

{{site.data.keyword.messagehub}} で問題が起こった場合、最初に [{{site.data.keyword.Bluemix_notm}} 状況ページ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/status){:new_window} を確認してください。 

{{site.data.keyword.messagehub}} チームから支援を受けたい場合は、以下の情報をできるだけ多く収集してください。
{:shortdesc}

1. {{site.data.keyword.messagehub}} のインスタンスがプロビジョンされているのはどの {{site.data.keyword.Bluemix_notm}} 地域ですか? 例えば、米国南部または英国です。 
2. どのインターフェースで問題が起きていますか? REST、Kafka、AMQP、またはブリッジのどれですか?
3. 問題が最初に起こったのはいつですか (時刻、日付、タイム・ゾーンを具体的に)? それまでにアプリケーションはどのくらい長く実行されていましたか?
4. 問題は引き続き発生していますか? 再生成できますか?
5. 使用している {{site.data.keyword.messagehub}} サービスのインスタンス ID は?
この ID は、サービスの VCAP_SERVICES JSON 内の "instance_id" フィールドで確認できます。
6. アプリケーションは Kafka クライアントと REST クライアントのどちらを使用していますか? バージョンの詳細は?
7. クライアント構成の詳細は?
8. 問題が示されているアプリケーション・ログ・スニペットがありますか?
9. 発生している問題は何ですか? 影響を受けるトピック、クライアント ID、およびグループ ID は?
10. あなたのサービスへの問題の影響は?


収集した情報は、[サポート要求を送信する ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/support/index.html#open-ticket) ことにより、サポート・チケットとして IBM に提出することができます。










