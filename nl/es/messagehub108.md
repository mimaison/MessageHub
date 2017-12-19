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

# Preguntas más frecuentes sobre {{site.data.keyword.messagehub}}
{: #faqs}

Respuestas a preguntas comunes acerca del servicio {{site.data.keyword.IBM}} {{site.data.keyword.messagehub}}.

<!--17/10/17 - Karen: same info duplicated at messagehub104 -->
## ¿Cómo se utilizan las API de Kafka para crear y suprimir temas?
{: #topic_admin notoc}

Si está utilizando un cliente Kafka de la versión 0.11 o posterior, o bien Streams Kafka versión 0.10.2.0 o posterior, puede utilizar la API para crear y suprimir temas. Existen varias restricciones para la configuración permitida al crear temas. Actualmente, solo se pueden modificar los siguientes valores:

<dl>
<dt>cleanup.policy</dt>
<dd>Establezca este valor en <code>delete</code> (predeterminado), <code>compact</code> o <code>delete,compact</code></dd>
<dt>retention.ms</dt>
<dd>El período de retención predeterminado es de 24 horas. El valor mínimo es de 1 hora y el máximo de 30 días.
Especifique este valor como múltiplo de horas.<p>**Nota:**
si la política de limpieza es solo <code>compact</code>, se añade automáticamente <code>delete</code>, pero se inhabilita la supresión en función del tiempo. Los mensajes del tema se compactan a 1 GB antes de la supresión.</p>
</dd>
</dl>

## ¿Durante cuánto tiempo establece {{site.data.keyword.messagehub}} la ventana de retención de registros para el tema de desplazamientos de consumidor?
{: #offsets notoc}
{{site.data.keyword.messagehub}} retiene los desplazamientos de consumidor durante 7 días. Esto corresponde al valor de configuración de Kafka offsets.retention.minutes. 

La retención de desplazamiento abarca todo el sistema y no se puede establecer en temas individuales. Todos los grupos de consumidores obtienen solo 7 días de desplazamientos almacenados, aunque utilicen un tema con una retención de registro que se ha aumentado al máximo de 30 días.  

## ¿Cuál es el comportamiento de la disponibilidad de {{site.data.keyword.messagehub}}?
{: #availability notoc}

Si escribe apps de {{site.data.keyword.messagehub}}, utilice esta información para comprender cuál es el comportamiento de disponibilidad normal de {{site.data.keyword.messagehub}} y qué se espera que gestionen las apps.

### API
{: #api_availability notoc}

Como parte del funcionamiento normal de {{site.data.keyword.messagehub}}, los nodos de los clústeres de Kafka se reinician ocasionalmente. En algunos casos, las apps detectarán que el clúster reasigna recursos. Escriba las apps de modo que resistan estos cambios y puedan reconectarse y reintentar operaciones.


### Puentes de {{site.data.keyword.messagehub}}
{: #bridge_availability notoc}

Escriba sus apps para que tengan en cuenta la posibilidad de reinicio ocasional de los puentes.
