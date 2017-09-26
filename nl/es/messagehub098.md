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

# ¿Qué se necesita para utilizar la API MQ Light con Message
Hub?
{: #mql_reqs}

Deben cumplirse los requisitos siguientes para utilizar la API {{site.data.keyword.mql}} con {{site.data.keyword.messagehub}}: 

**Debe crear explícitamente un tema llamado "MQLight Kafka" para poder utilizar la API porque todos los mensajes pasan por el tema "MQLight". Este tema tiene una única partición. La creación de este tema habilita la API MQ Light para la instancia de servicio. ** Para obtener más información sobre cómo crear temas de {{site.data.keyword.messagehub}}, consulte [Gestión de temas](/docs/services/MessageHub/messagehub070.html).

La API MQ Light utiliza el tema "MQLight" para almacenar sus datos de mensajes e interactuar con otros clientes de Kafka. Tenga en cuenta que, cuando se crea este tema, se incurre en cargos en la tarifa estándar tal como se describe en el plan de pago de servicios.

Para inhabilitar la API MQ Light, suprima el tema "MQLight". Tenga en cuenta que todos los datos se destruyen cuando se suprime el tema.
