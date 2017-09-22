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

# MQ Light API について、および他の API との違い
{: #mqlight}

{{site.data.keyword.mql}} API は、Kafka に比べて、より高いレベルでのメッセージングの抽象化を提供します。これによって、習得が容易になり、アプリケーションでの使用がより簡単になります。
{:shortdesc}

Kafka クライアントと {{site.data.keyword.mql}} API のどちらを使用するのかの選択は、構築したいメッセージング・トポロジーに基づきます。

* Kafka を使用する場合は、少数のトピックを使用し、スケーラビリティーを高めるために各トピックに複数のパーティションを含めることが可能です。コンシューマー・グループを使用することによってコンシューマー間でメッセージを共有できますが、各コンシューマーは、割り当てられたパーティションでメッセージ速度に遅れずに対応できなければなりません。
* {{site.data.keyword.mql}} API を使用する場合は、ずっと多くのトピックを使用でき、トピック名は階層的です (例: <code>‘/sports/football’</code> および <code>‘/sports/tiddlywinks’</code>)。コンシューマー間でのメッセージの共有は、より簡単です。

{{site.data.keyword.mql}} API のトピックは、Kafka トピックと同じではありません。そうではなく、{{site.data.keyword.mql}} API は「MQLight」という名前の単一の Kafka トピックを使用し、{{site.data.keyword.mql}} API を使用して送受信されるすべてのメッセージはこの 1 つの Kafka トピックを経由します。

{{site.data.keyword.mql}} が使用可能な {{site.data.keyword.Bluemix_notm}} 地域は、米国南部、英国、およびシドニーのみです。MQ Light API は、ドイツ地域および {{site.data.keyword.Bluemix_notm}} Dedicated では使用不可です。

<!-- begin PRODUCTION ONLY -->
どの API を使用するのかの選択について詳しくは、[Kafka API を使用する理由](/docs/services/MessageHub/messagehub054.html)、[MQ Light API を使用する理由](/docs/services/MessageHub/messagehub076.html)、および [Kafka REST API を使用する理由](/docs/services/MessageHub/messagehub065.html)を参照してください。
<!-- end PRODUCTION ONLY -->
