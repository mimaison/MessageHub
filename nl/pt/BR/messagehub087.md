---

copyright:
  years: 2015, 2017
lastupdated: "2017-01-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Escolhendo entre as três APIs
{: #choose_api}

O {{site.data.keyword.messagehub}} suporta três APIs. A seguir há algumas informações para ajudá-lo
a escolher o que é mais apropriado:

## Por que usar a API Kafka?
{: #why_kafka notoc}

Existem algumas razões pelas quais você pode escolher usar a API Kafka em vez
de outras interfaces fornecidas pelo {{site.data.keyword.messagehub}}. Algumas dessas razões são as seguintes:
{:shortdesc}


* É mais fácil integrar seu aplicativo com sistemas existentes que possuam o suporte para Kafka, por
exemplo, {{site.data.keyword.IBM}} {{site.data.keyword.streaminganalyticsshort}} e {{site.data.keyword.sparks}}.
* Ela oferece latência inferior e rendimento mais alto do que as outras APIs.
* Oferece uma API mais detalhada do que a API REST Kafka.


## Por que usar a API {{site.data.keyword.mql}}?
{: #why_mql notoc}

A API {{site.data.keyword.mql}} fornece um nível mais alto de abstração do que a API Kafka. O {{site.data.keyword.mql}} permite que aplicativos sejam gravados de maneira rápida e portátil em um modelo de sistema de mensagens unificado que suporta padrões de sistema de mensagens de fila e de publicação/assinatura. 
{:shortdesc}

Os aplicativos trocam mensagens usando destinos criados dinamicamente, os quais você pode estruturar hierarquicamente (por exemplo, <code>‘/sports/football’</code>), agrupar usando curingas (por exemplo,
<code>‘/sports/#’</code>) e tenha controles simples para garantia de entrega e validação de mensagem.
Isso permite implementar cenários como a transferência do trabalhador, a notificação de eventos e o processamento em lote diretamente.

Bem como enviar mensagens entre outros aplicativos usando a API {{site.data.keyword.mql}}, também é possível trocar mensagens com aplicativos que usam as APIs Kafka REST ou Kafka. Como alternativa, também é possível usar aplicativos no local com o {{site.data.keyword.IBM_notm}} MQ.


## Por que usar a API REST Kafka?
{: #why_rest notoc}

A API REST do Kafka é uma interface conveniente que pode ser usada nas situações a
            seguir:  

* Em que um desenvolvedor deseja iniciar rapidamente usando o
{{site.data.keyword.messagehub}}
* Em determinados casos de uso de baixo rendimento em que a latência não é um fator crítico
* Para depuração e descoberta de falhas

A API REST do Kafka não foi planejada como uma interface de alto rendimento e baixa latência.​Para esses tipos de requisitos, recomendamos o uso da API Kafka para conectar-se ao {{site.data.keyword.messagehub}} e por meio dele. Para obter informações adicionais, consulte [Usando um cliente Kafka](/docs/services/MessageHub/messagehub050.html#kafka_client).












