---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.messagehub}} FAQ
{: #faqs}

{{site.data.keyword.IBM}} {{site.data.keyword.messagehub}} 서비스에 대한 일반적인 질문에 답변합니다. 

## Kafka offsets.retention.minutes의 기본값은 무엇입니까?
{: #offsets notoc}
기본값은 7일입니다. 

오프셋 보존은 시스템 전체에 해당하므로 개별 토픽 레벨에서 설정할 수 없습니다. 모든 이용자 그룹은 해당 토픽의 로그 보존이 최대 30일로 늘어났더라도 저장된 오프셋의 기간은 7일 동안만 가능합니다.  

## {{site.data.keyword.messagehub}}의 가용성 작동은 무엇입니까?
{: #availability notoc}

{{site.data.keyword.messagehub}} 앱을 작성하는 경우, 이 정보를 사용하여 보통 {{site.data.keyword.messagehub}} 가용성 작동이 무엇이며 사용자의 앱에서 무엇을 처리해야 하는지 이해하십시오. 

### API
{: #api_availability notoc}

{{site.data.keyword.messagehub}}의 일반 오퍼레이션의 일부로서 Kafka 클러스터의 노드가 가끔씩 다시 시작됩니다.
어떤 경우에는 클러스터가 리소스를 재지정하면 사용자의 앱이 인식하게 됩니다. 이러한 변경사항에 복원력이 있으며
다시 연결해서 오퍼레이션을 재시도할 수 있도록 앱을 작성하십시오. 

### {{site.data.keyword.messagehub}} 브릿지
{: #bridge_availability notoc}

브릿지가 가끔씩 다시 시작할 수 있는 가능성을 감당할 수 있도록 앱을 작성하십시오. 
