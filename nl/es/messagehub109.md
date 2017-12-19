---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-19"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}



# Notificación de un problema al equipo de {{site.data.keyword.messagehub}}
{: #report_problem}

Si tiene problemas con {{site.data.keyword.messagehub}}, compruebe primero la página de estado de [{{site.data.keyword.Bluemix_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/status){:new_window}. 

Si desea ayuda del equipo de {{site.data.keyword.messagehub}}, recopile tanta de la siguiente información como sea posible:{:shortdesc}

1. ¿En qué región de {{site.data.keyword.Bluemix_notm}} se ha suministrado la instancia de {{site.data.keyword.messagehub}}? Por ejemplo, en el sur de Estados Unidos o en el Reino Unido. 
2. ¿Qué interfaz presenta problemas? REST, Kafka, AMQP o los puentes
3. ¿Cuándo se produjo el primer problema (específicamente hora, fecha y huso horario)? ¿Cuánto tiempo estuvo ejecutando la app antes del problema?
4. ¿El problema sigue ocurriendo? ¿Lo puede replicar?
5. ¿Qué ID de instancia del servicio {{site.data.keyword.messagehub}} está utilizando? Puede encontrar este ID buscando en el campo "instance_id" en el JSON VCAP_SERVICES del servicio.
6. ¿Qué cliente Kafka o REST utiliza la aplicación? ¿Cuáles son los detalles de la versión?
7. ¿Cuáles son los detalles de la configuración de cliente?
8. ¿Hay fragmentos del registro de aplicaciones con el mismo problema?
9. ¿Cuál es el problema que ve? ¿Qué temas, ID de cliente e ID de grupo se han visto afectados?
10. ¿Qué impacto tiene el problema en el servicio?


Puede proporcionar la información que ha obtenido a IBM en una incidencia de soporte [mediante el envío de una solicitud de soporte ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/support/index.html#open-ticket).










