---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Perguntas mais frequentes do {{site.data.keyword.messagehub}}
{: #faqs}

Respostas para perguntas comuns sobre o serviço do {{site.data.keyword.IBM}}
{{site.data.keyword.messagehub}}.

<!--17/10/17 - Karen: same info duplicated at messagehub104 -->
## Como uso as APIs Kafka para criar e excluir tópicos?
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

## Por quanto tempo o {{site.data.keyword.messagehub}} configura a janela de retenção de log para o tópico de compensações do consumidor?
{: #offsets notoc}
O {{site.data.keyword.messagehub}} retém as compensações do consumidor por sete dias. Isso corresponde
à configuração offsets.retention.minutes do Kafka. 

A retenção de compensação é feita no sistema inteiro, portanto, não é possível configurá-la
em um nível de tópico individual. Todos os grupos de consumidores obtêm somente 7 dias de compensações armazenadas, mesmo se usando um tópico com uma retenção de log que foi aumentada para
o máximo de 30 dias. 

## O que é comportamento de disponibilidade do {{site.data.keyword.messagehub}}?
{: #availability notoc}

Se você gravar aplicativos do {{site.data.keyword.messagehub}}, use estas informações para
entender o que é um comportamento normal de disponibilidade do
{{site.data.keyword.messagehub}} e o que seus aplicativos esperam manipular.

### APIs
{: #api_availability notoc}

Como parte da operação regular do {{site.data.keyword.messagehub}}, os nós do cluster do Kafka
são reiniciados ocasionalmente.
Em alguns casos, seus aplicativos se tornam perceptivos conforme o cluster redesigna recursos. Grave seus
aplicativos para que sejam resilientes a essas mudanças e capazes de se reconectarem e tentarem novamente as
operações.

### Pontes de {{site.data.keyword.messagehub}}
{: #bridge_availability notoc}

Grave seus aplicativos para manipular a possibilidade de que pontes possam reiniciar ocasionalmente.
