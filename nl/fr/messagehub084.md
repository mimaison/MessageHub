---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-11"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Procédure de migration du client Kafka depuis la version 0.9.X vers la version 0.10.X ou 0.11.X
{: #kafka_migrate}


Si vous utilisez les clients Java, vous pouvez désormais utiliser les clients Kafka 0.10.X ou 0.11.X disponibles. Il est fortement conseillé de migrer la version 0.9.X vers la version 0.10.X ou 0.11.X la plus récente (nous prenons en charge toutes les versions les plus récentes). Procédez comme suit :

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

3. Ajoutez cette ligne aux propriétés de consommateur et de producteur : <code>sasl.mechanism=PLAIN</code>


