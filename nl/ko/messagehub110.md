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

# Message Hub로 KSQL 사용
{: #ksql_using}

스트림 처리를 위해 {{site.data.keyword.messagehub}}와 함께 [KSQL ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/confluentinc/ksql){:new_window}을 사용할 수 있습니다. 다음 단계를 완료하십시오. 

1. {{site.data.keyword.messagehub}} KSQL 구성 파일을 작성하십시오. 

    예를 들어, 
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
    다음 행을 편집하여 고유한 데이터를 삽입해야 합니다.
	- <code>bootstrap.servers</code> - **서비스 신임 정보** 페이지에 나열된 모든 호스트를 삽입하십시오. 이 정보를 찾으려면
{{site.data.keyword.Bluemix_notm}}의 {{site.data.keyword.messagehub}} 인스턴스로 이동하고
**서비스 신임 정보** 탭으로 이동한 후 사용할 **신임 정보**를 선택하십시오. 
	- <code>sasl.jaas.config</code> - 고유한 사용자 이름 및 비밀번호 쌍을 삽입하십시오. 
	
2. {{site.data.keyword.Bluemix_notm}} 콘솔의 {{site.data.keyword.messagehub}} 대시보드를 사용하여 단일 파티션 및 기본 보존 기간이 포함된
<code>ksql__commands</code>라는 토픽을 작성하십시오. 
3. Docker 터미널에서 다음 명령을 사용하여 KSQL을 시작하십시오. 
<pre class="pre">/bin/ksql-cli local 
--<var class="keyword varname">properties-file</var> ./config/ksqlserver.properties
</pre>
4. 데이터를 채우려면 <code>ksql-examples</code> 프로젝트의 <code>io.confluent.ksql.datagen</code>에서 <code>DataGen</code> 클래스를 편집하십시오. 예를 들어, 
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
5. {{site.data.keyword.Bluemix_notm}} 콘솔의 {{site.data.keyword.messagehub}} 대시보드를 사용하여 하나의 파티션이 포함된 두 개의 토픽 즉,
<code>users</code> 및 <code>pageviews</code>를 작성하십시오.

    다음과 같이 <code>DataGen</code>을 시작하십시오. 
	
    i. <code>bootstrap-server=HOSTNAME:PORTNUMBER quickstart=users format=json topic=users maxInterval=10000</code>을 사용하여
<code>users</code> 이벤트 작성을 시작합니다. 
	
    ii. <code>bootstrap-server=HOSTNAME:PORTNUMBER quickstart=pageviews format=delimited topic=pageviews maxInterval=10000</code>을 사용하여
<code>pageviews</code> 이벤트 작성을 시작합니다. 
	
	<code>bootstrap-server</code>의 값으로 **서비스 신임 정보** 페이지에 나열된 모든 Kafka 호스트를 삽입해야 합니다. 이 정보를 찾으려면
{{site.data.keyword.Bluemix_notm}}의 {{site.data.keyword.messagehub}} 인스턴스로 이동하고
**서비스 신임 정보** 탭으로 이동한 후 사용할 **신임 정보**를 선택하십시오. 

이 단계를 완료한 경우
[KSQL 빠른 시작
안내서![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/confluentinc/ksql/tree/0.1.x/docs/quickstart#create-a-stream-and-table){:new_window}에 나열된 모든 조회를 실행할 수 있습니다. 

