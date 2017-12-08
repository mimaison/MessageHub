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

# Por que usar a API {{site.data.keyword.mql}}?
{: #why_mql}

A API {{site.data.keyword.mql}} fornece um nível mais alto de abstração do que a API Kafka. O {{site.data.keyword.mql}} permite que aplicativos sejam gravados de maneira rápida e portátil em um modelo de sistema de mensagens unificado que suporta padrões de sistema de mensagens de fila e de publicação/assinatura. 
{:shortdesc}

Os aplicativos trocam mensagens usando destinos criados dinamicamente, os quais você pode estruturar hierarquicamente (por exemplo, <code>‘/sports/football’</code>), agrupar usando curingas (por exemplo,
<code>‘/sports/#’</code>) e tenha controles simples para garantia de entrega e validação de mensagem.
Isso permite implementar cenários como a transferência do trabalhador, a notificação de eventos e o processamento em lote diretamente.

Bem como enviar mensagens entre outros aplicativos usando a API {{site.data.keyword.mql}}, também é possível trocar mensagens com aplicativos que usam as APIs Kafka REST ou Kafka. Como alternativa, também é possível usar aplicativos no local com o {{site.data.keyword.IBM}} MQ.

