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

# {{site.data.keyword.messagehub}} での {{site.data.keyword.mql}} API の有効化
{: #mql_enable}


**この API を使用するには、その前に「MQLight」という名前の Kafka トピックを明示的に作成する必要があります。これは、すべてのメッセージが「MQLight」トピックを経由するためです。このトピックのパーティションは 1 つでなければなりません。このトピックを作成すると、サービス・インスタンスに対して MQ Light API が有効になります。**  {{site.data.keyword.messagehub}} でのトピックの作成方法について詳しくは、[トピックの管理](/docs/services/MessageHub/messagehub070.html)を参照してください。

「MQLight」トピックは、MQ Light API によって、メッセージ・データを保管するため、および他の Kafka クライアントと対話するために使用されます。このトピックが作成されると、サービス支払いプランに概説されている標準レートで課金が発生することに注意してください。

MQ Light API を無効にするには、「MQLight」トピックを削除します。トピックを削除するとすべてのデータが破棄されることに注意してください。
