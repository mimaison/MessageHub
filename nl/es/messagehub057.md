---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-05"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Restricciones conocidas
{: #restrictions}


##Temas y particiones
{: #topics_partitions notoc}

*  La longitud de los nombres de los temas está restringida y
pueden tener hasta 100 caracteres.
*  El número predeterminado de particiones por tema es de uno. 
*  Cada espacio de {{site.data.keyword.Bluemix_notm}} tiene un límite de 100 particiones. Para
crear más particiones, utilice un espacio nuevo de
{{site.data.keyword.Bluemix_notm}}. 

## Retención de mensajes
{: #message_retention}

De forma predeterminada, los mensajes se retienen un máximo de 24 horas
en Kafka y cada partición está limitada a 1 GB. Si se alcanza el GB, se descartarán los mensajes más antiguos para mantenerse dentro
del límite.

Puede cambiar el límite de tiempo para la retención de mensajes cuando cree un tema utilizando la interfaz de usuario o la API de administración.
El límite de tiempo es un mínimo de una hora y un máximo de 30 días.

## Creación y supresión de temas en Kafka
{: #create_delete notoc}

En Kafka, la creación y supresión de temas son operaciones asíncronas que pueden tardar algún tiempo en completarse.
Se recomienda evitar el uso de patrones que dependan de la creación y supresión rápidas de temas o de la supresión y recreación rápidas de temas.


## API REST Kafka
{: #trouble_rest notoc}

*  Para solicitudes y respuestas, sólo se admite el
formato compacto binario. No se da soporte a los formatos incorporado Avro y JSON. 
*  Las solicitudes actuales no se admiten para una instancia de consumidores. Las solicitudes read, commit o
                    delete correspondientes a una instancia de consumidores deben enviarse sólo después de
                    que se haya recibido una respuesta para todas las solicitudes pendientes de dicha                     instancia.

## Limitación de tasa de API REST Kafka
{: #kafka_rate notoc}

Las aplicaciones que utilizan la API REST Kafka pueden estar sujetas a la limitación de tasa para cada ApiKey. Cuando se produce esta limitación, la API responde con el siguiente error HTTP:

<code>429 Demasiadas solicitudes</code>
{:screen}

Si ve este error, espere y vuelva a enviar la solicitud.

## Reinicio diario de la API REST Kafka
{: #rest_restart notoc}

La API REST Kafka se reinicia una vez al día durante un breve período de tiempo. Durante este período, la API REST Kafka puede estar disponible. Si esto sucede, se recomienda reintentar la solicitud. Una vez reiniciada la API REST, deberá volver a crear las instancias de consumidor de Kafka. Si este es el caso, la API REST devuelve el siguiente JSON:

```'{"error_code":40403,"message":"Consumer instance not found."}'
```
{:screen}

## API de consumidor de alto nivel Kafka
{: #kafka_consumer notoc}

No puede utilizar la API simple o de
consumidor de alto nivel de Apache Kafka 0.8.2 con {{site.data.keyword.messagehub}}. Puede utilizar en su lugar la API de consumidor de Kafka soportada anteriormente, que es la API de consumidor 0.9.
