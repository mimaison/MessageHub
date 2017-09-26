---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# ¿Qué es la API MQ Light y cuáles son sus particularidades?
{: #mqlight}

La API {{site.data.keyword.mql}} proporciona un nivel superior de abstracción de mensajería que la API Kafka, lo que facilita su aprendizaje y su uso en las aplicaciones. {:shortdesc}

La elección entre el uso de un cliente Kafka o la API {{site.data.keyword.mql}} depende de la topología de mensajería que desee crear:

* Con Kafka, se utiliza un número reducido de temas y puede haber varias particiones para cada tema para obtener mayor escalabilidad. Puede compartir mensajes entre consumidores utilizando grupos de consumidores, pero cada consumidor debe poder mantener la tasa de mensajes de las particiones asignadas.
* Con la API {{site.data.keyword.mql}}, puede utilizar un número mucho mayor de temas y los nombres de temas son jerárquicos (por ejemplo: <code>'/sports/football'</code> y <code>'/sports/tiddlywinks'</code>). Compartir mensajes entre los consumidores es mucho más sencillo.

Los temas de la API {{site.data.keyword.mql}} no son los mismos que los temas de Kafka. En su lugar, la API {{site.data.keyword.mql}} utiliza un tema único denominado "MQLight Kafka" y todos los mensajes enviados y recibidos utilizando la API {{site.data.keyword.mql}} pasan por ese tema de Kafka concreto.

{{site.data.keyword.mql}} está disponible solo en las siguientes regiones de {{site.data.keyword.Bluemix_notm}}: el sur de EE.UU., Reino Unido y Sydney. La API MQ Light no está disponible en la región de Alemania ni en {{site.data.keyword.Bluemix_notm}}.

<!-- begin PRODUCTION ONLY -->
Para obtener más información sobre la elección de las API, consulte [¿Por qué utilizar la API Kafka?](/docs/services/MessageHub/messagehub054.html), [¿Por qué utilizar la API MQ Light?](/docs/services/MessageHub/messagehub076.html)y [¿Por qué utilizar la API REST Kafka?](/docs/services/MessageHub/messagehub065.html).
<!-- end PRODUCTION ONLY -->
