---

copyright:
  years: 2015, 2017
lastupdated: "2017-04-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 브릿지를 사용하여 다른 서비스에 링크
{: #bridges}

브릿지는 {{site.data.keyword.messagehub}} 및 다른 서비스 사이의 단방향 링크입니다. 브릿지는
데이터를 {{site.data.keyword.messagehub}}에서 읽고 다른 서비스에
쓰도록 허용하거나 데이터를 다른 서비스에서 읽고 {{site.data.keyword.messagehub}}에 쓰도록 허용합니다.
{:shortdesc}

{{site.data.keyword.messagehub}} 브릿지 사용의 주요 이점은 다음과 같습니다.   

* 관리상 브릿지를 정의할 수 있어서 애플리케이션 코드를 작성할 필요가 없습니다.
* 각 브릿지의 라이프사이클을 {{site.data.keyword.messagehub}} 서비스에서 모니터하고 관리합니다. 예를 들어, 브릿지에 오류가 발생하면 {{site.data.keyword.messagehub}}에서 자동으로 브릿지를 다시 시작합니다.
* 브릿지는 {{site.data.keyword.Bluemix_short}} 플랫폼과 통합됩니다. 예를 들어, 브릿지에서 생성된 로깅 및 모니터링 정보는 Kibana 및 Grafana 대시보드로 경로가 지정됩니다. 

다음 두 개의 공통 시나리오에서 브릿지가 유용하게 사용될 수 있습니다. 

* 하나 이상의 데이터 소스에서 {{site.data.keyword.messagehub}}로 데이터 이용
* 데이터를 {{site.data.keyword.messagehub}}에서 장기 스토리지와 같은 다른 서비스에 전송

## {{site.data.keyword.messagehub}} 브릿지
{: notoc}

* 다음 두 가지 유형의 브릿지를 제공합니다.  
  - {{site.data.keyword.objectstorageshort}} 브릿지는 {{site.data.keyword.messagehub}} 데이터를 [Object Storage 서비스 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/services/ObjectStorage/index.html){:new_window}의 인스턴스에 전송합니다. 
  - MQ 브릿지는 {{site.data.keyword.IBM}} MQ에서 메시지 데이터를 택해서 {{site.data.keyword.messagehub}}의 토픽에 전송합니다. 향후에는 더 광범위한 범위의 브릿지를 지원할 계획입니다.
* 현재 브릿지는 모든 {{site.data.keyword.Bluemix_notm}} 퍼블릭 환경에서 사용 가능합니다. 브릿지는 {{site.data.keyword.Bluemix_short}} 데디케이티드에서는 사용할 수 없습니다.
* 다음 두 가지 방법으로 브릿지를 관리할 수 있습니다. 
  - [REST API ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/ibm-messaging/message-hub-docs){:new_window}를 사용하며, 이는 기존 {{site.data.keyword.messagehub}} 관리 API에 대한 확장입니다. [message-hub-docs ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/ibm-messaging/message-hub-docs){:new_window}에서 브릿지의 라이프사이클 관리를 위한 curl 사용 방법의 예제를 찾을 수도 있습니다. 브릿지를 계속 개발함에 따라 이 REST API를 변경할 수 있습니다. 이 API를 안정화할 예정입니다.
  - {{site.data.keyword.Bluemix_notm}} 콘솔에서 {{site.data.keyword.messagehub}} 대시보드를 사용합니다.
* {{site.data.keyword.messagehub}} 서비스의 인스턴스와 모든 유형의 브릿지를 최대 두 개까지 연관시킬 수 있습니다. 브릿지를 계속 개발함에 따라 이 제한사항을 계속 검토하게 됩니다.

* 해당 메시징 오퍼레이션 이외의 브릿지 사용에 대한 추가 비용은 없습니다. 
* {{site.data.keyword.objectstorageshort}} 브릿지는 {{site.data.keyword.objectstorageshort}}에 데이터를 작성할 때 구분 기호로 줄 바꾸기 문자를 사용하여 메시지를 연결합니다. 이는 브릿지를 임베디드 줄 바꾸기 문자가 포함된 메시지 및 2진 메시지 데이터에 적합하지 않게 만듭니다. 
* {{site.data.keyword.objectstorageshort}} 브릿지에서 현재 사용되는 오브젝트 이름 지정 규칙은 향후에 변경될 수 있습니다.
* MQ 브릿지는 브릿지와 MQ 큐 관리자 간에 전송되므로 데이터의 무결성 및 개인정보 보호정책을 보호하기 위해 SSL/TLS의 사용을 지원하지 않습니다. 브릿지에 SSL/TLS 사용에 대한 지원을 추가할 계획입니다.  

그러나 [{{site.data.keyword.SecureGatewayfull}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/services/SecureGateway/secure_gateway.html){:new_window} 서비스를 사용하여
{{site.data.keyword.Bluemix_notm}}와 온프레미스로 설치할 수 있는 {{site.data.keyword.SecureGateway}} 클라이언트 사이의 보안 터널을 통해
데이터를 전송할 수 있습니다. 이 구성에서는 SSL/TLS를 사용하여 터널의 양쪽 끝에서 통신의 보안이 되지 않습니다. 
