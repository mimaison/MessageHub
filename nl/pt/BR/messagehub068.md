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


#Segurança e privacidade de dados
{: #data_security}


O {{site.data.keyword.IBM}} usa os métodos a seguir para ajudar a garantir a segurança e a
privacidade dos seus dados:
{:shortdesc}

## Protocolos criptográficos
{: #cryptographic notoc}


*  Conexões ao Kafka nativo e interfaces REST devem ser feitas usando TLS 1.2.
*  Conexões estão restritas aos seguintes conjuntos de criptografia forte:

      * ECDHE-RSA-AES128-GCM-SHA256
      * ECDHE-RSA-AES256-GCM-SHA384
      * DHE-RSA-AES128-GCM-SHA256
      * kEDH+AESGCM
      * ECDHE-RSA-AES128-SHA256
      * ECDHE-RSA-AES256-SHA384
      * DHE-RSA-AES128-SHA256
      * DHE-RSA-AES256-SHA256



*  Para acessar o painel do {{site.data.keyword.messagehub}}, deve-se usar um navegador que suporte TLS 1.2.
   
## Criptografia de cargas úteis de mensagem
{: #encryption_payloads notoc}

Os dados de mensagens são criptografados para transmissões entre o {{site.data.keyword.messagehub}}
e clientes como um resultado de TLS. O {{site.data.keyword.messagehub}} armazena dados da mensagem em espera e logs de mensagem em discos criptografados.



