---

copyright:
  years: 2015, 2017
lastupdated: "2017-02-08"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Différences entre Message Hub dans les environnements Bluemix Public et Bluemix Dedicated
{: #public_dedicated}

{{site.data.keyword.Bluemix}} est une plateforme à normes ouvertes reposant sur le cloud qui permet de construire, d'exécuter et de gérer des applications. {{site.data.keyword.Bluemix_notm}}
fournit des modèles de déploiement publics et dédiés. {{site.data.keyword.messagehub}} est disponible dans les deux environnements.

## Environnement {{site.data.keyword.Bluemix_notm}} Public
{: notoc}

{{site.data.keyword.Bluemix_notm}} Public propose un service de cloud à moindre coût, dans lequel vous ne payez que ce que vous utilisez et partagez l'infrastructure avec d'autres. 

Dans {{site.data.keyword.Bluemix_notm}} Public, le coût de {{site.data.keyword.messagehub}} est déterminé par deux facteurs : le nombre de partitions que vous utilisez et le nombre de messages que vous envoyez et recevez. Les
données des messages ne sont pas facturées tant qu'elles sont conservées dans les sujets, mais leur volume est limité à 1 Go sur chaque partition. 

Pour plus d'informations, voir [{{site.data.keyword.Bluemix_notm}} Public ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud-computing/bluemix/public){:new_window}.


## Environnement {{site.data.keyword.Bluemix_notm}} Dedicated
{: notoc}

{{site.data.keyword.Bluemix_notm}} Dedicated propose un environnement plus isolé dans lequel votre infrastructure n'est pas partagée et est hébergée dans un compte SoftLayer distinct géré par {{site.data.keyword.IBM_notm}}. Cet environnement est connecté de manière sécurisée à {{site.data.keyword.Bluemix_notm}} Public et à votre propre réseau. 

Dans une instance dédiée de {{site.data.keyword.messagehub}}, vous payez pour le service plutôt que pour le volume d'utilisation. Vous pouvez disposer d'un maximum de 75 sur la totalité de l'environnement, incluant toutes les organisations et tous les espaces. Chaque partition est limitée à 10 Go, ce qui garantit un espace suffisant au cluster. 

Les tableaux de bord Kibana et Grafana pour la surveillance du service ne sont pas pris en charge dans {{site.data.keyword.Bluemix_notm}} Dedicated.

Pour plus d'informations, voir [{{site.data.keyword.Bluemix_notm}} Dedicated ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/cloud-computing/bluemix/dedicated/){:new_window}.


