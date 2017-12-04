---

copyright:
  years: 2015, 2017
lastupdated: "2017-01-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Choix entre les trois API
{: #choose_api}

{{site.data.keyword.messagehub}} prend en charge trois API. Les informations suivantes vous aideront à choisir celle qui vous convient le mieux.

## Pourquoi utiliser l'API Kafka ?
{: #why_kafka notoc}

Plusieurs raisons peuvent justifier l'utilisation de l'API Kafka par rapport aux autres interfaces fournies par {{site.data.keyword.messagehub}}. Ces raisons sont les suivantes :
{:shortdesc}


* Il est plus facile d'intégrer votre application à des systèmes existants qui prennent en charge Kafka, par exemple {{site.data.keyword.IBM}} {{site.data.keyword.streaminganalyticsshort}} et {{site.data.keyword.sparks}}.
* Les temps d'attente sont moins longs et la capacité de traitement plus élevée qu'avec les autres API.
* Elle est plus riche que l'API REST Kafka.


## Pourquoi utiliser l'API {{site.data.keyword.mql}} ?
{: #why_mql notoc}

L'API {{site.data.keyword.mql}} offre un niveau plus élevé d'abstraction que l'API Kafka. {{site.data.keyword.mql}} permet d'écrire de manière rapide et portable les applications dans un modèle de messagerie unifiée qui prend en charge à la fois les masques de messagerie de publication/abonnement et de file d'attente. 
{:shortdesc}

Les applications échangent des messages grâce à des destinations créées de manière dynamique, que vous pouvez structurer hiérarchiquement (par exemple, <code>‘/sports/football’</code>), regrouper à l'aide de caractères génériques (par exemple,
<code>‘/sports/#’</code>) et sont dotées de contrôles simples pour l'assurance de distribution et l'expiration des messages.
Cela vous permet d'implémenter simplement des scénarios tels que le déchargement d'agent, la notification d'événement et le traitement par lot.

De même que vous envoyez des messages vers d'autres applications à l'aide de l'API {{site.data.keyword.mql}}, vous pouvez échanger des messages avec les applications qui utilisent l'API REST Kafka ou les API Kafka. Vous pouvez également utiliser des applications sur site avec {{site.data.keyword.IBM_notm}} MQ.


## Pourquoi utiliser l'API REST Kafka ?
{: #why_rest notoc}

L'API REST Kafka est une interface pratique qui peut servir dans les situations suivantes :

* Quand un développeur veut être rapidement en mesure d'utiliser {{site.data.keyword.messagehub}}
* Dans certains cas d'utilisation à faible capacité de traitement pour lesquels le temps d'attente n'est pas un facteur critique
* Pour le débogage et la détection des incidents

L'API REST Kafka n'est pas conçue pour être une interface offrant une capacité de traitement élevée et de faibles temps d'attente.Pour ce type de besoins, il est recommandé d'utiliser l'API Kafka afin d'établir une connexion vers et depuis {{site.data.keyword.messagehub}}. Pour plus d'informations, voir [Utilisation d'un client Kafka](/docs/services/MessageHub/messagehub050.html#kafka_client).












