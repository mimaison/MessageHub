---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-08"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Kafka Java client properties and APIs
{: #kafka_using_props}


## Using the sasl.jaas.config property
{: #sasl_prop notoc}
If you're using a Kafka client at 0.10.2.1 or later, you can use the ```sasl.jaas.config``` property for client configuration instead of a JAAS file. To connect to {{site.data.keyword.messagehub}}, set ```sasl.jaas.config``` as follows:
<pre>
<code>    sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required \
    username="USERNAME" \
    password="PASSWORD";</code>
</pre>
{:codeblock}

where USERNAME and PASSWORD are the values from your {{site.data.keyword.messagehub}} **Service Credentials** tab in {{site.data.keyword.Bluemix_notm}}.

If you use ```sasl.jaas.config```, clients running in the same JVM can use different credentials. For more information, see
[Configuring Kafka clients ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://kafka.apache.org/documentation/#security_sasl_plain_clientconfig){:new_window}

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

## Support for Kafka Streams
{: #kafka_streams notoc}

Starting from the Streams library 0.10.2.0, the topic APIs now work with {{site.data.keyword.messagehub}} with no setup required. Specify your SASL credentials using ```sasl.jaas.config``` or a JAAS file and set ```replication.factor``` to 3.

For example:

<pre>
<code>
    props.put(StreamsConfig.REPLICATION_FACTOR_CONFIG, "3");
    props.put(StreamsConfig.BOOTSTRAP_SERVERS_CONFIG, BOOTSTRAP_SERVERS);
    props.put("security.protocol","SASL_SSL");
    props.put("sasl.mechanism","PLAIN");
    props.put("ssl.protocol","TLSv1.2");
    props.put("ssl.enabled.protocols","TLSv1.2");
    props.put("sasl.jaas.config","org.apache.kafka.common.security.plain.PlainLoginModule required username=\"USERNAME\" password=\"PASSWORD\";");
</code>
</pre>
{:codeblock}

where BOOTSTRAP_SERVERS, USERNAME, and PASSWORD are the values from your {{site.data.keyword.messagehub}} **Service Credentials** tab in
{{site.data.keyword.Bluemix_notm}}.

<!-- PRODUCTION ONLY VERSION
new topic that includes content from existing topics about samples and migration
-->
