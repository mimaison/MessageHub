---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-26"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Utilización de KSQL con Message Hub
{: #ksql_using}

Puede utilizar [KSQL ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/confluentinc/ksql){:new_window} con {{site.data.keyword.messagehub}} para el proceso de secuencias. Siga estos pasos: 

1. Cree un archivo de configuración de KSQL de {{site.data.keyword.messagehub}} KSQL. 

    Por ejemplo:
    ```
    bootstrap.servers=HOSTNAME:PORTNUMBER
    application.id=ksql_server_quickstart
    ksql.command.topic.suffix=commands
    listeners=http://localhost:8080
    security.protocol=SASL_SSL
    sasl.mechanism=PLAIN
    ssl.protocol=TLSv1.2
    ssl.enabled.protocols=TLSv1.2
    sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required username="USERNAME" password="PASSWORD";
    ksql.sink.replications.default=3
    ```
    Asegúrese de editar las siguientes líneas para insertar sus propios datos:
	- <code>bootstrap.servers</code> - inserte todos los hosts Kafka que aparecen en la página **Credenciales de servicio**. Para encontrar esta información, vaya a la instancia de {{site.data.keyword.messagehub}} en {{site.data.keyword.Bluemix_notm}}, vaya al separador **Credenciales de servicio** y seleccione las **Credenciales** que desee utilizar.
	- <code>sasl.jaas.config</code> - inserte su par de nombre de usuario y contraseña
	
2. Utilice el panel de control de {{site.data.keyword.messagehub}} de la consola de {{site.data.keyword.Bluemix_notm}} para crear un tema denominado <code>ksql__commands</code> con una sola partición y el periodo de retención predeterminado. 
3. En un terminal Docker, inicie KSQL con el siguiente mandato: 
<pre class="pre">/bin/ksql-cli local
--<var class="keyword varname">properties-file</var> ./config/ksqlserver.properties
</pre>
4. Para especificar datos, edite la clase <code>DataGen</code> en <code>io.confluent.ksql.datagen</code> en el proyecto <code>ksql-examples</code>. Por ejemplo:
```
     Properties props = new Properties();
     props.put("bootstrap.servers", arguments.bootstrapServer);
     props.put("client.id", "KSQLDataGenProducer");
     props.put("security.protocol", "SASL_SSL");
     props.put("sasl.mechanism", "PLAIN");
     props.put("ssl.protocol", "TLSv1.2");
     props.put("ssl.enabled.protocols", "TLSv1.2");
     props.put("sasl.jaas.config", "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"USERNAME\" password=\"PASSWORD\";");
```
    {: codeblock}
5. Utilice el panel de control de {{site.data.keyword.messagehub}} de la consola de {{site.data.keyword.Bluemix_notm}} para crear dos temas con una partición cada uno: <code>users</code> y <code>pageviews</code>. 

    Luego inicie <code>DataGen</code> dos veces del siguiente modo: 
	
    i. Con <code>bootstrap-server=HOSTNAME:PORTNUMBER quickstart=users format=json topic=users maxInterval=10000</code> para empezar a crear sucesos de <code>users</code>. 
	
    ii. Con <code>bootstrap-server=HOSTNAME:PORTNUMBER quickstart=pageviews format=delimited topic=pageviews maxInterval=10000</code> para empezar a crear sucesos de <code>pageviews</code>. 
	
	Asegúrese de insertar todos los hosts Kafka que aparecen en la página **Credenciales de servicio** como valores correspondientes a <code>bootstrap-server</code>. Para encontrar esta información, vaya a la instancia de {{site.data.keyword.messagehub}} en {{site.data.keyword.Bluemix_notm}}, vaya al separador **Credenciales de servicio** y seleccione las **Credenciales** que desee utilizar.

Cuando finalice estos pasos, puede ejecutar todas las consultas que se muestran en la [guía de inicio rápido de KSQL ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/confluentinc/ksql/tree/0.1.x/docs/quickstart#create-a-stream-and-table){:new_window}

