---

copyright:
  years: 2015, 2017
lastupdated: "2017-02-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Message Hub 정보
{: #about}

{{site.data.keyword.messagehub_full}}는 애플리케이션과 서비스를 쉽고 안정적으로 통신할 수 있는 처리량이 높고 확장 가능한 분산된 메시징 서비스입니다.
{:shortdesc}

{{site.data.keyword.messagehub}}에서 애플리케이션은
메시지를 작성하고 해당 메시지를 토픽에 보냄으로써 데이터를 전송합니다. 메시지를 수신하기 위해 애플리케이션은
토픽을 구독하고 모든 토픽의 메시지를 수신할지 또는 그 사이에서 메시지를 공유할지 선택합니다.
{{site.data.keyword.messagehub}}는 정렬된 순서로 메시지를 호스팅하고
유지보수합니다. 기존 메시징 시스템과 반대로 {{site.data.keyword.messagehub}}는 토픽을 제공하지만 큐에 저장하지는 않습니다. 하지만
{{site.data.keyword.messagehub}}에서는 수신 애플리케이션 간에 메시지를 공유하는 방법을 제공하며,
이는 결과적으로 큐와 비슷한 작동을 합니다. 

{{site.data.keyword.messagehub}}를 사용하여 다음과 같은 태스크를 완료할 수 있습니다. 

* 마이크로서비스를 서로 연결합니다.
* 백엔드 작업자 프로세스에 작업을 오프로드합니다. 
* 스트림 데이터를 분석에 연결하여 강력한 통찰을 실현합니다.
* 실시간으로 반응하도록 이벤트 데이터를 여러 애플리케이션에 공개합니다.
* 데이터를 장기 스토리지와 같은 다른 서비스에 전송합니다. 
