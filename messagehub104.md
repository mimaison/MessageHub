---

copyright:
  years: 2015, 2018
lastupdated: "2017-08-03"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Using the Kafka Java client
{: #kafka_using}

## How to use, download, and run the Java Kafka API sample
{: notoc}

The Java&trade; Kafka API sample is an example producer and consumer that is written in Java, which directly uses the Kafka API. You can run this sample locally or in {{site.data.keyword.Bluemix_short}}.

The sample code is in the [message-hub-samples GitHub project ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}. Although the sample uses
the Kafka API to send and receive messages, the sample uses the {{site.data.keyword.messagehub}} Administration API to create the topic it sends messages to and receives messages from.

For more information about the setup and running of the sample, see the [README.md ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}.

For a detailed walkthrough of how to run the sample, see [Getting started with {{site.data.keyword.messagehub}}](/docs/services/MessageHub/index.html#getting_started_steps).

## How to use, download, and run the Liberty for Java sample
{: #liberty_sample notoc}

The Liberty for Java sample implements a simple application that is deployed onto the Liberty runtime. The application uses the Kafka API for {{site.data.keyword.messagehub}} to produce and consume messages.
The application also serves up a web front end that you can use for administration.

You can find the sample code in the [message-hub-samples GitHub project ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-liberty-sample){:new_window}.

## How to migrate the Kafka client from 0.9.x to 0.10.x
{: #kafka_migrate notoc}


If you're using the Java clients, you can now use
the publicly available 0.10.x Kafka clients. You are strongly encouraged to move from 0.9.x to the
latest 0.10.x version (currently 0.10.2.1). Complete the following steps:

1. Delete the {{site.data.keyword.messagehub}} login jar module.
2. Change your <code>jaas.conf</code> file to the following:
    ```
        KafkaClient {
          org.apache.kafka.common.security.plain.PlainLoginModule required
          serviceName="kafka"
            username="<your username>"
            password="<your password>";
        };
    ```
    {: codeblock}

3. Add this line to your consumer and producer properties: <code>sasl.mechanism=PLAIN</code>

<!--
17/10/17 - Karen: following info duplicated at messagehub063 
-->

## Using the sasl.jaas.config property
{: #sasl_prop notoc}
If you're using a Kafka client at 0.10.2.1 or later, you can use the <code>sasl.jaas.config</code> property for client configuration instead of a JAAS file. To connect to {{site.data.keyword.messagehub}}, set <code>sasl.jaas.config</code> as follows:
<pre>
<code>    sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required \
    username="USERNAME" \
    password="PASSWORD";</code>
</pre>
{:codeblock}

where USERNAME and PASSWORD are the values from your {{site.data.keyword.messagehub}} **Service Credentials** tab in {{site.data.keyword.Bluemix_notm}}.

If you use <code>sasl.jaas.config</code>, clients running in the same JVM can use different credentials. For more information, see
[Configuring Kafka clients ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://kafka.apache.org/documentation/#security_sasl_plain_clientconfig){:new_window}

For an earlier Kafka client, you must use a JAAS configuration file to specify the credentials. This mechanism is less convenient therefore we recommend using the <code>sasl.jaas.config</code> property instead.

<!-- 
17/10/17 - Karen: following info duplicated at messagehub108
 -->

## APIs for topic administration
{: #topic_admin notoc}

If you're using a Kafka client at 0.11 or later, or Kafka Streams at 0.10.2.0 or later, you can use APIs to create and delete topics. We've put some restrictions on the settings allowed when you create topics. Currently, you can modify the following settings only:

<dl>
<dt>cleanup.policy</dt>
<dd>Set to <code>delete</code> (default), <code>compact</code> or <code>delete,compact</code></dd>
<dt>retention.ms</dt>
<dd>The default retention period is 24 hours. The minimum is 1 hour and the maximum is
30 days. Specify this value as multiples of hours.

<p>**Note:**
If the cleanup policy is <code>compact</code> only, we automatically add <code>delete</code> but disable deletion based on time. Messages in the topic are compacted up to 1 GB before being deleted.</p>
</dd>
</dl>

<!--
new topic that includes content from existing topics about samples and migration
-->
