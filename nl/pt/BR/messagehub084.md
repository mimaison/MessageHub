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

# Como migrar o cliente Kafka de 0.9.X para 0.10.X ou 0.11.X
{: #kafka_migrate}


Se você estiver usando os clientes Java, poderá usar os clientes Kafka 0.10.X ou 0.11.X publicamente disponíveis. É altamente recomendado mover da versão 0.9.X para a versão 0.10.X ou 0.11.X mais recente
(todas as versões mais recentes são suportadas). Execute as seguintes etapas:

1. Exclua o módulo jar de login do {{site.data.keyword.messagehub}}.
2. Mude seu arquivo <code>jaas.conf</code> para o seguinte:
    ```
        KafkaClient {
          org.apache.kafka.common.security.plain.PlainLoginModule required serviceName="kafka" username="<your username>" password="<your password>"; };
    ```
    {: codeblock}

3. Inclua esta linha em suas propriedades do consumidor e do produtor: <code>sasl.mechanism=PLAIN</code>


