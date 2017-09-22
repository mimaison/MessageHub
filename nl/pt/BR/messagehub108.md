---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-16"

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

## Qual é o valor padrão para offsets.retention.minutes do Kafka?
{: #offsets notoc}
O valor padrão é 7 dias. 

Como a retenção de deslocamento abrange todo o sistema, não é possível configurá-la em um
nível de tópico individual. Todos os grupos de consumidores obtêm apenas 7 dias de deslocamentos armazenados, mesmo se o
tópico foi aumentado para o máximo de 30 dias de retenção de log. 

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
