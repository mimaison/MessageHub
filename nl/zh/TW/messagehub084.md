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

# 如何將 Kafka 用戶端從 0.9.X 移轉至 0.10.X 或 0.11.X
{: #kafka_migrate}


如果您使用 Java 用戶端，可以使用公開提供的 0.10 X 或 0.11.X Kafka 用戶端。我們強烈鼓勵您從 0.9.X 移至最新的 0.10.X 或 0.11.X 版（我們支援所有更新的版本）。請完成下列步驟：

1. 刪除 {{site.data.keyword.messagehub}} 登入 jar 模組。
2. 將 <code>jaas.conf</code> 檔案變更如下：
    ```
        KafkaClient {
          org.apache.kafka.common.security.plain.PlainLoginModule required
          serviceName="kafka"
            username="<your username>"
            password="<your password>";
        };
    ```
    {: codeblock}

3. 將此行新增到您的消費者和生產者內容：<code>sasl.mechanism=PLAIN</code>


