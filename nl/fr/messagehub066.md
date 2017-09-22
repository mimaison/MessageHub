---

copyright:
  years: 2015, 2017
lastupdated: "2016-11-22"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Procédure de connexion et d'authentification
{: #rest_connect}

Pour se connecter à {{site.data.keyword.messagehub}}, l'API Kafka utilise les données d'identification <code>api_key</code> et <code>kafka_rest_url</code> provenant de la [variable d'environnement VCAP_SERVICES](/docs/services/MessageHub/messagehub071.html).

Pour vous authentifier à l'API REST Kafka {{site.data.keyword.messagehub}}, vous devez spécifier l'attribut <code>api_key</code> dans l'en-tête X-Auth-Token de vos demandes.
