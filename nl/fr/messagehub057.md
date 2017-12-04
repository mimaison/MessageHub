---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-05"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Restrictions connues
{: #restrictions}


##Sujets et partitions
{: #topics_partitions notoc}

*  Les noms de sujet ne peuvent pas comporter plus de 100 caractères.
*  Le nombre par défaut de partitions pour un sujet est un.
*  Chaque espace {{site.data.keyword.Bluemix_notm}} est soumis à une limite de 100 partitions. Si vous voulez créer des
partitions supplémentaires, vous devez utiliser un nouvel espace {{site.data.keyword.Bluemix_notm}}.

## Conservation des messages
{: #message_retention}

Par défaut, les messages sont conservés dans Kafka pendant 24 heures maximum et chaque partition ne peut pas dépasser 1 Go. Si le plafond de 1 Go est atteint, les messages les plus anciens sont supprimés pour que la limite soit respectée.

Vous pouvez modifier la durée de conservation des messages lorsque vous créez un sujet à l'aide de l'interface utilisateur ou de l'API d'administration. La limite de temps a un minimum d'une heure et un maximum de 30 jours.

## Création et suppression de sujets dans Kafka
{: #create_delete notoc}

Dans Kafka, la création et la suppression de sujets sont des opérations asynchrones susceptibles de prendre un certain temps. Il est conseillé d'éviter l'utilisation de modèles qui reposent sur la création rapide et la suppression de sujets, ou sur la suppression rapide et la re-création de sujets.

## API REST Kafka
{: #trouble_rest notoc}

*  Seul le format binaire intégré est pris en charge pour les demandes et les réponses. Les formats Avro et JSON intégrés ne sont pas pris en charge.
*  Les demandes simultanées ne sont pas prises en charge pour une instance consommateur.
   Les demandes de lecture, de validation ou de suppression correspondant à une instance consommateur ne doivent être envoyées qu'après réception d'une réponse aux demandes en attente pour cette instance.

## Limitation de débit de l'API REST Kafka
{: #kafka_rate notoc}

Les applications utilisant l'API REST Kafka peuvent être soumises à une
limitation de débit pour chaque clé d'API. Dans ce cas, l'API
répond avec l'erreur HTTP suivante :

<code>429 Too Many Requests</code>
{:screen}

Si vous rencontrez cette erreur, patientez et soumettez à nouveau la demande.

## Redémarrage quotidien de l'API REST Kafka
{: #rest_restart notoc}

L'API REST Kafka redémarre une fois par jour pendant un court laps de
temps. Au cours de cette période, elle est susceptible de ne plus être disponible. Si cela se produit, il est conseillé de relancer votre demande. Après le redémarrage
de l'API REST, vous devez créer à nouveau vos instances consommateur Kafka. Dans ce cas,
l'API REST renvoie le code JSON suivant :

```'{"error_code":40403,"message":"Consumer instance not found."}'
```
{:screen}

## API de consommateur de haut niveau Kafka
{: #kafka_consumer notoc}

L'API de consommateur simple ou de haut niveau Apache Kafka 0.8.2 ne peut pas être utilisée
avec {{site.data.keyword.messagehub}}. Utilisez à la place la toute première API consommateur Kafka prise en charge, à savoir l'API consommateur 0.9.
