---

copyright:
  years: 2015, 2017
lastupdated: "2017-01-25"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Message Hub y Apache Kafka
{: #apache_kafka}

Apache Kafka conforma el núcleo de mensajería segura de {{site.data.keyword.messagehub}}. Es un sistema de
mensajería de publicación y suscripción y está diseñado para ser tolerante a fallos, proporcionando una plataforma de
alto rendimiento, latencia baja para gestionar canales de información de datos en tiempo real. Estas características son ideales para utilizarse en un entorno cloud. {:shortdesc}

![Diagrama con la arquitectura de Kafka.](kafka_architecture.png "Diagrama con la arquitectura de Kafka. Los productores introducen datos en un clúster de Kafka y los consumidores se suscriben a los mensajes.") 

La siguiente lista define algunos conceptos de Apache Kafka: 

<dl><dt>Tema</dt>
<dd>Un canal de información en el cual se publican mensajes.</dd>
<dt>Partición</dt>
<dd>Cada tema contiene una o más particiones. Cada partición es una lista ordenada de mensajes. Si un tema
tiene más de una partición, permite a los datos alimentarse en paralelo para aumentar el rendimiento.</dd>
<dt>Productor</dt>
<dd>Un proceso que publica secuencias de mensajes en temas Kafka. Un productor puede publicar en uno o más temas y puede elegir opcionalmente la partición que almacena los datos.</dd>
<dt>Consumidor </dt>
<dd>Un proceso que consume mensajes de temas Kafka y procesa los canales de información de mensajes publicados. Un consumidor puede suscribirse a uno o más temas o particiones.</dd>
<dt>Grupo de consumidores</dt>
<dd>Un grupo determinado de uno o más consumidores. Cada consumidor del grupo lee mensajes de particiones específicas
de los temas a los que el consumidor está suscrito. Cada mensaje se envía a
un consumidor del grupo y todos los mensajes con la misma clave se envían al mismo consumidor.<p>Cada partición se asigna a un solo consumidor del grupo. </p> 
<ul>
<li>Si hay más particiones que consumidores en un grupo, algunos consumidores tienen varias particiones.</li>
<li>Si hay más consumidores que particiones, algunos consumidores no tienen particiones.</li>
</ul>
</dd>
</dl>

Para obtener más información, consulte la [Documentación de Apache Kafka ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://kafka.apache.org/documentation.html){:new_window} y el artículo [Message Hub Kafka Java&trade; API developerWorks&reg; ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/messaging/2016/03/03/message-hub-kafka-java-api/){:new_window}.


