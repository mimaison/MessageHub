---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-26"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Uso de la API REST Kafka
{: #rest_using}

La API REST Kafka proporciona una interfaz RESTful a
un clúster Kafka. Mediante la API, se pueden producir y consumir mensajes fácilmente y realizar tareas de administración. Para los documentos de referencia, consulte [ Confluent ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://docs.confluent.io/2.0.0/){:new_window}. Para solicitudes y respuestas en {{site.data.keyword.messagehub}}, solo se admite el
formato compacto binario. No se da soporte a los formatos incorporado Avro y JSON. 

Si utiliza CURL, puede utilizar un ejemplo como el siguiente para generar: 
<pre class="pre"><code>
curl -X POST -H "X-Auth-Token:<var class="keyword varname">APIKEY</var>" -H "Content-Type: application/vnd.kafka.binary.v1+json" <var class="keyword varname">kafka-rest endpoint</var>/topics/<var class="keyword varname">nombre tema</var> -d

'
{
  "records": [
    {
      "value": "<var class="keyword varname">Serie de valor codificado en base 64</var>"
    }
  ]
}
'
</code></pre>
{: codeblock}

Si utiliza CURL, puede utilizar un ejemplo como el siguiente para consumir: 
<pre class="pre"><code>
curl -X GET -H "X-Auth-Token:<var class="keyword varname">APIKEY</var>" -H "Accept: application/vnd.kafka.binary.v1+json" <var class="keyword varname">kafka-rest endpoint</var>/topics/<var class="keyword varname">nombre tema</var>/partitions/<var class="keyword varname">partition ID</var>/messages?offset=<var class="keyword varname">desplazamiento desde el que empezar</var>
</code></pre>
{: codeblock}


Para CURL, también puede adaptar los ejemplos de código detallados en [Confluent docs ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://docs.confluent.io/2.0.0/){:new_window} añadiendo la siguiente línea a la línea de mandatos:
<pre class="pre">-H "X-Auth-Token: <var class="keyword varname">APIKEY</var>"</pre>
{: codeblock}


<!-- Comment from Andrew
basic introduction, definitely including health warning
-->

