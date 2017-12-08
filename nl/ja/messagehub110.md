---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-26"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Message Hub での KSQL の使用
{: #ksql_using}

ストリーム処理のために、[KSQL ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/confluentinc/ksql){:new_window} を {{site.data.keyword.messagehub}} と共に使用できます。以下のステップを実行してください。

1. {{site.data.keyword.messagehub}} KSQL 構成ファイルを作成します。

    以下に例を示します。
    ```
    bootstrap.servers=HOSTNAME:PORTNUMBER
    application.id=ksql_server_quickstart
    ksql.command.topic.suffix=commands
    listeners=http://localhost:8080
    security.protocol=SASL_SSL
    sasl.mechanism=PLAIN
    ssl.protocol=TLSv1.2
    ssl.enabled.protocols=TLSv1.2
    sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required username="USERNAME" password="PASSWORD";
    ksql.sink.replications.default=3
    ```
    以下の行を編集して自分のデータを挿入してください。
	- <code>bootstrap.servers</code> -**「サービス資格情報」**ページにリストされているすべての Kafka ホストを挿入します。この情報を調べるには、{{site.data.keyword.Bluemix_notm}} で {{site.data.keyword.messagehub}} インスタンスに移動し、
**「サービス資格情報」**タブに進み、使用する**資格情報**を選択します。

	- <code>sasl.jaas.config</code> - 自分のユーザー名とパスワードのペアを挿入します。
	
2. {{site.data.keyword.Bluemix_notm}} コンソール内の {{site.data.keyword.messagehub}} ダッシュボードを使用して、単一パーティションとデフォルトの保存期間を使って <code>ksql__commands</code> という名前のトピックを作成します。
3. Docker 端末から、次のコマンドを使用して KSQL を開始します。
<pre class="pre">/bin/ksql-cli local 
--<var class="keyword varname">properties-file</var> ./config/ksqlserver.properties
</pre>
4. データを追加するには、<code>ksql-examples</code> プロジェクトの <code>io.confluent.ksql.datagen</code> 内の <code>DataGen</code> クラスを編集します。以下に例を示します。
```
     Properties props = new Properties();
     props.put("bootstrap.servers", arguments.bootstrapServer);
     props.put("client.id", "KSQLDataGenProducer");
     props.put("security.protocol", "SASL_SSL");
     props.put("sasl.mechanism", "PLAIN");
     props.put("ssl.protocol", "TLSv1.2");
     props.put("ssl.enabled.protocols", "TLSv1.2");
     props.put("sasl.jaas.config", "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"USERNAME\" password=\"PASSWORD\";"); 
```
    {: codeblock}
5. {{site.data.keyword.Bluemix_notm}} コンソール内の {{site.data.keyword.messagehub}} ダッシュボードを使用して、それぞれに 1 つのパーティションがある 2 つのトピック、<code>users</code> と <code>pageviews</code> を作成します。

    その後、次のように <code>DataGen</code> を 2 回開始します。
	
    i. <code>bootstrap-server=HOSTNAME:PORTNUMBER quickstart=users format=json topic=users maxInterval=10000</code> によって、<code>users</code> イベントの作成を開始します。
	
    ii. <code>bootstrap-server=HOSTNAME:PORTNUMBER quickstart=pageviews format=delimited topic=pageviews maxInterval=10000</code> によって、<code>pageviews</code> イベントの作成を開始します。
	
	**「サービス資格情報」**ページにリストされたすべての Kafka ホストを <code>bootstrap-server</code> の値として挿入してください。この情報を調べるには、{{site.data.keyword.Bluemix_notm}} で {{site.data.keyword.messagehub}} インスタンスに移動し、**「サービス資格情報」**タブに進み、使用する**資格情報**を選択します。

これらの手順を完了すると、[KSQL Quick Start Guide ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/confluentinc/ksql/tree/0.1.x/docs/quickstart#create-a-stream-and-table){:new_window} にリストされたすべての照会を実行できます。

