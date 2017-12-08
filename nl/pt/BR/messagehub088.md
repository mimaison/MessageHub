---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-01"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Vinculando-se a outros serviços usando pontes
{: #bridges}

Pontes são links unidirecionais entre o {{site.data.keyword.messagehub}} e outro serviço. As
pontes permitem que os dados sejam lidos do {{site.data.keyword.messagehub}} e gravados em
outro serviço ou que sejam lidos de outro serviço e gravados no {{site.data.keyword.messagehub}}. 
{:shortdesc}

Os principais benefícios do uso das pontes do {{site.data.keyword.messagehub}} são os
seguintes:  

* É possível definir as pontes administrativamente, de modo que não é necessário gravar código do
aplicativo.
* O ciclo de vida de cada ponte é monitorado e gerenciado pelo serviço do {{site.data.keyword.messagehub}}. Por exemplo, se uma ponte encontra um erro, ela é reiniciada automaticamente pelo {{site.data.keyword.messagehub}}.
* As pontes são integradas com a plataforma do {{site.data.keyword.Bluemix_short}}. Por exemplo, as informações de criação de log e de monitoramento geradas pelas pontes são direcionadas aos
painéis do Kibana e Grafana.

Talvez você ache as pontes úteis nos dois cenários comuns a seguir:

* Consumindo dados de uma ou mais origens de dados para o {{site.data.keyword.messagehub}}.
* Transferindo dados do {{site.data.keyword.messagehub}} para outro serviço. Por exemplo, para armazenamento de longo prazo.

## Pontes de {{site.data.keyword.messagehub}}
{: notoc}

* Os dois tipos de pontes a seguir são fornecidos: 
  - Ponte do MQ, que usa dados da mensagem do {{site.data.keyword.IBM}} MQ e os transfere para um tópico no {{site.data.keyword.messagehub}}. Pretendemos oferecer suporte para uma ampla variedade de pontes futuramente.
  - Ponte {{site.data.keyword.objectstorageshort}}, que transfere dados do {{site.data.keyword.messagehub}} para uma instância do serviço do [Object Storage ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/services/ObjectStorage/index.html){:new_window}.
* Atualmente, as pontes estão disponíveis em todos os ambientes públicos do {{site.data.keyword.Bluemix_notm}}. As pontes não estão disponíveis no {{site.data.keyword.Bluemix_short}} Dedicated.
* É possível administrar as pontes nos dois modos a seguir:
  - Usando uma [API de REST ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/ibm-messaging/message-hub-docs){:new_window}, que é uma extensão para a API de administração do {{site.data.keyword.messagehub}}. Também é possível localizar exemplos de como usar o curl
para gerenciar o ciclo de vida de pontes em [message-hub-docs ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/ibm-messaging/message-hub-docs){:new_window}. Podemos mudar essa API de REST conforme continuamos a desenvolver pontes. Pretendemos estabilizar esta API.
  - Usando o painel do {{site.data.keyword.messagehub}} no console do {{site.data.keyword.Bluemix_notm}}.
* É possível associar um máximo de duas pontes de qualquer tipo a uma instância do serviço do {{site.data.keyword.messagehub}}. Continuaremos a revisar esta limitação conforme continuamos a desenvolver pontes.
* Não há encargos adicionais pelo uso de pontes além das operações de sistema de mensagens.
* A ponte do MQ não suporta o uso de SSL/TLS para proteger a privacidade e a integridade dos dados
enquanto eles são transferidos entre a ponte e o gerenciador de filas do MQ. Pretendemos incluir suporte para o uso de SSL/TLS para a ponte. 
* A ponte do {{site.data.keyword.objectstorageshort}} concatena mensagens usando caracteres de nova linha como separadores à medida que grava os dados no {{site.data.keyword.objectstorageshort}}. Isso a torna inadequada para mensagens que contêm caracteres de nova linha integrados e para dados da mensagem binários.
* As convenções de nomenclatura de objeto que são usadas atualmente pela ponte do {{site.data.keyword.objectstorageshort}} podem mudar futuramente.

No entanto, é possível usar o serviço do [{{site.data.keyword.SecureGatewayfull}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/services/SecureGateway/secure_gateway.html){:new_window} para enviar seus dados por meio de um túnel seguro entre o
{{site.data.keyword.Bluemix_notm}} e um cliente
do {{site.data.keyword.SecureGateway}}
que pode ser instalado no local. Nessa configuração, a comunicação em qualquer extremidade do túnel não é
protegida usando SSL/TLS.
