---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-11"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Cómo se migra el cliente Kafka de 0.9.X a 0.10.X o 0.11.X
{: #kafka_migrate}


Si utiliza clientes Java, ahora puede utilizar los clientes Kafka 0.10.X o 0.11.X disponibles públicamente. Se recomienda encarecidamente actualizar la versión 0.9.X a la última versión 0.10.X o 0.11.X (damos soporte a todas las versiones más nuevas). Siga estos pasos: 

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


