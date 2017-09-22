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

# Kafka-Client verwenden
{: #kafka_using}

{{site.data.keyword.messagehub}} basiert derzeit auf Kafka 0.10.2.1. Die niedrigste Version des Kafka-Clients, die eine Verbindung zu {{site.data.keyword.messagehub}} herstellen kann, ist Version 0.9.0.0. Die höchste Version ist
0.10.2.1. Ein Kafka-Client kann nicht mit {{site.data.keyword.messagehub}} verbunden werden, wenn die Versionsnummer des Kafka-Clients
höher ist als die Nummer der von uns bereitgestellten Kafka-Version.

Kafka-Clients sind in vielen Sprachen verfügbar. Anweisungen für einige dieser Sprachen werden von uns bereitgestellt. Wenn andere Kafka-Clients verwendet werden, ist Unterstützung für SASL PLAIN erforderlich, damit Berechtigungsnachweise bereitgestellt werden können.
