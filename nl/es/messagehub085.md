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

# Diferencias entre Message Hub en entornos de Bluemix Public y Bluemix Dedicated
{: #public_dedicated}

{{site.data.keyword.Bluemix}} es una plataforma de estándares abiertos basada en la nube para crear, ejecutar y gestionar apps. {{site.data.keyword.Bluemix_notm}} proporciona modelos de despliegue públicos y dedicados. {{site.data.keyword.messagehub}} está disponible en ambos entornos.

## Entorno público de {{site.data.keyword.Bluemix_notm}}
{: notoc}

{{site.data.keyword.Bluemix_notm}} Public proporciona un servicio económico en la nube pública en el que se paga por lo que se utiliza y se comparte la infraestructura con otros usuarios.

En {{site.data.keyword.Bluemix_notm}} Public, el costo de {{site.data.keyword.messagehub}} está determinado por dos factores: el número de particiones que utilice y el número de mensajes que se envían y reciben. No hay ningún cargo para los datos del mensaje mientras se mantiene en los temas, pero los datos que cada partición se mantiene limitada a 1 GB.

Para obtener más información, consulte [{{site.data.keyword.Bluemix_notm}} Public ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud-computing/bluemix/public){:new_window}.


## Entorno de {{site.data.keyword.Bluemix_notm}} Dedicated
{: notoc}

{{site.data.keyword.Bluemix_notm}} Dedicated proporciona un entorno más aislado en el que la infraestructura no se comparte y se aloja en una cuenta SoftLayer gestionada por {{site.data.keyword.IBM_notm}}. Este entorno está conectado de forma segura a {{site.data.keyword.Bluemix_notm}} Public y a su propia red.

En una instancia dedicada de {{site.data.keyword.messagehub}}, debe pagar por el servicio en lugar de por el uso. Puede tener hasta 75 particiones en todo el entorno, incluidas las organizaciones y los espacios. Cada partición está limitada a 10 GB para garantizar que el clúster no se quede sin espacio.

Los paneles de control de Kibana y Grafana para la supervisión del servicio no se soportan en {{site.data.keyword.Bluemix_notm}} Dedicated.

Para obtener más información, consulte [{{site.data.keyword.Bluemix_notm}} Dedicated ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/cloud-computing/bluemix/dedicated/){:new_window}.


