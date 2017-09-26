---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-27"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# ¿Qué es {{site.data.keyword.messagehub}}?

{{site.data.keyword.messagehub}} implementa la mensajería de publicación/suscripción utilizando temas.
Al contrario de lo que sucede con los sistemas de mensajería tradicionales, {{site.data.keyword.messagehub}} proporciona temas pero no colas. {{site.data.keyword.messagehub}} también ofrece funciones adicionales como {{site.data.keyword.mql}} API y puentes para otros sistemas.

{{site.data.keyword.messagehub}} tiene tres API: la API Kafka, la API de {{site.data.keyword.mql}} y la API REST Kafka. Para obtener más información sobre la creación de aplicaciones de mensajería mediante las API, consulte [Uso de un cliente Kafka](/docs/services/MessageHub/messagehub050.html), [Uso de un cliente API MQ Light](/docs/services/MessageHub/messagehub075.html) y [Uso de la API REST Kafka](/docs/services/MessageHub/messagehub025.html).

{{site.data.keyword.messagehub}} también soporta puentes con otros sistemas seleccionados. Un puente es un enlace unidireccional a otro sistema. Un puente puede tener mensajes del otro sistema y publicarlos en un tema, o consumir mensajes de un tema y enviarlos al otro sistema. De esta forma, puede utilizar {{site.data.keyword.messagehub}} para integrar con otros sistemas sin escribir código. Para más información, consulte [Cómo enlazar con otros servicios utilizando puentes](/docs/services/MessageHub/messagehub088.html).

{{site.data.keyword.messagehub}} se basa en el proyecto de código abierto Apache Kafka, una red troncal de mensajería de alto rendimiento y sumamente escalable probada en numerosos entornos de producción.
Para obtener más información, consulte [{{site.data.keyword.messagehub}} y Apache Kafka](/docs/services/MessageHub/messagehub073.html).
