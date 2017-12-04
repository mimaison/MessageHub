---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Foire aux questions {{site.data.keyword.messagehub}}
{: #faqs}

Vous trouverez ici les réponses aux questions courantes concernant le service {{site.data.keyword.IBM}} {{site.data.keyword.messagehub}}.

<!--17/10/17 - Karen: same info duplicated at messagehub104 -->
## Comment utiliser des API Kafka pour créer et supprimer des sujets ?
{: #topic_admin notoc}

Si vous utilisez la version 0.11 ou une version ultérieure du client Kafka, ou la version 0.10.2.0 ou une version ultérieure de Kafka Streams, vous pouvez employer des API pour créer et supprimer des sujets. Certaines restrictions s'appliquent aux paramètres autorisés lors de la création des sujets. Actuellement, vous ne pouvez modifier que les paramètres suivants :

<dl>
<dt>cleanup.policy</dt>
<dd>Défini sur <code>delete</code> (par défaut), <code>compact</code> ou <code>delete,compact</code></dd>
<dt>retention.ms</dt>
<dd>La durée de conservation par défaut est de 24 heures. La durée minimale est d'une heure et la durée maximale de 30 jours. Spécifiez cette valeur comme un nombre d'heures.

<p>**Remarque :** Si la règle de nettoyage est uniquement <code>compact</code>, <code>delete</code> est automatiquement ajouté, mais la suppression est désactivée selon l'heure. Les messages du sujet sont compactés jusqu'à 1 Go avant d'être supprimés.</p>
</dd>
</dl>

## Quelle est la durée que {{site.data.keyword.messagehub}} définit dans la fenêtre de conservation des journaux pour le sujet Décalages consommateur ?
{: #offsets notoc}
{{site.data.keyword.messagehub}} conserve les décalages consommateur pendant 7 jours. Cela correspond à la configuration Kafka offsets.retention.minutes. 

La conservation des décalages s'effectue au niveau du système. Vous ne pouvez donc pas la définir au niveau d'un sujet spécifique. Les groupes de consommateurs n'obtiennent que 7 jours de décalages stockés, même en utilisant un sujet dont la durée de conservation a été augmentée jusqu'au maximum de 30 jours. 

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
