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

# Pourquoi utiliser l'API {{site.data.keyword.mql}} ?
{: #why_mql}

L'API {{site.data.keyword.mql}} offre un niveau plus élevé d'abstraction que l'API Kafka. {{site.data.keyword.mql}} permet d'écrire de manière rapide et portable les applications dans un modèle de messagerie unifiée qui prend en charge à la fois les masques de messagerie de publication/abonnement et de file d'attente. 
{:shortdesc}

Les applications échangent des messages grâce à des destinations créées de manière dynamique, que vous pouvez structurer hiérarchiquement (par exemple,
<code>‘/sports/football’</code>), regrouper à l'aide de caractères génériques (par exemple,
<code>‘/sports/#’</code>) et sont dotées de contrôles simples pour l'assurance de distribution et l'expiration des messages.
Cela vous permet d'implémenter simplement des scénarios tels que le déchargement d'agent, la notification d'événement et le traitement par lot.

De même que vous envoyez des messages vers d'autres applications à l'aide de l'API {{site.data.keyword.mql}}, vous pouvez échanger des messages avec les applications qui utilisent l'API REST Kafka ou les API Kafka. Vous pouvez également utiliser des applications sur site avec {{site.data.keyword.IBM}} MQ.

