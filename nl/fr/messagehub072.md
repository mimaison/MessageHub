---

copyright:
  years: 2015, 2017
lastupdated: "2017-03-14"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


#Surveillance et journalisation
{: #monitoring}


{{site.data.keyword.messagehub}} collecte automatiquement les mesures et les événements qui vous permettent de surveiller votre utilisation de {{site.data.keyword.messagehub}}.
{:shortdesc}

**Remarque :** Les mesures et les événements ne sont pas disponibles dans {{site.data.keyword.messagehub}} dans les environnements
{{site.data.keyword.Bluemix_short}} Dédié.

Vous pouvez surveiller les informations de journal suivantes :

<dl>
<dt>Mesures relatives aux sujets</dt>
<dd>Le nombre d'octets entrants et sortants pour chacun de vos sujets est envoyé (un point de contrôle est mis en place toutes les 15 minutes). Vous
pouvez accéder à ces mesures en cliquant sur le bouton **Grafana**
du tableau de bord {{site.data.keyword.messagehub}} dans la console {{site.data.keyword.Bluemix_notm}}.
</dd>
<dt>Evénements relatifs aux sujets</dt>
<dd>Des événements sont aussi envoyés par push chaque fois que vous créez ou supprimez un sujet. Vous pouvez accéder à ces événements en cliquant sur le bouton **Kibana**
du tableau de bord {{site.data.keyword.messagehub}} dans la console
{{site.data.keyword.Bluemix_notm}}.</dd>
</dl>


Il est conseillé de ne pas éditer les tableaux de bord
{{site.data.keyword.messagehub}} car {{site.data.keyword.messagehub}}
effectue des mises à jour susceptibles d'écraser vos modifications. Vous pouvez toutefois inclure ces mesures et événements dans vos propres tableaux de bord.
