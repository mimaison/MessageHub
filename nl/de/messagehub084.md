---

copyright:
  years: 2015, 2017
lastupdated: "2017-05-11"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Vorgehensweise bei der Migration des Kafka-Clients von Version 0.9.X auf Version 0.10.X oder 0.11.X
{: #kafka_migrate}


Wenn Sie mit den Java-Clients arbeiten, können Sie die offiziell verfügbaren Kafka-Clients der
Version 0.10.X oder 0.11.X verwenden. Es wird dringend empfohlen, von der Version 0.9.X auf den neuesten
Stand der Version 0.10.X oder 0.11.X umzustellen (alle neueren Versionen werden unterstützt). Führen Sie die folgenden Schritte aus:

1. Löschen Sie das JAR-Modul für die {{site.data.keyword.messagehub}}-Anmeldung.
2. Ändern Sie Ihre Datei <code>jaas.conf</code> wie folgt:
    ```
        KafkaClient {
          org.apache.kafka.common.security.plain.PlainLoginModule required
          serviceName="kafka"
            username="<ihr benutzername>"
            password="<ihr kennwort>";
        };
    ```
    {: codeblock}

3. Fügen Sie die folgende Zeile in Ihren Eigenschaften 'consumer' und 'producer' hinzu: <code>sasl.mechanism=PLAIN</code>.


