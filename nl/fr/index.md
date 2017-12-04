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

# Initiation à Message Hub
{: #messagehub}

{{site.data.keyword.messagehub_full}} est un service de messagerie
évolutif, distribué, à haute capacité de traitement qui permet aux applications et aux
services de communiquer facilement et de manière fiable.
{:shortdesc}

{{site.data.keyword.messagehub}} vous permet d'effectuer les tâches suivantes :

* Décharger des travaux vers des processus d'agent de back end
* Connecter des données de flux à des fonctions d'analyse pour en tirer des informations importantes
* Fournir des données d'événement à plusieurs applications pour qu'elles réagissent en temps réel
* Transférer des données vers un autre service

Pour vous familiariser avec {{site.data.keyword.messagehub}}
et commencer à envoyer et à recevoir des messages, utilisez l'exemple Java™. Cet exemple montre comment
un producteur envoie des messages à un consommateur à l'aide d'un sujet. Le même
exemple de programme permet de consommer et de produire des messages.

![Diagramme de présentation de l'exemple Java](getting_started_sample.gif "Diagramme de présentation de l'exemple Java illustrant le flux de messages.")


Procédez comme suit :
{: #getting_started_steps}
 
1. Créez une instance de service {{site.data.keyword.messagehub}} :

  a. Connectez-vous à {{site.data.keyword.Bluemix_notm}} à l'aide de l'interface utilisateur Web. 
  
  b. Cliquez sur **CATALOGUE**.
  
  c. Dans la section **Services d'application**, cliquez sur **{{site.data.keyword.messagehub}}**. La page de l'instance de service {{site.data.keyword.messagehub}} s'ouvre.
  
  d. Laissez le service déconnecté dans le menu **Connecter à** et entrez le nom de votre service, ainsi que les données d'identification. Vous pouvez utiliser les valeurs par défaut.
  
  e. Cliquez sur **Créer**.

2. Si vous n'en disposez pas déjà, installez la configuration requise suivante :

    * [git ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://git-scm.com/){:new_window}
	* [Gradle ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://gradle.org/){:new_window}
    * Java 7 ou version ultérieure
 
3. Clonez le référentiel Git message-hub-samples en exécutant la commande suivante à partir de la ligne de commande :

    <pre class="pre">
    git clone https://github.com/ibm-messaging/message-hub-samples.git
    </pre>
	{: codeblock}

4. Accédez au répertoire de l'exemple de console Java en exécutant la commande suivante :

    <pre class="pre">
    cd message-hub-samples/kafka-java-console-sample
    </pre>
	{: codeblock}

5. Exécutez les commandes de génération suivantes :

    <pre class="pre">
    gradle clean && gradle build
    </pre>
	{: codeblock}

6. Démarrez le consommateur sur votre console en exécutant la commande suivante :

    <pre class="pre">java -jar build/libs/kafka-java-console-sample-2.0.jar 
	<var class="keyword varname">kafka_brokers_sasl</var> <var class="keyword varname">kafka_admin_url</var> <var class="keyword varname">api_key</var> -consumer</pre>
    {: codeblock}
    
    Cet exemple utilise un sujet nommé `kafka-java-console-sample-topic`. Si le sujet n'existe pas déjà, l'exemple le crée à l'aide de l'API d'administration {{site.data.keyword.messagehub}}. Pour envoyer et recevoir des messages, l'exemple utilise l'API Java Apache Kafka.

    Pour trouver les valeurs de *kafka_brokers_sasl*, *kafka_admin_url* et *api_key*, accédez à votre instance {{site.data.keyword.messagehub}} dans {{site.data.keyword.Bluemix_notm}}, cliquez sur l'onglet **Données d'identification pour le service** et sélectionnez les **Données d'identification** que vous souhaitez utiliser.
    
	**Important :** *kafka_brokers_sasl* doit être une chaîne unique, encadrée de guillemets. Par exemple :

    <pre class="pre">
    "host1:port1,host2:port2"
    </pre>
	{: codeblock}

    Il est conseillé d'utiliser tous les hôtes Kafka répertoriés dans les **Données d'identification** que vous avez sélectionnées.

7. Démarrez le producteur sur votre console en exécutant la commande suivante :
   
    <pre class="pre">java -jar build/libs/kafka-java-console-sample-2.0.jar 
	<var class="keyword varname">kafka_brokers_sasl</var> <var class="keyword varname">kafka_admin_url</var> <var class="keyword varname">api_key</var> -producer</pre>
 {: codeblock}
  
8. Vous devriez voir les messages envoyés par le producteur apparaître sur dans le consommateur. Voici
un exemple de sortie :

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
	
9. L'exemple s'exécute indéfiniment jusqu'à ce que vous l'arrêtiez. Pour arrêter le processus, exécutez une commande similaire à celle-ci : <code>Ctrl+C</code>


Pour plus d'informations sur l'exécution d'un exemple {{site.data.keyword.messagehub}} avec Python, voir [Modèle d'application de console Python ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/messaging/2017/02/09/new-message-hub-sample-python-console-application/){:new_window}. Vous
trouverez également des exemples qui illustrent le fonctionnement d'autres API ou d'autres fonctionnalités sur la page [Exemples {{site.data.keyword.messagehub}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-messaging/message-hub-samples){:new_window}.

Pour regarder une vidéo qui décrit pas à pas la procédure d'obtention d'un exemple Java destiné à s'exécuter sur {{site.data.keyword.messagehub}}, voir [{{site.data.keyword.messagehub}} - Getting started with IBM's Kafka in the cloud ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.youtube.com/watch?v=tt-bLtFzC_4){:new_window}.

