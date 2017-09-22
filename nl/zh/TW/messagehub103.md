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

# 使用 MQ Light Ruby 用戶端
{: #mql_how}


若要使用 API，請為 Ruby 新增參照到最新的可用 {{site.data.keyword.mql}} 用戶端 API，如下所示：

新增下列參照到 <code>Gemfile</code>：

```
gem 'mqlight', '~> 1.0'
```
{: codeblock}

然後新增下列 require 陳述式到您的原始檔：

```
require 'mqlight'
```
{: codeblock}

<!-- Comment from Andrew
Instructions for getting started, with links for more info
Simple send source and receive source in-line

-->


