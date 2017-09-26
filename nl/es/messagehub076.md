---

copyright:
  years: 2015, 2017
lastupdated: "2016-11-22"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# ¿Por qué utilizar la API {{site.data.keyword.mql}} ?
{: #why_mql}

La API {{site.data.keyword.mql}} proporciona un nivel superior de abstracción que la API Kafka. {{site.data.keyword.mql}} permite grabar las apps de forma rápida y portátil en un modelo de mensajería unificada que soporta tanto los patrones de mensajería en cola como de publicación/suscripción.
{:shortdesc}

Las apps se intercambian mensajes utilizando destinos creados dinámicamente, que se pueden estructurar de forma jerárquica (por ejemplo, <code>'/sports/football'</code>), agrupar utilizando comodines (por ejemplo,
<code>‘/sports/#’</code>) y a los que se pueden añadir sencillos controles para garantizar la entrega y controlar la caducidad del mensaje.
Esto permite implementar escenarios como descarga de trabajador, notificación de eventos y procesamiento por lotes directamente.
Además de enviar mensajes entre otras apps utilizando la API {{site.data.keyword.mql}}, también se pueden intercambiar mensajes con apps que utilizan la API de Kafka o la API REST de Kafka. Como alternativa, también puede utilizar las apps en sistemas con {{site.data.keyword.IBM}} MQ.

