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

# Procédure de connexion et d'authentification
{: #kafka_connect}


Pour se connecter à {{site.data.keyword.messagehub}}, l'API Kafka utilise les  
<code>kafka_brokers_sasl</code> données d'identification, ainsi que l'utilisateur <code>user</code> et le mot de passe
<code>password</code> provenant de la [variable d'environnement VCAP_SERVICES](/docs/services/MessageHub/messagehub071.html).

## Connexion et authentification dans une application autre que Java
{: #kafka_notjava notoc}

Le service {{site.data.keyword.messagehub}} procède actuellement à l'authentification des
clients grâce à SASL PLAIN. Les données d'identification sont transmises via une connexion cryptée.
Il s'agit d'une nouvelle fonction de Kafka 0.10.0.X. N'importe client prenant en charge
Kafka 0.10 avec SASL PLAIN doit fonctionner avec {{site.data.keyword.messagehub}}. Voici des exemples de client :

* [librdkafka ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/edenhill/librdkafka/){:new_window}
* [confluent-kafka-python ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/confluentinc/confluent-kafka-python){:new_window}

Si vous utilisez le client Kafka 0.9.0.0 plus ancien, vous devez employer un module de connexion personnalisé que vous pouvez télécharger à partir de la page [Module de connexion à {{site.data.keyword.messagehub}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-messaging/message-hub-samples/blob/master/kafka-0.9/message-hub-login-library/messagehub.login-1.0.0.jar){:new_window}.

