---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-27"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# O que é o {{site.data.keyword.messagehub}}?

O {{site.data.keyword.messagehub}} implementa o sistema de mensagens de publicação/assinatura
usando tópicos. Diferentemente de outros sistemas de mensagens, o {{site.data.keyword.messagehub}}
fornece tópicos, mas não filas. O {{site.data.keyword.messagehub}} também oferece recursos adicionais,
como a API do {{site.data.keyword.mql}} e pontes para outros sistemas.

O {{site.data.keyword.messagehub}} possui três APIs: a API do Kafka, a
API do {{site.data.keyword.mql}} e a API de REST do Kafka. Para obter mais informações sobre como
criar aplicativos de sistema de mensagens usando as APIs, consulte
[Usando um cliente do Kafka](/docs/services/MessageHub/messagehub050.html),
[Usando um cliente da API do MQ Light](/docs/services/MessageHub/messagehub075.html) e
[Usando a API de REST do Kafka](/docs/services/MessageHub/messagehub025.html).

O {{site.data.keyword.messagehub}} também suporta pontes para uma seleção de outros sistemas. 
Uma ponte é um link unidirecional para outro sistema. Uma ponte pode tomar mensagens do outro sistema e
publicá-las em um tópico ou consumir mensagens de um tópico e enviá-las para o outro sistema. Dessa maneira, é
possível usar o {{site.data.keyword.messagehub}} para integração com outros sistemas sem gravar
código. Para obter mais informações, consulte
[Vinculando-se a outros serviços usando pontes](/docs/services/MessageHub/messagehub088.html).

O {{site.data.keyword.messagehub}} é baseado no projeto Apache Kafka de software livre, um
backbone de sistema de mensagens altamente escalável e de alto desempenho comprovado em muitos ambientes de
produção. Para obter mais informações, consulte
[{{site.data.keyword.messagehub}} e Apache
Kafka](/docs/services/MessageHub/messagehub073.html).
