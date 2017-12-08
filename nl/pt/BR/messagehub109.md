---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-19"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}



# Relatando um problema para a equipe do {{site.data.keyword.messagehub}}
{: #report_problem}

Se você estiver enfrentando um problema com o {{site.data.keyword.messagehub}}, primeiro
verifique a página de status do [{{site.data.keyword.Bluemix_notm}}
![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/status){:new_window}. 

Se você deseja ajuda da equipe do {{site.data.keyword.messagehub}}, reúna o máximo de
informações possível a seguir:
{:shortdesc}

1. Em qual região do {{site.data.keyword.Bluemix_notm}} sua instância do
{{site.data.keyword.messagehub}} está sendo fornecida?  Por exemplo, sul dos EUA ou Reino Unido. 
2. Em qual interface você está encontrando problemas? REST, Kafka, AMQP ou pontes?
3. Quando o primeiro problema ocorreu (especificamente hora, data e fuso horário)? Por quanto tempo
seu aplicativo esteve em execução antes disso?
4. O problema ainda está ocorrendo? É possível replicá-lo?
5. Qual é o ID da instância do serviço do {{site.data.keyword.messagehub}} que você está
usando? 
É possível localizar esse ID consultando o campo "instance_id" no JSON VCAP_SERVICES do serviço.
6. Que cliente Kafka ou REST seu aplicativo está usando? Quais são os detalhes da versão?
7. Quais são os detalhes de configuração do seu cliente?
8. Você possui fragmentos de log do aplicativo que exibem o problema?
9. Qual é o problema que você está vendo? Quais tópicos, IDs de cliente e IDs de grupo são afetados?
10. Que impacto o problema está causando em seu serviço?


É possível fornecer as informações reunidas para a IBM em um chamado de suporte [enviando uma solicitação
de suporte ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/support/index.html#open-ticket).










