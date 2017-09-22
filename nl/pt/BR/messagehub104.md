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

# Usando o cliente Kafka Java
{: #kafka_using}

## Como usar, fazer download e executar a amostra da API Java Kafka
{: notoc}

A amostra da API Java&trade; Kafka é um exemplo de produtor e consumidor que são gravados em Java, que usa a API Kafka diretamente. É possível executar esta amostra localmente ou no {{site.data.keyword.Bluemix_short}}.

O código de amostra está no [projeto do GitHub message-hub-samples ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}. Embora os usuários de amostra usem a API
Kafka para enviar e receber mensagens, a amostra usa a API de administração do
{{site.data.keyword.messagehub}} para criar o tópico que ela envia mensagens para e recebe
mensagens de.

Para obter informações adicionais sobre a instalação e execução da amostra, consulte [README.md ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-console-sample){:new_window}.

Para obter uma apresentação detalhada de como executar a amostra, consulte [Introdução ao {{site.data.keyword.messagehub}}](/docs/services/MessageHub/index.html#getting_started_steps).

## Como usar, fazer download e executar a amostra do Liberty para Java
{: #liberty_sample notoc}

A amostra do Liberty for Java implementa um aplicativo simples que é implementado no tempo de execução do Liberty. O aplicativo usa a API Kafka para o {{site.data.keyword.messagehub}} produzir e consumir mensagens.
O aplicativo também serve um frontend da web que você pode usar para administração.

É possível localizar o código de amostra no [projeto do GitHub message-hub-samples ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-liberty-sample){:new_window}.

## Como migrar o cliente Kafka da versão 0.9.x para a 0.10.x
{: #kafka_migrate notoc}


Se você estiver usando os clientes Java, agora poderá usar os clientes Kafka 0.10.x disponíveis publicamente. É altamente recomendado mudar da versão 0.9.x para a versão 0.10.x mais recente (atualmente 0.10.2.1). Execute as seguintes etapas:

1. Exclua o módulo jar de login do {{site.data.keyword.messagehub}}.
2. Mude seu arquivo <code>jaas.conf</code> para o seguinte:
    ```
        KafkaClient {
          org.apache.kafka.common.security.plain.PlainLoginModule required serviceName="kafka" username="<your username>" password="<your password>"; };
    ```
    {: codeblock}

3. Inclua esta linha em suas propriedades do consumidor e do produtor: <code>sasl.mechanism=PLAIN</code>


## Usando a propriedade sasl.jaas.config
{: #sasl_prop notoc}
Se estiver usando um cliente Kafka em 0.10.2.1 ou mais recente, será possível usar a
propriedade <code>sasl.jaas.config</code> para a configuração do cliente em vez de um arquivo do
JAAS. Para conectar-se ao {{site.data.keyword.messagehub}}, configure <code>sasl.jaas.config</code>
como segue:
<pre>
<code>    sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required \
    username="USERNAME" \
    password="PASSWORD";</code>
</pre>
{:codeblock}

em que USERNAME e PASSWORD são os valores do {{site.data.keyword.messagehub}} na guia
**Credenciais de serviço** no {{site.data.keyword.Bluemix_notm}}.

Se usar <code>sasl.jaas.config</code>, os clientes em execução na mesma JVM poderão usar credenciais
diferentes. Para obter mais informações, consulte
[Configurando clientes do
Kafka ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://kafka.apache.org/documentation/#security_sasl_plain_clientconfig){:new_window}

## APIs para administração do tópico
{: #topic_admin notoc}

Se estiver usando um cliente do Kafka em 0.11 ou mais recente ou o Streams Kafka em 0.10.2.0 ou
mais recente, será possível utilizar APIs para criar e excluir tópicos. Colocamos algumas restrições nas
configurações permitidas ao criar tópicos. Atualmente, é possível modificar somente as configurações
a seguir:

<dl>
<dt>cleanup.policy</dt>
<dd>Configure para <code>excluir</code> (padrão), <code>compact</code> ou <code>delete,compact</code></dd>
<dt>retention.ms</dt>
<dd>O período de retenção padrão é de 24 horas. O mínimo é uma hora e o máximo é 30 dias. Especifique esse
valor como múltiplos de horas.
<p>**Nota:** se a política de limpeza for somente <code>compact</code>,
incluiremos <code>delete</code> automaticamente, mas desativaremos a exclusão com base no tempo. As mensagens
no tópico são compactadas até 1 GB antes de serem excluídas.</p>
</dd>
</dl>

## Suporte para o Streams Kafka
{: #kafka_streams notoc}

Iniciando com a biblioteca Streams 0.10.2.0, as APIs do tópico agora trabalham com o
{{site.data.keyword.messagehub}} sem configuração necessária. Especifique suas credenciais SASL usando
<code>sasl.jaas.config</code> ou um arquivo JAAS e configure <code>replication.factor</code> para 3.

Por exemplo:

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

em que BOOTSTRAP_SERVERS, USERNAME e PASSWORD são os valores de sua guia
{{site.data.keyword.messagehub}} **Credenciais de serviço** no
{{site.data.keyword.Bluemix_notm}}.

<!--
new topic that includes content from existing topics about samples and migration
-->
