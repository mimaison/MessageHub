---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.messagehub}} FAQ
{: #faqs}

{{site.data.keyword.IBM}} {{site.data.keyword.messagehub}} 서비스에 대한 일반적인 질문에 답변합니다. 

<!--17/10/17 - Karen: same info duplicated at messagehub104 -->
## 토픽 작성 및 삭제를 위해 Kafka API를 사용하는 방법
{: #topic_admin notoc}

Kafka 클라이언트를 0.11 이상에서 사용 중이거나 Kafka 스트림을 0.10.2.0 이상에서 사용 중인 경우, API를 사용하여 토픽을 작성하고 삭제할 수 있습니다. 토픽 작성 시 허용되는 설정에 대한 제한사항이 있습니다. 현재는 다음 설정만 수정할 수 있습니다. 

<dl>
<dt>cleanup.policy</dt>
<dd><code>delete</code>(기본값), <code>compact</code> 또는 <code>delete,compact</code>로 설정하십시오.</dd>
<dt>retention.ms</dt>
<dd>기본 보존 기간은 24시간입니다. 최소 1시간이며 최대 30일입니다. 이 값을 시간 배수로 지정하십시오.

<p>**참고:**
정리 정책이 <code>compact</code> 전용인 경우, <code>delete</code>를 자동으로 추가하지만 시간에 따라 삭제가 사용 불가능합니다. 토픽의 메시지는 삭제되기 전에 최대 1GB로 압축됩니다. </p>
</dd>
</dl>

## {{site.data.keyword.messagehub}}에서 이용자 오프셋 토픽의 로그 보존 기간으로 설정하는 기간
{: #offsets notoc}
{{site.data.keyword.messagehub}}에서는 이용자 오프셋을 7일 동안 보존합니다. 이는 Kafka 구성 offsets.retention.minutes에 해당됩니다. 

오프셋 보존은 시스템 전체에 해당하므로 개별 토픽 레벨에서 설정할 수 없습니다. 모든 이용자 그룹은 토픽의 로그 보존이 최대 30일로 늘어났더라도 저장된 오프셋의 기간은 7일 동안만 가능합니다.  

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
