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

# Preguntas más frecuentes sobre {{site.data.keyword.messagehub}}
{: #faqs}

Respuestas a preguntas comunes acerca del servicio {{site.data.keyword.IBM}} {{site.data.keyword.messagehub}}.

## ¿Cuál es el valor predeterminado para offsets.retention.minutes de Kafka?
{: #offsets notoc}
El valor predeterminado es de 7 días. 

La retención de desplazamiento abarca todo el sistema y no se puede establecer en temas individuales. Todos los grupos de consumidores obtienen solo 7 días de desplazamientos almacenados incluso si su tema se ha ampliado al máximo de 30 días de retención de registro. 

## ¿Cuál es el comportamiento de la disponibilidad de {{site.data.keyword.messagehub}}?
{: #availability notoc}

Si escribe apps de {{site.data.keyword.messagehub}}, utilice esta información para comprender cuál es el comportamiento de disponibilidad normal de {{site.data.keyword.messagehub}} y qué se espera que gestionen las apps.

### API
{: #api_availability notoc}

Como parte del funcionamiento normal de {{site.data.keyword.messagehub}}, los nodos de los clústeres de Kafka se reinician ocasionalmente. En algunos casos, las apps detectarán que el clúster reasigna recursos. Escriba las apps de modo que resistan estos cambios y puedan reconectarse y reintentar operaciones.


### Puentes de {{site.data.keyword.messagehub}}
{: #bridge_availability notoc}

Escriba sus apps para que tengan en cuenta la posibilidad de reinicio ocasional de los puentes.
