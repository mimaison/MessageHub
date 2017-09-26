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

# Cómo conectarse y autenticarse
{: #rest_connect}

Para conectarse a {{site.data.keyword.messagehub}}, la API REST Kafka utiliza las credenciales <code>api_key</code> y <code>kafka_rest_url</code> de la variable de entorno [VCAP_SERVICES](/docs/services/MessageHub/messagehub071.html).

Para autenticarse con la API REST Kafka {{site.data.keyword.messagehub}}, debe
                especificar <code>api_key</code> en el encabezado X-Auth-Token de sus
                solicitudes.
