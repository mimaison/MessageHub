---

copyright:
  years: 2015, 2017
lastupdated: "2016-11-22"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# O que é necessário para usar a API do MQ Light com o Message Hub?
{: #mql_reqs}

Os requisitos a seguir são necessários para usar a API do {{site.data.keyword.messagehub}}
com o {{site.data.keyword.mql}}: 

**Deve-se criar explicitamente um tópico de Kafka denominado "MQLight" antes de poder usar a API porque todas as mensagens passam pelo tópico "MQLight". Este tópico deve ter uma única partição. A criação deste tópico ativa a API MQ Light para sua instância de serviço. ** Para obter informações adicionais sobre como criar tópicos no {{site.data.keyword.messagehub}}, consulte [Gerenciando tópicos](/docs/services/MessageHub/messagehub070.html).

O tópico "MQLight" é usado pela API MQ Light para armazenar seus dados da mensagem e interagir com outros clientes Kafka. Saiba que, quando este tópico é criado, ele incorre em encargos com a taxa padrão descrita no plano de pagamento dos serviços.

Para desativar a API MQ Light, exclua o tópico "MQLight". Observe que todos os dados foram destruídos quando o tópico foi excluído.
