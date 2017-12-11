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

# 如何将 Kafka 客户机从 0.9.X 迁移到 0.10.X 或 0.11.X
{: #kafka_migrate}


如果使用的是 Java 客户机，那么可以使用公共可用的 0.10.X 或 0.11.X Kafka 客户机。强烈建议您从 0.9.X 迁移到最新的 0.10.X 或 0.11.X 版本（我们支持所有更新版本）。请完成以下步骤：

1. 删除 {{site.data.keyword.messagehub}} 登录 JAR 模块。
2. 将 <code>jaas.conf</code> 文件更改为以下内容：
    ```
        KafkaClient {
          org.apache.kafka.common.security.plain.PlainLoginModule required
          serviceName="kafka"
            username="<your username>"
            password="<your password>";
        };
    ```
    {: codeblock}

3. 将以下行添加到使用者和生产者属性：<code>sasl.mechanism=PLAIN</code>


