---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-03"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Uso del cliente Kafka Java
{: #kafka_using}

## Cómo utilizar, descargar y ejecutar el ejemplo de la API Java Kafka
{: notoc}

La API Java&trade; Kafka es una muestra de productor y consumidor escrita en Java, que utiliza directamente la API Kafka. Este ejemplo puede ejecutarse de manera local o en {{site.data.keyword.Bluemix_short}}.

El código de ejemplo está en [message-hub-samples GitHub project ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}.A pesar de que el ejemplo
utiliza la API Kafka para enviar y recibir mensajes, el
ejemplo utiliza la API de administración de
{{site.data.keyword.messagehub}}
para crear un tema desde el cual envía y recibe mensajes. 

Para obtener más información sobre cómo configurar y ejecutar el ejemplo, consulte [README.md ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}.

Para obtener una explicación detallada sobre cómo ejecutar el ejemplo, consulte [Iniciación a {{site.data.keyword.messagehub}}](/docs/services/MessageHub/index.html#getting_started_steps).

## Cómo utilizar, descargar y ejecutar el ejemplo de Liberty for Java
{: #liberty_sample notoc}

El ejemplo de Liberty for Java implementa una aplicación simple que se despliega en el tiempo de ejecución de Liberty. La aplicación utiliza la API Kafka para que {{site.data.keyword.messagehub}} produzca y consuma mensajes. La aplicación también sirve un frontal web que se puede utilizar para la administración.

El código de ejemplo está en el [proyecto GitHub message-hub-samples ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-liberty-sample){:new_window}.

## Cómo migrar el cliente Kafka de 0.9.x a 0.10.x
{: #kafka_migrate notoc}


Si está utilizando los clientes Java, ahora puede utilizar los clientes Kafka 0.10.x disponibles públicamente. Se recomienda encarecidamente actualizar la versión 0.9.x a la última versión 0.10.x (actualmente 0.10.2.1). Siga estos pasos: 

1. Suprimir el módulo jar de inicio de sesión de {{site.data.keyword.messagehub}}.
2. Cambie el archivo <code>jaas.conf</code> de la siguiente forma:
    ```
        KafkaClient {
          org.apache.kafka.common.security.plain.PlainLoginModule required
          serviceName="kafka"
            username="<your username>"
            password="<your password>";
        };
    ```
    {: codeblock}

3. Añada esta línea a las propiedades de consumidor y productor: <code>sasl.mechanism=PLAIN</code>


## Uso de la propiedad sasl.jaas.config
{: #sasl_prop notoc}
Si está utilizando un cliente Kafka de la versión 0.10.2.1 o posterior, puede utilizar la propiedad <code>sasl.jaas.config</code> para la configuración del cliente en lugar de un archivo JAAS. Para conectarse a {{site.data.keyword.messagehub}}, establezca <code>sasl.jaas.config</code> de la siguiente manera:
<pre>
<code>    sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required \
    username="USERNAME" \
    password="PASSWORD";</code>
</pre>
{:codeblock}

donde USERNAME y PASSWORD son los valores del separador de {{site.data.keyword.messagehub}} **Credenciales de servicio** en {{site.data.keyword.Bluemix_notm}}.

Si utiliza <code>sasl.jaas.config</code>, los clientes que se ejecuten en la misma JVM podrán utilizar credenciales diferentes. Para obtener más información, consulte [Configuración de clientes Kafka ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://kafka.apache.org/documentation/#security_sasl_plain_clientconfig){:new_window}

## API para la administración de temas
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

## Soporte para secuencias de Kafka
{: #kafka_streams notoc}

A partir de la biblioteca Streams 0.10.2.0, el tema de API funciona con {{site.data.keyword.messagehub}} sin necesidad de configuración. Especifique sus credenciales SASL utilizando <code>sasl.jaas.config</code> o un archivo JAAS y establezca <code>replication.factor</code> en 3.

Por ejemplo:

<pre>
<code>
    props.put(StreamsConfig.REPLICATION_FACTOR_CONFIG, "3");
    props.put(StreamsConfig.BOOTSTRAP_SERVERS_CONFIG, BOOTSTRAP_SERVERS);
    props.put("security.protocol","SASL_SSL");
    props.put("sasl.mechanism","PLAIN");
    props.put("ssl.protocol","TLSv1.2");
    props.put("ssl.enabled.protocols","TLSv1.2");
    props.put("sasl.jaas.config","org.apache.kafka.common.security.plain.PlainLoginModule required username=\"USERNAME\" password=\"PASSWORD\";");
</code>
</pre>
{:codeblock}

donde BOOTSTRAP_SERVERS, USERNAME y PASSWORD son los valores del separador {{site.data.keyword.messagehub}} **Credenciales de servicio** en {{site.data.keyword.Bluemix_notm}}.

<!--
new topic that includes content from existing topics about samples and migration
-->
