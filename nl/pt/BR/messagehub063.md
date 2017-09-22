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

# Como conectar e autenticar
{: #kafka_connect}


Para conectar-se ao {{site.data.keyword.messagehub}}, a API do Kafka usa as 
```kafka_brokers_sasl
``` 
credenciais e o
```
usuário
```
 e

 ```password
```
 no [VCAP_SERVICES environment variable](/docs/services/MessageHub/messagehub071.html).

## Conectando e autenticando em um aplicativo diferente do Java
{: #kafka_notjava notoc}

O serviço {{site.data.keyword.messagehub}} atualmente autentica clientes usando SASL PLAIN. As credenciais são
transportadas uma conexão criptografada.
Este é um novo recurso incluído no Kafka 0.10.0.X. Qualquer cliente que suporta Kafka 0.10 com SASL PLAIN deve
trabalhar com {{site.data.keyword.messagehub}}. Os clientes de exemplo são os seguintes:

* [librdkafka ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/edenhill/librdkafka/){:new_window} 
* [confluent-kafka-python ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/confluentinc/confluent-kafka-python){:new_window}

Se estiver usando um cliente Kafka 0.9.0.0 ou anterior, será necessário usar um módulo de login
customizado, que pode ser transferido por download do módulo de login [{{site.data.keyword.messagehub}}
![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-messaging/message-hub-samples/blob/master/kafka-0.9/message-hub-login-library/messagehub.login-1.0.0.jar){:new_window}. 

