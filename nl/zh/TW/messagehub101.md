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

# 使用 MQ Light Python 用戶端
{: #mql_python}


若要使用 API，請為 Python 新增參照到最新的可用 {{site.data.keyword.mql}} 用戶端 API，如下所示：

新增下列參照到您的 <code>requirements.txt</code> 檔案：

```
git+git://github.com/mqlight/python-mqlight.git@readthedocs
```
{:codeblock}

<br>
然後新增下列 import 陳述式到您的原始檔：

```
import mqlight
```
{:codeblock}

<!-- Comment from Andrew
Instructions for getting started, with links for more info
Simple send source and receive source in-line

-->

