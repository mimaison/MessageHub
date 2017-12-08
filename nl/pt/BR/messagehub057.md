---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-05"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Restrições conhecidas
{: #restrictions}


##Tópicos e partições
{: #topics_partitions notoc}

*  Os nomes dos tópicos são restritos a um máximo de 100 caracteres.
*  O número padrão de partições para um tópico é um.
*  Cada espaço do {{site.data.keyword.Bluemix_notm}} possui um limite de 100 partições. Para criar
                    mais partições, deve-se usar um novo espaço do {{site.data.keyword.Bluemix_notm}}.

## Retenção de mensagem
{: #message_retention}

Por padrão, as mensagens são retidas no Kafka por até 24 horas e cada partição é limitada a 1 GB. Se um valor máximo de 1 GB for atingido, as mensagens mais antigas serão descartadas para permanecerem
no limite.

É possível mudar o limite de tempo para retenção mensagem ao criar um tópico usando a interface
com o usuário ou a API de administração. O limite de tempo é um mínimo de uma hora e um máximo de 30 dias.

## Criando e excluindo tópicos no Kafka
{: #create_delete notoc}

No Kafka, a criação e a exclusão de tópico são operações assíncronas que podem levar algum tempo
para serem concluídas. É recomendável evitar o uso de padrões que dependam da rápida criação e exclusão
de tópicos ou da rápida exclusão e recriação de tópicos.

## API REST Kafka
{: #trouble_rest notoc}

*  Somente o formato integrado binário é suportado para solicitações e respostas. Os formatos integrados do Avro e JSON não são suportados.
*  Solicitações simultâneas não são suportadas para uma instância do consumidor.
   Solicitações de leitura, confirmação
                    ou exclusão correspondentes a uma instância do consumidor devem ser enviadas somente após uma
                    resposta ser recebida para quaisquer solicitações pendentes dessa instância.

## Limitação de taxa da API de REST do Kafka
{: #kafka_rate notoc}

Os aplicativos que usam a API de REST do Kafka podem estar sujeitos à limitação de taxa para cada
ApiKey. Quando esta limitação ocorre, a API responde com o erro HTTP a seguir:

<code>429 Too Many Requests</code>
{:screen}

Se este erro ocorrer, aguarde e envie a solicitação novamente.

## Reinício diário da API de REST do Kafka
{: #rest_restart notoc}

A API de REST do Kafka reinicia uma vez por dia por um curto período de tempo. Durante esse período, a
API de REST do Kafka pode se tornar indisponível. Se isso acontecer, é recomendado tentar novamente
sua solicitação. Após a API de REST ser reiniciada, será necessário recriar suas instâncias do consumidor
do Kafka. Se este for o caso, a API de REST retornará o JSON a seguir:

```'{"error_code":40403,"message":"Consumer instance not found."}'
```
{:screen}

## API de consumidor de alto nível Kafka
{: #kafka_consumer notoc}

Não é possível usar Apache Kafka 0.8.2 simples ou a API de consumidor de alto nível com o {{site.data.keyword.messagehub}}. Em vez disso, é possível usar a API de consumidor Kafka
mais antiga suportada, que é a API do consumidor 0.9.
