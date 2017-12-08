---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-02"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Usando o Kafka Connect com o {{site.data.keyword.messagehub}}
{: #kafka_connect }

É possível usar o Kafka Connect com o {{site.data.keyword.messagehub}} e executar os trabalhadores dentro ou fora do {{site.data.keyword.Bluemix_short}}.

O Kafka Connect pode ser executado nos modos independente ou distribuído. O modo independente
é destinado a testes e conexões temporários entre os sistemas. O modo distribuído é mais apropriado para uso em produção. A configuração requerida para usar o {{site.data.keyword.messagehub}} com esses dois modos é um pouco diferente.
{:shortdesc}

## Configuração do trabalhador independente
{: #standalone_worker notoc}

Deve-se fornecer os servidores de autoinicialização e informações das credenciais SASL no
arquivo de propriedades do trabalhador fornecido quando você iniciar um trabalhador independente Kafka Connect.

O trabalhador independente não usa nenhum tópico interno. Em vez disso, ele usa um arquivo
para armazenar informações de compensação.

### Conector de origem
{: #source_connector notoc }

O exemplo a seguir lista as propriedades que devem ser fornecidas em seu arquivo de propriedades:

<pre>
<code>
  bootstrap.servers=KAFKA_BROKERS_SASL
  producer.sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule username necessário="USER" password="PASSWORD";
  producer.security.protocol=SASL_SSL
  producer.sasl.mechanism=PLAIN
  producer.ssl.protocol=TLSv1.2
  producer.ssl.enabled.protocols=TLSv1.2
  producer.ssl.endpoint.identification.algorithm=HTTPS
</code>
</pre>
{:codeblock}

Substitua KAFKA_BROKERS_SASL, USER e PASSWORD pelos valores de sua guia {{site.data.keyword.messagehub}} **Credenciais de serviço** no console do {{site.data.keyword.Bluemix_notm}}.

### Conector sink
{: #sink_connector }

O exemplo a seguir lista as propriedades que devem ser fornecidas em seu arquivo de propriedades:

<pre>
<code>
  bootstrap.servers=KAFKA_BROKERS_SASL
  consumer.sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule username necessário="USER" password="PASSWORD";
  consumer.security.protocol=SASL_SSL
  consumer.sasl.mechanism=PLAIN
  consumer.ssl.protocol=TLSv1.2
  consumer.ssl.enabled.protocols=TLSv1.2
  consumer.ssl.endpoint.identification.algorithm=HTTPS
</code>
</pre>
{:codeblock}

Substitua KAFKA_BROKERS_SASL, USER e PASSWORD pelos valores de sua guia {{site.data.keyword.messagehub}} **Credenciais de serviço** no console do {{site.data.keyword.Bluemix_notm}}.

## Configuração do trabalhador distribuído
{: #distributed_worker notoc}

Deve-se fornecer os servidores de autoinicialização e informações das credenciais SASL no
arquivo de propriedades fornecido quando você iniciar os trabalhadores distribuídos Kafka Connect. O exemplo a seguir lista as propriedades que devem ser fornecidas em seu arquivo de propriedades:

<pre>
<code>
  bootstrap.servers=KAFKA_BROKERS_SASL
  sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule username necessário="USER" password="PASSWORD";
  security.protocol=SASL_SSL
  sasl.mechanism=PLAIN
  ssl.protocol=TLSv1.2
  ssl.enabled.protocols=TLSv1.2
  ssl.endpoint.identification.algorithm=HTTPS
</code>
</pre>
{:codeblock}

Substitua KAFKA_BROKERS_SASL, USER e PASSWORD pelos valores de sua guia {{site.data.keyword.messagehub}} **Credenciais de serviço** no console do {{site.data.keyword.Bluemix_notm}}.

Se você desejar usar um conector de origem, também deverá especificar a configuração SSL e SASL para o produtor, conforme a seguir:

<pre>
<code>
  producer.sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule username necessário="USER" password="PASSWORD";
  producer.security.protocol=SASL_SSL
  producer.sasl.mechanism=PLAIN
  producer.ssl.protocol=TLSv1.2
  producer.ssl.enabled.protocols=TLSv1.2
  producer.ssl.endpoint.identification.algorithm=HTTPS
</code>
</pre>
{:codeblock}

Se você desejar usar um conector sink, também deverá especificar a configuração SSL e SASL para o consumidor, conforme a seguir:

<pre>
<code>
  consumer.sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule username necessário="USER" password="PASSWORD";
  consumer.security.protocol=SASL_SSL
  consumer.sasl.mechanism=PLAIN
  consumer.ssl.protocol=TLSv1.2
  consumer.ssl.enabled.protocols=TLSv1.2
  consumer.ssl.endpoint.identification.algorithm=HTTPS
</code>
</pre>
{:codeblock}

Além disso, o Kafka Connect no modo distribuído usa três tópicos internamente. Esses tópicos
são criados automaticamente quando um trabalhador é inicializado, desde que você use o Kafka Connect
no Apache Kafka versão 0.11 ou mais recente. Você fornece os nomes dos tópicos como parâmetros de
configuração. Assegure-se de que os valores sejam os mesmos para todos os trabalhadores com o mesmo valor de configuração `group.id`.

| Configuração               | Descrição                                                         |
| --------------------------- | ------------------------------------------------------------------- |
| `offset.storage.topic`      | Tópico de deslocamentos do Conector                |
| `offset.storage.partitions` | Número de partições para o tópico de deslocamentos do conector (padrão 25) |
| `config.storage.topic`      | Tópico de configuração do conector    |
| `status.storage.topic`      | Tópico de status do conector                                 |
| `status.storage.partitions` | Número de partições para o tópico de status do conector (padrão 5)          |

Por exemplo, é possível usar os seguintes pares chave-valor em seu arquivo de propriedades:

<pre>
<code>
  offset.storage.topic=connect-offsets
  config.storage.topic=connect-configs
  status.storage.topic=connect-status
</code>
</pre>
{:codeblock}

Considere reduzir o número de partições se você estiver fazendo somente um uso leve do Kafka Connect.



