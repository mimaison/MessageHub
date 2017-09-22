---

copyright:
  years: 2015, 2017
lastupdated: "2017-02-08"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Diferenças do Message Hub em ambientes Bluemix Public e Bluemix Dedicated
{: #public_dedicated}

{{site.data.keyword.Bluemix}} é uma plataforma de padrão aberto, baseada em nuvem para construir, executar e gerenciar aplicativos. O {{site.data.keyword.Bluemix_notm}} fornece modelos de implementação pública e
dedicada. O {{site.data.keyword.messagehub}} está disponível em ambos os ambientes.

## Ambiente {{site.data.keyword.Bluemix_notm}} Public 
{: notoc}

O {{site.data.keyword.Bluemix_notm}} Public fornece um serviço de nuvem pública econômica em que
você paga pelo que usa e compartilha a infraestrutura com outros.

No {{site.data.keyword.Bluemix_notm}} Public, o custo do
{{site.data.keyword.messagehub}} é determinado por dois fatores: o número de partições que você usa e
o número de mensagens que você envia e recebe. Os dados da mensagem não são cobrados enquanto eles estão
retidos nos tópicos, mas os dados que cada partição retém são limitados a 1 GB.

Para obter mais informações, consulte [{{site.data.keyword.Bluemix_notm}} Public ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud-computing/bluemix/public){:new_window}.


## Ambiente {{site.data.keyword.Bluemix_notm}} Dedicated
{: notoc}

O {{site.data.keyword.Bluemix_notm}} Dedicated fornece um ambiente mais isolado em que sua
infraestrutura não é compartilhada e é hospedado em uma conta separada do SoftLayer gerenciada pela
{{site.data.keyword.IBM_notm}}. Este ambiente é conectado com segurança ao {{site.data.keyword.Bluemix_notm}} Public e à sua própria rede.

Em uma instância dedicada do {{site.data.keyword.messagehub}}, você paga pelo serviço em vez do
quanto ele é usado. É possível ter até 75 partições no ambiente inteiro, incluindo todas as organizações e
espaços. Cada partição é limitada a 10 GB para assegurar que o cluster não fique sem espaço.

Os painéis do Kibana e Grafana para monitoramento do serviço não são suportados no {{site.data.keyword.Bluemix_notm}} Dedicated.

Para obter mais informações, consulte [{{site.data.keyword.Bluemix_notm}} Dedicated ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/cloud-computing/bluemix/dedicated/){:new_window}.


