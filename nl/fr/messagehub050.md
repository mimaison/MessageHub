---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-10"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Utilisation d'un client Kafka
{: #kafka_using}

{{site.data.keyword.messagehub}} repose actuellement sur
Kafka 0.10.2.1. La première version du client Kafka pouvant se connecter à {{site.data.keyword.messagehub}} est la version 0.9.0.0. La version la plus récente est la version 
0.10.2.1. Vous ne pouvez pas connecter un client Kafka à {{site.data.keyword.messagehub}} si le numéro de version du client Kafka est
supérieur au numéro de version de Kafka que nous avons déployé.

Les clients Kafka existent en plusieurs langages et nous fournissons des instructions pour certains d'entre eux. Vous pouvez en utiliser d'autres, mais vous aurez besoin d'une prise en charge SASL PLAIN pour les données d'identification.
