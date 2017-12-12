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

# {{site.data.keyword.Bluemix_notm}} 퍼블릭 및 데디케이티드 환경의 Message Hub 사이의 차이점
{: #public_dedicated}

{{site.data.keyword.Bluemix}}는 애플리케이션을 빌드, 실행 및 관리하기 위한 개방형 표준, 클라우드 기반 플랫폼입니다. {{site.data.keyword.Bluemix_notm}}는
퍼블릭 및 데디케이티드 배치 모델을 제공합니다. {{site.data.keyword.messagehub}}는 두 환경에서 모두 사용 가능합니다. 

## {{site.data.keyword.Bluemix_notm}} 퍼블릭 환경
{: notoc}

{{site.data.keyword.Bluemix_notm}} 퍼블릭은 인프라를 다른 사용자들과 공유하고 사용하는 것에 대해 지불하는 경제적인
퍼블릭 클라우드 서비스를 제공합니다. 

{{site.data.keyword.Bluemix_notm}} 퍼블릭에서
{{site.data.keyword.messagehub}}의 비용은 두 가지 요인(사용자가 사용하는 파티션의 수 및 사용자가 보내고 받는 메시지의 수)에 의해 결정됩니다. 메시지 데이터가 토픽에 보존되어 있는 동안에는 그에 대한
비용이 없지만, 각 파티션이 보유하는 데이터는 1GB로 상한이 제한됩니다. 

자세한 정보는 [{{site.data.keyword.Bluemix_notm}} 퍼블릭 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud-computing/bluemix/public){:new_window}을 참조하십시오.


## {{site.data.keyword.Bluemix_notm}} 데디케이티드 환경
{: notoc}

{{site.data.keyword.Bluemix_notm}} 데디케이티드는
사용자의 인프라가 공유되지 않고 {{site.data.keyword.IBM_notm}}에서 관리하는 개별 SoftLayer 계정에 호스팅되는
더 격리된 환경을 제공합니다. 이 환경은 {{site.data.keyword.Bluemix_notm}} 퍼블릭 및 사용자 자신의 네트워크에 안전하게 연결됩니다. 

{{site.data.keyword.messagehub}}의 데디케이티드 인스턴스에서는
서비스를 얼마나 사용하는지 보다는 서비스에 대해 지불합니다. 모든 조직과 영역을 포함한 전체 환경에서 최대 75개의 파티션이
가능합니다. 각 파티션은 클러스터가 영역 밖에서 실행되지 않도록 하기 위해 10GB로 상한이 제한됩니다. 

데디케이티드 환경의 {{site.data.keyword.messagehub}}는 {{site.data.keyword.Bluemix_notm}} 데이케이티드로만 배치될 수 있으나
기타 데디케이티드 환경을 사용하는 경우 공용 서비스의 신디케이티드 버전을 제공할 수 있습니다.
서비스 모니터링을 위한 Kibana 및 Grafana 대시보드는 {{site.data.keyword.Bluemix_notm}} 데디케이티드에서 지원되지 않습니다.

자세한 정보는 [{{site.data.keyword.Bluemix_notm}} 데디케이티드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ibm.com/cloud-computing/bluemix/dedicated/){:new_window}을 참조하십시오.


