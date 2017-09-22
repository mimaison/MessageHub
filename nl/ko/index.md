---

copyright:
  years: 2015, 2017
lastupdated: "2017-03-02"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Message Hub 시작하기
{: #messagehub}


{{site.data.keyword.messagehub_full}}는 온프레미스 및 오프프레미스 클라우드 기술을 통합하는 확장 가능하고, 분산된, 처리량이 많은 메시지 버스입니다.
{:shortdesc}

{{site.data.keyword.messagehub}}를 사용하여 다음 태스크를 완료할 수 있습니다. 

* 오픈 프로토콜을 사용하여 마이크로서비스를 서로 연결
* 강력한 통찰을 실현하기 위해 스트림 데이터를 분석에 연결
* 실시간으로 대응할 수 있도록 이벤트 데이터를 여러 애플리케이션에 제공

예를 들어, {{site.data.keyword.messagehub}}를 사용하여
인벤토리 변경사항을 공개하고, 실시간 데이터를 위한 중앙 집중식 버스를 작성하거나
백엔드 작업자 프로세스에 작업을 오프로드하도록 앱을 사용으로 설정할 수 있습니다. 

{{site.data.keyword.messagehub}}를 시작하여
메시지 전송 및 수신을 시작하려면 Java™ 샘플을 사용하십시오. 샘플에서는 제작자가 토픽을 사용하여
이용자에게 메시지를 보내는 방법을 보여줍니다. 메시지를 이용하고 메시지를 생성하는 데 동일한 샘플 프로그램이 사용됩니다. 

![Java 샘플 개요 다이어그램](getting_started_sample.gif "메시지의 플로우를 보여주는 Java 샘플의 개요 다이어그램.")


다음 단계를 완료하십시오.
{: #getting_started_steps}
 
1. {{site.data.keyword.messagehub}} 서비스 인스턴스를 작성하십시오. 

  a. 웹 사용자 인터페이스를 사용하여 {{site.data.keyword.Bluemix_notm}}에 로그인하십시오. 
  
  b. **카탈로그**를 클릭하십시오. 
  
  c. **애플리케이션 서비스** 섹션에서 **{{site.data.keyword.messagehub}}**를 클릭하십시오. {{site.data.keyword.messagehub}} 서비스 인스턴스 페이지가 열립니다.
  
  d. **연결 대상** 메뉴에서 서비스를 바인딩되지 않은 상태로 두고 사용자의 서비스 및 신임 정보에 대한 이름을 입력하십시오. 기본값을 사용할 수 있습니다.
  
  e. **작성**을 클릭하십시오. 

2. 아직 설치되어 있지 않다면, 다음 필수 소프트웨어를 설치하십시오. 

    * [git ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://git-scm.com/){:new_window}
	* [Gradle ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://gradle.org/){:new_window}
    * Java 7 이상
 
3. 명령행에서 다음 명령을 실행하여 message-hub-samples git 저장소를 복제하십시오. 

    <pre class="pre">
    git clone https://github.com/ibm-messaging/message-hub-samples.git
    </pre>
	{: codeblock}

4. 다음 명령을 실행하여 java 콘솔 샘플로 디렉토리를 변경하십시오. 

    <pre class="pre">
    cd message-hub-samples/kafka-java-console-sample
    </pre>
	{: codeblock}

5. 다음 빌드 명령을 실행하십시오. 

    <pre class="pre">
    gradle clean && gradle build
    </pre>
	{: codeblock}

6. 다음 명령을 실행하여 콘솔에서 이용자를 시작하십시오. 

    <pre class="pre">java -jar build/libs/kafka-java-console-sample-2.0.jar 
	<var class="keyword varname">kafka_brokers_sasl</var> <var class="keyword varname">kafka_admin_url</var> <var class="keyword varname">api_key</var> -consumer</pre>
    {: codeblock}
    
    샘플은 `kafka-java-console-sample-topic`으로 이름 지정된 토픽을 사용합니다. 토픽이 아직 존재하지 않는 경우,
    샘플은 {{site.data.keyword.messagehub}} 관리 API를 사용하여 토픽을 작성합니다. 메시지를 전송 및 수신하기 위해
    샘플은 Apache Kafka Java API를 사용합니다.

    *kafka_brokers_sasl*, *kafka_admin_url*
    및 *api_key*에 대한 값을 찾으려면 {{site.data.keyword.Bluemix_notm}}의 {{site.data.keyword.messagehub}} 인스턴스로 이동하여 **서비스 신임 정보** 탭으로 이동한 후 사용하려는 **신임 정보**를 선택하십시오. 
    
	**중요:** *kafka_brokers_sasl*은 단일 문자열이어야 하며 따옴표로 묶어야 합니다. 예:

    <pre class="pre">
    "host1:port1,host2:port2"
    </pre>
	{: codeblock}

    선택한 **신임 정보**에 나열된 모든 Kafka 호스트 사용을 권장합니다. 

7. 다음 명령을 실행하여 콘솔에서 제작자를 시작하십시오. 
   
    <pre class="pre">java -jar build/libs/kafka-java-console-sample-2.0.jar
	<var class="keyword varname">kafka_brokers_sasl</var> <var class="keyword varname">kafka_admin_url</var> <var class="keyword varname">api_key</var> -producer</pre>
 {: codeblock}
  
8. 이제 이용자에 표시되는 제작자가 보낸 메시지를 볼 수 있습니다. 일부 샘플 출력은 다음과 같습니다. 

    ```
    [2016-11-30 17:30:53,492] INFO Running in local mode. (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:53,492] INFO Updating JAAS configuration (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:53,506] INFO Kafka Endpoints: kafka01-prod01.messagehub.services.us-south.bluemix.net:9093,kafka02-prod01.messagehub.services.us-south.bluemix.net:9093,kafka03-prod01.messagehub.services.us-south.bluemix.net:9093,kafka04-prod01.messagehub.services.us-south.bluemix.net:9093,kafka05-prod01.messagehub.services.us-south.bluemix.net:9093 (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:53,506] INFO Admin REST Endpoint: https://kafka-admin-prod01.messagehub.services.us-south.bluemix.net:443 (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:53,506] INFO Creating the topic kafka-java-console-sample-topic (com.messagehub.samples.MessageHubConsoleSample)
    (com.messagehub.samples.MessageHubConsoleSample)e :{}
    [2016-11-30 17:30:54,947] INFO Admin REST Listing Topics: [{"name":"kafka-java-console-sample-topic","partitions":1,"retentionMs":"86400000","markedForDeletion":false}] (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:55,952] INFO [Partition(topic = kafka-java-console-sample-topic, partition = 0, leader = 0, replicas = [0,1,4,], isr = [0,4,1,]] (com.messagehub.samples.ConsumerRunnable)
    [2016-11-30 17:30:55,953] INFO class com.messagehub.samples.ConsumerRunnable is starting. (com.messagehub.samples.ConsumerRunnable)
    [2016-11-30 17:30:57,023] INFO [Partition(topic = kafka-java-console-sample-topic, partition = 0, leader = 0, replicas = [0,1,4,], isr = [0,4,1,]] (com.messagehub.samples.ProducerRunnable)
    [2016-11-30 17:30:57,024] INFO MessageHubConsoleSample will run until interrupted. (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:57,024] INFO class com.messagehub.samples.ProducerRunnable is starting. (com.messagehub.samples.ProducerRunnable)
    [2016-11-30 17:30:58,018] INFO Message produced, offset: 0 (com.messagehub.samples.ProducerRunnable)
    [2016-11-30 17:30:58,956] INFO No messages consumed (com.messagehub.samples.ConsumerRunnable)
    [2016-11-30 17:31:00,301] INFO Message consumed: ConsumerRecord(topic = kafka-java-console-sample-topic, partition = 0, offset = 1, CreateTime = 1480527060022, checksum = 1906962734, serialized key size = 3, serialized value size = 25, key = key, value = This is a test message #1) (com.messagehub.samples.ConsumerRunnable)
    [2016-11-30 17:31:00,397] INFO Message produced, offset: 1 (com.messagehub.samples.ProducerRunnable)
    [2016-11-30 17:31:02,550] INFO Message consumed: ConsumerRecord(topic = kafka-java-console-sample-topic, partition = 0, offset = 2, CreateTime = 1480527062401, checksum = 3801731428, serialized key size = 3, serialized value size = 25, key = key, value = This is a test message #2) (com.messagehub.samples.ConsumerRunnable)
    ```
	{: codeblock}
	
9. 샘플은 사용자가 중지할 때까지 계속 실행됩니다. 프로세스를 중지하려면 <code>Ctrl+C</code>와 같은 명령을 실행하십시오.


Python을 사용하여 {{site.data.keyword.messagehub}} 샘플 실행에 대해 자세히 알아보려면 [Python 콘솔 샘플 애플리케이션 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/messaging/2017/02/09/new-message-hub-sample-python-console-application/){:new_window}을 참조하십시오. 
[{{site.data.keyword.messagehub}} 샘플 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/ibm-messaging/message-hub-samples){:new_window}에서 다른 API 및 기능을 보여주는 샘플을 찾아볼 수도 있습니다.

{{site.data.keyword.messagehub}}에 대해 Java 샘플 실행을 안내하는 동영상을 보려면 [{{site.data.keyword.messagehub}} - Getting started with IBM's Kafka in the cloud ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.youtube.com/watch?v=tt-bLtFzC_4){:new_window}를 참조하십시오.

