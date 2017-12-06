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

# Häufig gestellte Fragen (FAQs) zu {{site.data.keyword.messagehub}}
{: #faqs}

Antworten auf häufig gestellte Fragen zum {{site.data.keyword.IBM}} {{site.data.keyword.messagehub}}-Service.

<!--17/10/17 - Karen: same info duplicated at messagehub104 -->
## Wie können mit Kafka-APIs Topics erstellt und gelöscht werden?
{: #topic_admin notoc}

Wenn Sie einen Kafka-Client der Version 0.11 oder höher verwenden oder Kafka Streams Version 0.10.2.0 oder höher, können Sie APIs verwenden, um Topics zu erstellen oder zu löschen. Für die zulässigen Einstellungen beim Erstellen von Topics gelten bestimmte Einschränkungen. Gegenwärtig können Sie nur die folgenden Einstellungen ändern:

<dl>
<dt>cleanup.policy</dt>
<dd>Zulässige Werte sind <code>delete</code> (Standardwert), <code>compact</code> oder <code>delete,compact</code></dd>
<dt>retention.ms</dt>
<dd>Der Standardaufbewahrungszeitraum ist 24 Stunden. Der Mindestwert ist 1 Stunde und der Höchstwert ist
30 Tage. Geben Sie den Wert in Stunden an.

<p>**Anmerkung:**
Wenn für die Bereinigungsrichtlinie (cleanup.policy) nur der Wert <code>compact</code> angegeben ist, wird automatisch der Wert <code>delete</code>
hinzugefügt, aber die Löschfunktion wird auf Zeitbasis inaktiviert. Die Nachrichten in dem Topic werden bis 1 GB komprimiert. Die Löschfunktion wird
erst beim Überschreiten dieses Werts aktiviert.</p>
</dd>
</dl>

## Welchen Zeitraum legt {{site.data.keyword.messagehub}} für das Protokollspeicherungsfenster für das Consumer-Offsets-Topic fest?
{: #offsets notoc}
{{site.data.keyword.messagehub}} speichert Consumer-Offsets für einen Zeitraum von 7 Tagen. Dies entspricht der Kafka-Konfiguration 'offsets.retention.minutes'. 

Die Offset-Aufbewahrungsdauer gilt systemweit und kann nicht für eine einzelne Topicebene festgelegt werden. Für alle Consumergruppen werden nur gespeicherte Offsets für einen Zeitraum von 7 Tagen bereitgestellt, selbst wenn die Protokollspeicherungsdauer für das zugehörige Topic auf den Maximalwert von 30 Tagen erhöht wurde. 

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
