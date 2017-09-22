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

# Configuration requise pour l'utilisation de l'API MQ Light avec Message Hub
{: #mql_reqs}

La configuration suivante est nécessaire pour utiliser l'API {{site.data.keyword.mql}} avec {{site.data.keyword.messagehub}} : 

**Vous devez créer de façon explicite un sujet Kafka nommé "MQLight" pour pouvoir utiliser l'API car tous les messages passent par le sujet "MQLight". Ce sujet doit posséder une partition unique. La création de ce sujet active l'API MQ Light pour votre instance de service. ** Pour plus d'informations sur la création de sujets dans {{site.data.keyword.messagehub}}, voir [Gestion des sujets](/docs/services/MessageHub/messagehub070.html).

Le sujet "MQLight" est utilisé par l'API MQ Light pour stocker ses données de messages et interagir avec d'autres clients Kafka. Notez que la création de ce sujet entraîne la facturation de frais au tarif standard indiqué dans le plan de paiement des services. 

Pour désactiver l'API MQ Light, supprimez le sujet "MQLight". La suppression de ce sujet entraîne la destruction de toutes les données. 
