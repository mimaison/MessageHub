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

# Utilisation de KSQL avec Message Hub
{: #ksql_using}

Vous pouvez utiliser [KSQL ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/confluentinc/ksql){:new_window} avec {{site.data.keyword.messagehub}} pour le traitement des flux. Procédez comme suit :

1. Créez un fichier de configuration KSQL {{site.data.keyword.messagehub}}.

    Par exemple :
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
    Veillez à éditer les lignes suivantes pour y insérer vos propres données :
	- <code>bootstrap.servers</code> - insérez tous les hôtes Kafka répertoriés sur la page **Données d'identification pour le service**. Pour trouver ces informations, accédez à votre instance	{{site.data.keyword.messagehub}} dans {{site.data.keyword.Bluemix_notm}}, puis à l'onglet **Données d'identification pour le service** et sélectionnez les **Données d'identification** que vous voulez utiliser.
	- <code>sasl.jaas.config</code> - insérez votre propre paire nom d'utilisateur et mot de passe
	
2. Utilisez le tableau de bord {{site.data.keyword.messagehub}} dans la console {{site.data.keyword.Bluemix_notm}} pour créer un sujet nommé <code>ksql__commands</code> avec une seule partition et la durée de conservation par défaut.
3. A partir d'un terminal Docker, démarrez KSQL avec la commande suivante :
<pre class="pre">/bin/ksql-cli local 
--<var class="keyword varname">properties-file</var> ./config/ksqlserver.properties
</pre>
4. Pour renseigner les données, éditez la classe <code>DataGen</code> dans <code>io.confluent.ksql.datagen</code> dans le projet <code>ksql-examples</code>. Par exemple :
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
5. Utilisez le tableau de bord {{site.data.keyword.messagehub}} dans la console {{site.data.keyword.Bluemix_notm}} pour créer deux sujets avec une partition chacun : <code>users</code> et <code>pageviews</code>.

    Puis deux fois démarrez <code>DataGen</code> comme suit :
	
    i. Avec <code>bootstrap-server=HOSTNAME:PORTNUMBER quickstart=users format=json topic=users maxInterval=10000</code> pour lancer la création d'événements <code>users</code>.
	
    ii. Avec <code>bootstrap-server=HOSTNAME:PORTNUMBER quickstart=pageviews format=delimited topic=pageviews maxInterval=10000</code> pour lancer la création d'événements <code>pageviews</code>.
	
	Vérifiez que vous avez inséré tous les hôtes Kafka répertoriés sur la page **Données d'identification pour le service** comme valeurs de <code>bootstrap-server</code>. Pour trouver ces informations, accédez à votre instance	{{site.data.keyword.messagehub}} dans {{site.data.keyword.Bluemix_notm}}, puis à l'onglet **Données d'identification pour le service** et sélectionnez les **Données d'identification** que vous voulez utiliser.

Une fois ces étapes accomplies, vous pouvez exécuter toutes les requêtes répertoriées dans le [Guide de démarrage rapide KSQL ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/confluentinc/ksql/tree/0.1.x/docs/quickstart#create-a-stream-and-table){:new_window}

