---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-03"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Utilisation du client Java Kafka
{: #kafka_using}

## Utilisation, téléchargement et exécution de l'exemple d'API Java Kafka
{: notoc}

L'exemple d'API Java&trade; Kafka contient un producteur et un consommateur, codés en Java, qui utilisent directement l'API Kafka. Cet exemple peut être exécuté en local ou dans {{site.data.keyword.Bluemix_short}}.

L'exemple de code est disponible dans le [projet GitHub message-hub-samples ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}.Bien qu'il utilise l'API Kafka pour envoyer et recevoir des messages, il utilise l'API d'administration de {{site.data.keyword.messagehub}} pour créer le sujet auquel il en envoie et dont il en reçoit.

Pour plus d'informations sur la configuration et l'exécution de l'exemple, voir le fichier [README.md ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}.

Pour la procédure détaillée de l'exécution de l'exemple, voir [Initiation à {{site.data.keyword.messagehub}}](/docs/services/MessageHub/index.html#getting_started_steps).

## Utilisation, téléchargement et exécution de l'exemple Liberty for Java
{: #liberty_sample notoc}

L'exemple Liberty for Java implémente une application simple déployée dans le contexte d'exécution Liberty. L'application utilise l'API Kafka pour {{site.data.keyword.messagehub}} afin de produire et de consommer des messages.
Elle sert également un système frontal Web que vous pouvez utiliser pour l'administration.

L'exemple de code est disponible dans le [projet GitHub message-hub-samples ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-liberty-sample){:new_window}.

## Procédure de migration du client Kafka depuis la version 0.9.x vers la version 0.10.x
{: #kafka_migrate notoc}


Si vous utilisez les clients Java, vous pouvez désormais utiliser les clients Kafka 0.10.x disponibles. Il est fortement conseillé de migrer la version 0.9.x vers la version 0.10.x la plus récente (actuellement la version 0.10.2.1). Procédez comme suit :


1. Supprimez le module jar de connexion {{site.data.keyword.messagehub}}. 
2. Modifiez le fichier <code>jaas.conf</code> comme suit :
    ```
        KafkaClient {
          org.apache.kafka.common.security.plain.PlainLoginModule required
          serviceName="kafka"
            username="<your username>"
            password="<your password>";
        };
    ```
    {: codeblock}

3. Ajoutez cette ligne aux propriétés de consommateur et de producteur :
<code>sasl.mechanism=PLAIN</code>


## Utilisation de la propriété sasl.jaas.config
{: #sasl_prop notoc}
Si vous utilisez la version 0.10.2.1 ou une version ultérieure du client Kafka, vous pouvez employer la propriété <code>sasl.jaas.config</code> pour la configuration du client, à la place d'un fichier JAAS. Pour vous connecter à {{site.data.keyword.messagehub}}, définissez <code>sasl.jaas.config</code> comme suit :
<pre>
<code>    sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required \
    username="USERNAME" \
    password="PASSWORD";</code>
</pre>
{:codeblock}

Où USERNAME et PASSWORD sont les valeurs issues de l'onglet **Données d'identification pour le service** {{site.data.keyword.messagehub}} dans {{site.data.keyword.Bluemix_notm}}.

Si vous utilisez <code>sasl.jaas.config</code>, les clients exécutés dans la même machine virtuelle Java peuvent employer des données d'identification différentes. Pour plus d'informations, voir [Configuring Kafka clients ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://kafka.apache.org/documentation/#security_sasl_plain_clientconfig){:new_window}

## API pour l'administration des sujets
{: #topic_admin notoc}

Si vous utilisez la version 0.11 ou une version ultérieure du client Kafka, ou la version 0.10.2.0 ou une version ultérieure de Kafka Streams, vous pouvez employer des API pour créer et supprimer des sujets. Certaines restrictions s'appliquent aux paramètres autorisés lors de la création des sujets. Actuellement, vous ne pouvez modifier que les paramètres suivants : 

<dl>
<dt>cleanup.policy</dt>
<dd>Défini sur <code>delete</code> (par défaut), <code>compact</code> ou <code>delete,compact</code></dd>
<dt>retention.ms</dt>
<dd>La durée de conservation par défaut est de 24 heures. La durée minimale est d'une heure et la durée maximale de 30 jours. Spécifiez cette valeur comme un nombre d'heures.
<p>**Remarque :** Si la règle de nettoyage est uniquement <code>compact</code>, <code>delete</code> est automatiquement ajouté, mais la suppression est désactivée selon l'heure. Les messages du sujet sont compactés jusqu'à 1 Go avant d'être supprimés.</p>
</dd>
</dl>

## Prise en charge de Kafka Streams
{: #kafka_streams notoc}

Depuis la bibliothèque Streams 0.10.2.0, les API de sujet fonctionnent avec {{site.data.keyword.messagehub}} sans qu'aucune configuration ne soit requise. Spécifiez vos données d'identification SASL à l'aide de <code>sasl.jaas.config</code> ou d'un fichier JAAS et définissez <code>replication.factor</code> sur 3.

Exemple :

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

Où BOOTSTRAP_SERVERS, USERNAME et PASSWORD correspondent aux valeurs issues de l'onglet **Données d'identification pour le service** {{site.data.keyword.messagehub}} dans {{site.data.keyword.Bluemix_notm}}.

<!--
new topic that includes content from existing topics about samples and migration
-->
