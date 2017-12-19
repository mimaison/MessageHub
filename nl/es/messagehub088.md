---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-01"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Cómo enlazar con otros servicios utilizando puentes
{: #bridges}

Los puentes son enlaces unidireccionales entre {{site.data.keyword.messagehub}} y otro servicio. Los puentes permiten leer datos desde {{site.data.keyword.messagehub}} y grabarlos en otro servicio, o bien leer datos desde otro servicio y grabarlos en {{site.data.keyword.messagehub}}.
{:shortdesc}

Los principales beneficios de utilizar {{site.data.keyword.messagehub}} puentes son los siguientes:  

* Puede definir puentes administrativamente, por lo que no es necesario escribir código de aplicación.
* El ciclo de cada puente es supervisado y gestionado por el servicio {{site.data.keyword.messagehub}}. Por ejemplo, si un puente encuentra un error, se reinicia automáticamente mediante {{site.data.keyword.messagehub}}.
* Los puentes se integran con la plataforma {{site.data.keyword.Bluemix_short}}. Por ejemplo, la información de registro y supervisión generada por los puentes se direcciona a los paneles Kibana y Grafana.

Puede encontrar puentes útiles en los siguientes dos escenarios comunes:

* Consumo de datos de uno o varios orígenes de datos en {{site.data.keyword.messagehub}}.
* Transferencia de datos de {{site.data.keyword.messagehub}} a otro servicio. Por ejemplo, para el almacenamiento a largo plazo.

## Puentes de {{site.data.keyword.messagehub}}
{: notoc}

* Proporcionamos los dos siguientes tipos de puente: 
  - El puente de MQ, que obtiene datos de mensajes de {{site.data.keyword.IBM}} MQ y los transfiere a un tema en {{site.data.keyword.messagehub}}. A largo plazo, tenemos la intención de dar soporte a una variedad más amplia de puentes.
  - El puente de {{site.data.keyword.objectstorageshort}}, que transfiere datos de {{site.data.keyword.messagehub}} a la instancia del [servicio de Object Storage![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/services/ObjectStorage/index.html){:new_window}.
* Actualmente, los puentes están disponibles en todos los entornos públicos de {{site.data.keyword.Bluemix_notm}}. Los puentes no están disponibles en {{site.data.keyword.Bluemix_short}} Dedicated.
* Puede administrar puentes de las dos formas siguientes:
  - Utilizando una [API REST ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/ibm-messaging/message-hub-docs){:new_window}, que es la ampliación de la API de administración de {{site.data.keyword.messagehub}} existente. Encontrará ejemplos sobre cómo utilizar de curl para gestionar el ciclo de vida de los puentes en [message-hub-docs ![Icono de mensaje externo](../../icons/launch-glyph.svg "Icono de mensaje externo")](https://github.com/ibm-messaging/message-hub-docs){:new_window}. Es posible que, durante el desarrollo de puentes, esta API REST cambie. Intentaremos estabilizar esta API.
  - Uso del panel de control de {{site.data.keyword.messagehub}} en la consola de {{site.data.keyword.Bluemix_notm}}.
* Puede asociar un máximo de dos puentes de cualquier tipo con una instancia del servicio de {{site.data.keyword.messagehub}}. Durante el desarrollo de puentes, revisaremos esta limitación.
* No hay cargos adicionales por utilizar puentes con operaciones distintas a las de mensajería.
* El puente de MQ no da soporte al uso de SSL/TLS para proteger la privacidad y la integridad de los datos que se transfieren entre el puente y el gestor de colas de MQ. Tenemos la intención de añadir soporte para el uso de SSL/TLS en el puente. 
* El puente de {{site.data.keyword.objectstorageshort}} concatena mensajes utilizando caracteres de nueva línea como separadores a medida que graba los datos en {{site.data.keyword.objectstorageshort}}. Por este motivo, el puente no es apto para los mensajes que contienen caracteres de línea incluida y datos para mensajes binarios.
* Las convenciones de nomenclatura de objetos que utiliza actualmente el puente de {{site.data.keyword.objectstorageshort}} podrían cambiar en el futuro.

Sin embargo, puede utilizar el servicio de [{{site.data.keyword.SecureGatewayfull}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/services/SecureGateway/secure_gateway.html){:new_window} para enviar los datos a través de un túnel seguro entre {{site.data.keyword.Bluemix_notm}} y un cliente {{site.data.keyword.SecureGateway}} que se puede instalar localmente. En esta configuración, la comunicación en los extremos del túnel no está protegida mediante SSL/TLS.
