---

copyright:
  years: 2015, 2017
lastupdated: "2017-03-02"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Iniciación a Message Hub
{: #messagehub}


{{site.data.keyword.messagehub_full}} es un bus de mensajes escalable, distribuido y de alto rendimiento que aúna las tecnologías de nube locales y externas. {:shortdesc}

Utilizando {{site.data.keyword.messagehub}}, puede realizar las siguientes tareas:

* Enlazar microservicios gracias a los protocolos abiertos
* Conectar la corriente de datos a los análisis para obtener
información muy valiosa
* Proveer datos de sucesos a múltiples aplicaciones para
reaccionar
en tiempo real.

For example, you can use {{site.data.keyword.messagehub}} to
publish inventory changes, create a centralized bus for real-time data, or enable apps to offload
work to back-end worker processes.

Para empezar con {{site.data.keyword.messagehub}} y empezar a enviar y recibir mensajes, utilice el ejemplo Java™. El ejemplo muestra cómo un productor envía mensajes a un consumidor mediante un tema. Se utiliza el mismo programa de ejemplo para consumir mensajes y producir mensajes.

![Diagrama de la descripción general del ejemplo Java](getting_started_sample.gif "Diagrama con la descripción general del flujo de mensajes del ejemplo Java.")


Siga estos pasos:
{: #getting_started_steps}
 
1. Cree una instancia de servicio {{site.data.keyword.messagehub}}: 

  a. Inicie sesión en {{site.data.keyword.Bluemix_notm}} utilizando la interfaz de usuario web. 
  
  b. Pulse **CATÁLOGO**.
  
  c. En la sección **Servicios de aplicación**, pulse **{{site.data.keyword.messagehub}}**. Se abrirá la página de instancia de servicio de {{site.data.keyword.messagehub}}. 
  
  d. Deje el servicio desenlazado en el menú **Conectar a** y especifique nombres para el servicio y las credenciales correspondientes. Puede usar
los valores predeterminados. 
  
  e. Pulse **Crear**.

2. Si aún no los tiene, instale los requisitos previos siguientes:

    * [git ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://git-scm.com/){:new_window}
	* [Gradle ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://gradle.org/){:new_window}
    * Java 7 o superior
 
3. Clone el repositorio git message-hub-samples ejecutando el siguiente mandato desde la línea de mandatos:

    <pre class="pre">
    git clone https://github.com/ibm-messaging/message-hub-samples.git
    </pre>
	{: codeblock}

4. Cambie el directorio a la consola de java ejecutando el siguiente mandato:

    <pre class="pre">
    cd message-hub-samples/kafka-java-console-sample
    </pre>
	{: codeblock}

5. Ejecute los siguientes mandatos de compilación:

    <pre class="pre">
    gradle clean && gradle build
    </pre>
	{: codeblock}

6. Inicie el consumidor en la consola ejecutando el siguiente mandato:

    <pre class="pre">java -jar build/libs/kafka-java-console-sample-2.0.jar 
	<var class="keyword varname">kafka_brokers_sasl</var> <var class="keyword varname">kafka_admin_url</var> <var class="keyword varname">api_key</var> -consumer</pre>
    {: codeblock}
    
    El ejemplo utiliza un tema denominado `kafka-java-console-sample-topic`. Si el tema ya no existe, el ejemplo lo crea utilizando la API de administración de {{site.data.keyword.messagehub}}. Para enviar y recibir mensajes, el ejemplo utiliza la API Apache Kafka Java.

    Para buscar valores para *kafka_brokers_sasl*, *kafka_admin_url* y *api_key*, vaya a la instancia de {{site.data.keyword.messagehub}} en {{site.data.keyword.Bluemix_notm}}, vaya al separador **Credenciales de servicio** y seleccione las **Credenciales** que desee utilizar.
    
	**Importante:** *kafka_brokers_sasl* debe ser una serie única y debe escribirse entre comillas. Por ejemplo:

    <pre class="pre">
    "host1:port1,host2:port2"
    </pre>
	{: codeblock}

    Se recomienda utilizar todos los hosts Kafka listados en el campo **Credenciales** que ha seleccionado.

7. Inicie el productor en la consola ejecutando el siguiente mandato:
   
    <pre class="pre">java -jar build/libs/kafka-java-console-sample-2.0.jar 
	<var class="keyword varname">kafka_brokers_sasl</var> <var class="keyword varname">kafka_admin_url</var> <var class="keyword varname">api_key</var> -producer</pre>
 {: codeblock}
  
8. Ahora deberían aparecer en el consumidor los mensajes enviados por el productor. A continuación, se muestra una salida de ejemplo:

    ```
    [2016-11-30 17:30:53,492] INFO Running in local mode. (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:53,492] INFO Updating JAAS configuration (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:53,506] INFO Kafka Endpoints: kafka01-prod01.messagehub.services.us-south.bluemix.net:9093,kafka02-prod01.messagehub.services.us-south.bluemix.net:9093,kafka03-prod01.messagehub.services.us-south.bluemix.net:9093,kafka04-prod01.messagehub.services.us-south.bluemix.net:9093,kafka05-prod01.messagehub.services.us-south.bluemix.net:9093 (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:53,506] INFO Admin REST Endpoint: https://kafka-admin-prod01.messagehub.services.us-south.bluemix.net:443 (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:53,506] INFO Creating the topic kafka-java-console-sample-topic (com.messagehub.samples.MessageHubConsoleSample)
    (com.messagehub.samples.MessageHubConsoleSample)e :{}
    [2016-11-30 17:30:54,947] INFO Admin REST Listing Topics: [{"name":"kafka-java-console-sample-topic","partitions":1,"retentionMs":"86400000","markedForDeletion":false}] (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:55,952] INFO [Partition(topic = kafka-java-console-sample-topic, partition = 0, leader = 0, replicas = [0,1,4,], isr = [0,4,1,]] (com.messagehub.samples.ConsumerRunnable)
    [2016-11-30 17:30:55,953] INFO class com.messagehub.samples.ConsumerRunnable is starting. (com.messagehub.samples.ConsumerRunnable)
    [2016-11-30 17:30:57,023] INFO [Partition(topic = kafka-java-console-sample-topic, partition = 0, leader = 0, replicas = [0,1,4,], isr = [0,4,1,]] (com.messagehub.samples.ProducerRunnable)
    [2016-11-30 17:30:57,024] INFO MessageHubConsoleSample will run until interrupted. (com.messagehub.samples.MessageHubConsoleSample)
    [2016-11-30 17:30:57,024] INFO class com.messagehub.samples.ProducerRunnable is starting. (com.messagehub.samples.ProducerRunnable)
    [2016-11-30 17:30:58,018] INFO Message produced, offset: 0 (com.messagehub.samples.ProducerRunnable)
    [2016-11-30 17:30:58,956] INFO No messages consumed (com.messagehub.samples.ConsumerRunnable)
    [2016-11-30 17:31:00,301] INFO Message consumed: ConsumerRecord(topic = kafka-java-console-sample-topic, partition = 0, offset = 1, CreateTime = 1480527060022, checksum = 1906962734, serialized key size = 3, serialized value size = 25, key = key, value = This is a test message #1) (com.messagehub.samples.ConsumerRunnable)
    [2016-11-30 17:31:00,397] INFO Message produced, offset: 1 (com.messagehub.samples.ProducerRunnable)
    [2016-11-30 17:31:02,550] INFO Message consumed: ConsumerRecord(topic = kafka-java-console-sample-topic, partition = 0, offset = 2, CreateTime = 1480527062401, checksum = 3801731428, serialized key size = 3, serialized value size = 25, key = key, value = This is a test message #2) (com.messagehub.samples.ConsumerRunnable)
    ```
	{: codeblock}
	
9. El ejemplo se ejecuta indefinidamente hasta que lo detenga. Para detener el proceso, ejecute un mandato como el siguiente: <code>Control+C</code>


Para obtener más información sobre la ejecución de un ejemplo de {{site.data.keyword.messagehub}} utilizando Python, consulte el artículo [Aplicación de ejemplo de la consola de Python ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/messaging/2017/02/09/new-message-hub-sample-python-console-application/){:new_window}. También puede encontrar ejemplos que ilustran otras API y características en [{{site.data.keyword.messagehub}} samples ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/ibm-messaging/message-hub-samples){:new_window}.

Para ver un vídeo que describe cómo ejecutar un ejemplo de Java en {{site.data.keyword.messagehub}}, consulte [{{site.data.keyword.messagehub}} - Getting started with IBM's Kafka in the cloud ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.youtube.com/watch?v=tt-bLtFzC_4){:new_window}.

