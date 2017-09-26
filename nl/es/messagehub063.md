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

# Cómo conectarse y autenticarse
{: #kafka_connect}


Para conectarse a {{site.data.keyword.messagehub}}, la API Kafka utiliza 
```kafka_brokers_sasl
``` 
las credenciales y
```
el usuario
```
y

 ```password
```
 la contraseña de [VCAP_SERVICES environment variable](/docs/services/MessageHub/messagehub071.html).

## Connecting and authenticating in an application other than Java
{: #kafka_notjava notoc}

El servicio de {{site.data.keyword.messagehub}} actualmente autentica a sus clientes utilizando SASL PLAIN. Las credenciales se envía a través de una conexión cifrada. Esta es una nueva característica añadida en Kafka 0.10.0.X. Cualquier cliente que soporte Kafka 0.10 con SASL PLAIN debe trabajar con {{site.data.keyword.messagehub}}. Los clientes de ejemplo son los siguientes:
* [librdkafka ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/edenhill/librdkafka/){:new_window} 
* [confluent-kafka-python ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/confluentinc/confluent-kafka-python){:new_window} 

If you are using the earlier Kafka 0.9.0.0 client, you need to use a custom login module, which you
can download from [{{site.data.keyword.messagehub}} login module ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-messaging/message-hub-samples/blob/master/kafka-0.9/message-hub-login-library/messagehub.login-1.0.0.jar){:new_window}. 

