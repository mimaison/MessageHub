---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Foire aux questions {{site.data.keyword.messagehub}}
{: #faqs}

Vous trouverez ici les réponses aux questions courantes concernant le service {{site.data.keyword.IBM}} {{site.data.keyword.messagehub}}. 

## Quelle est la valeur par défaut de Kafka offsets.retention.minutes ?
{: #offsets notoc}
La valeur par défaut est de 7 jours. 

La conservation des positions s'effectue au niveau du système. Vous ne pouvez donc pas la définir au niveau d'un sujet spécifique. Les
groupes de consommateurs n'obtiennent que 7 jours de positions stockées, même si la durée
de conservation de journal de leur sujet a été augmentée pour atteindre la valeur
maximale de 30 jours. 

## Quel est le comportement en disponibilité de {{site.data.keyword.messagehub}} ?
{: #availability notoc}

Si vous écrivez des applications {{site.data.keyword.messagehub}}, ces informations vous expliquent le comportement normal en disponibilité de {{site.data.keyword.messagehub}} et ce que vos applications sont censées traiter. 

### API
{: #api_availability notoc}

Dans le cadre du fonctionnement normal de {{site.data.keyword.messagehub}}, les noeuds des clusters Kafka sont parfois redémarrés.
Dans certains cas, vos applications sont conscientes de la réaffectation des ressources par le cluster. Ecrivez vos applications de telle sorte qu'elles soient résilientes face à ces changements et qu'elles puissent se reconnecter et reprendre leur fonctionnement.

### Ponts {{site.data.keyword.messagehub}}
{: #bridge_availability notoc}

Ecrivez vos applications de telle sorte qu'elles gèrent la possibilité d'un redémarrage occasionnel des ponts. 
