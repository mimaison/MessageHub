---

copyright:
  years: 2015, 2017
lastupdated: "2017-01-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Selección entre las tres API
{: #choose_api}

{{site.data.keyword.messagehub}} soporta tres API. A continuación, encontrará información para ayudarle a decidir qué opción es la más adecuada:

## ¿Por qué utilizar la API Kafka?
{: #why_kafka notoc}

Existen diversas razones por las que puede elegir la API Kafka en vez de elegir otras interfaces proporcionadas
por
{{site.data.keyword.messagehub}}. Estas razones son:{:shortdesc}


* Es más fácil integrar su app con sistemas existentes que admiten Kafka, por ejemplo {{site.data.keyword.IBM}} {{site.data.keyword.streaminganalyticsshort}} y {{site.data.keyword.sparks}}.
* Ofrece una latencia inferior y un rendimiento mayor que las demás API.

* Ofrece una API más rica que la API REST Kafka.


## ¿Por qué utilizar la API {{site.data.keyword.mql}} ?
{: #why_mql notoc}

La API {{site.data.keyword.mql}} proporciona un nivel superior de abstracción que la API Kafka. {{site.data.keyword.mql}} permite grabar las apps de forma rápida y portátil en un modelo de mensajería unificada que soporta tanto los patrones de mensajería en cola como de publicación/suscripción.
{:shortdesc}

Las apps se intercambian mensajes utilizando destinos creados dinámicamente, que se pueden estructurar de forma jerárquica (por ejemplo, <code>'/sports/football'</code>), agrupar utilizando comodines (por ejemplo,
<code>‘/sports/#’</code>) y a los que se pueden añadir sencillos controles para garantizar la entrega y controlar la caducidad del mensaje.
Esto permite implementar escenarios como descarga de trabajador, notificación de eventos y procesamiento por lotes directamente.
Además de enviar mensajes entre otras apps utilizando la API {{site.data.keyword.mql}}, también se pueden intercambiar mensajes con apps que utilizan la API de Kafka o la API REST de Kafka. Como alternativa, también puede utilizar las apps en sistemas con {{site.data.keyword.IBM_notm}} MQ.


## ¿Por qué utilizar la API REST Kafka?
{: #why_rest notoc}

La API REST Kafka es una interfaz conveniente que puede ser utilizada en las siguientes situaciones:  

* Cuando un desarrollador quiera empezar a utilizar {{site.data.keyword.messagehub}}
* En algunos casos de uso de bajo rendimiento donde la latencia no sea un factor importante 
* Para depurar y encontrar errores

La API REST Kafka no está pensada como una interfaz de rendimiento elevado y latencia baja. ​Para estos tipos de requisitos, recomendamos el uso de la API de Kafka para conectarse a y desde {{site.data.keyword.messagehub}}. Para obtener más información, consulte [Uso de un cliente Kafka](/docs/services/MessageHub/messagehub050.html#kafka_client).












