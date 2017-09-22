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

# Message Hub 在 Bluemix 公用與 Bluemix 專用環境之間的差異
{: #public_dedicated}

{{site.data.keyword.Bluemix}} 是一種以雲端為基礎的開放標準平台，用於建置、執行及管理應用程式。{{site.data.keyword.Bluemix_notm}} 提供公用及專用的部署模型。{{site.data.keyword.messagehub}} 可以在這兩個環境中使用。

## {{site.data.keyword.Bluemix_notm}} 公用環境
{: notoc}

「{{site.data.keyword.Bluemix_notm}} 公用」提供經濟實惠的公用雲端服務，您只要針對使用的部分付費，並且與其他人共用基礎架構。

在「{{site.data.keyword.Bluemix_notm}} 公用」中，{{site.data.keyword.messagehub}} 的成本取決於兩個因素：您使用的分割區數目，以及您傳送與接收的訊息數目。針對保留在主題上的訊息資料不會有任何費用，但每個分割區保留的資料上限為
1 GB。

如需相關資訊，請參閱 [{{site.data.keyword.Bluemix_notm}} 公用 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud-computing/bluemix/public){:new_window}。


## {{site.data.keyword.Bluemix_notm}} 專用環境
{: notoc}

「{{site.data.keyword.Bluemix_notm}} 專用」提供較隔離的環境，您的基礎架構不會共用，並管理於個別的 SoftLayer
帳戶（由 {{site.data.keyword.IBM_notm}} 管理）。此環境會安全地連接至「{{site.data.keyword.Bluemix_notm}} 公用」及您自己的網路。

在 {{site.data.keyword.messagehub}} 的專用實例中，您會針對服務而付費，而不是針對使用的量付費。您可以在整個環境中有最多 75
個分割區，包括所有組織及空間。每個分割區的上限為 10 GB，以確保叢集不會用盡空間。

在「{{site.data.keyword.Bluemix_notm}} 專用」中不支援用 Kibana 和 Grafana 儀表板來監視服務。

如需相關資訊，請參閱 [{{site.data.keyword.Bluemix_notm}} 專用 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/cloud-computing/bluemix/dedicated/){:new_window}。


