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

# Como migrar o cliente Kafka da versão 0.9.x para a 0.10.x
{: #kafka_migrate}


Se você estiver usando os clientes Java, agora poderá usar os clientes Kafka 0.10.x disponíveis publicamente. É altamente recomendado mudar da versão 0.9.x para a versão 0.10.x mais recente (atualmente 0.10.2.1). Execute as seguintes etapas:

1. Exclua o módulo jar de login do {{site.data.keyword.messagehub}}.
2. Mude seu arquivo <code>jaas.conf</code> para o seguinte:
    ```
        KafkaClient {
          org.apache.kafka.common.security.plain.PlainLoginModule required serviceName="kafka" username="<your username>" password="<your password>"; };
    ```
    {: codeblock}

3. Inclua esta linha em suas propriedades do consumidor e do produtor: <code>sasl.mechanism=PLAIN</code>


