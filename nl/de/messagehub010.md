---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-26"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Informationen zu Message Hub
{: #about}

{{site.data.keyword.messagehub_full}} ist ein skalierbarer verteilter Messaging-Service mit
hohem Durchsatz, der eine einfache und zuverlässige Kommunikation zwischen Anwendungen und Services ermöglicht.
{:shortdesc}

In {{site.data.keyword.messagehub}} können Anwendungen Daten senden, indem eine
Nachricht erstellt und an ein Topic gesendet wird. Zum Empfangen von Nachrichten abonnieren Anwendungen
ein Topic. Dabei kann ausgewählt werden, ob die Anwendungen alle Nachrichten für das abonnierte Topic
empfangen oder jeweils nur freigegebene Nachrichten.
{{site.data.keyword.messagehub}} hostet und verwaltet die Nachrichten in einer
geordneten Reihenfolge. Im Unterschied zu konventionellen Messaging-Systemen arbeitet
{{site.data.keyword.messagehub}} mit Topics und nicht mit Warteschlangen. {{site.data.keyword.messagehub}}
bietet jedoch Möglichkeiten zur gemeinsamen Nutzung von Nachrichten durch empfangende
Anwendungen. Dies entspricht in etwa dem Ausführungsverhalten von Warteschlangen.

Mit {{site.data.keyword.messagehub}} können Sie die folgenden
Tasks ausführen:

* Arbeit in Back-End-Verarbeitungsprozesse auslagern
* Streaming-Daten mit Analysen verbinden, um aussagekräftige Erkenntnisse zu gewinnen
* Ereignisdaten in mehreren Anwendungen veröffentlichen, um in Echtzeit reagieren zu können
* Daten in einen anderen Service übertragen (z. B. in einen Langzeitspeicher)
