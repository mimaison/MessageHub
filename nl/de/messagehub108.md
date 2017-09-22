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

# Häufig gestellte Fragen (FAQs) zu {{site.data.keyword.messagehub}}
{: #faqs}

Antworten auf häufig gestellte Fragen zum {{site.data.keyword.IBM}} {{site.data.keyword.messagehub}}-Service.

## Was ist der Kafka-Standardwert für offsets.retention.minutes?
{: #offsets notoc}
Der Standardwert ist 7 Tage. 

Die Offset-Aufbewahrungsdauer gilt systemweit und kann nicht für eine einzelne Topicebene festgelegt werden. Für alle Consumergruppen werden nur gespeicherte Offsets für einen Zeitraum von 7 Tagen bereitgestellt, selbst wenn die Aufbewahrungsdauer für das zugehörige Topic auf den Maximalwert von 30 Tagen erhöht wurde. 

## Wie ist das Verfügbarkeitsverhalten von {{site.data.keyword.messagehub}}?
{: #availability notoc}

Verwenden Sie diese Informationen beim Schreiben von {{site.data.keyword.messagehub}}-Apps, um das normale Verfügbarkeitsverhalten von {{site.data.keyword.messagehub}} und die damit verbundenen Anforderungen an das Ausführungsverhalten Ihrer Apps kennenzulernen.

### APIs
{: #api_availability notoc}

Im regulären Betrieb von {{site.data.keyword.messagehub}} werden die Knoten der Kafka-Cluster bei Bedarf erneut gestartet.
In manchen Fällen werden Ihre Apps darauf vorbereitet, dass der Cluster Ressourcen neu zuordnet. Gestalten Sie Ihre Apps so,
dass sie auf solche Änderungen entsprechend reagieren und Verbindungen wiederherstellen bzw. Operationen wiederholen können.

### {{site.data.keyword.messagehub}}-Bridges
{: #bridge_availability notoc}

Gestalten Sie Ihre Apps so, dass gelegentliche Neustarts der Bridges verarbeitet werden können.
