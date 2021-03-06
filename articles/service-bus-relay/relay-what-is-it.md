---
title: "Azure 릴레이 정의 및 사용 이유 개요 | Microsoft Docs"
description: "Azure 릴레이 개요"
services: service-bus-relay
documentationcenter: .net
author: banisadr
manager: timlt
editor: 
ms.assetid: 1e3e971d-2a24-4f96-a88a-ce3ea2b1a1cd
ms.service: service-bus-relay
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: multiple
ms.topic: get-started-article
ms.date: 03/09/2017
ms.author: babanisa;sethm
translationtype: Human Translation
ms.sourcegitcommit: 8a531f70f0d9e173d6ea9fb72b9c997f73c23244
ms.openlocfilehash: 9fd40892c77630bd4f0b7abf5c3458a6dc200402
ms.lasthandoff: 03/10/2017


---
# <a name="what-is-azure-relay"></a>Azure 릴레이란?
Azure 릴레이 서비스는 방화벽 연결을 열거나 회사 네트워크 인프라를 주입식으로 변경하지 않고도 회사 엔터프라이즈 네트워크 내에 있는 서비스를 공용 클라우드에 안전하게 노출할 수 있게 함으로써 이 작업을 도와줍니다. 릴레이는 다양한 전송 프로토콜 및 웹 서비스 표준을 지원합니다.

릴레이 서비스는 기존의 단방향, 요청/응답 및 피어투피어 트래픽을 지원합니다. 또한 인터넷에서 이벤트 배포를 지원하여 향상된 지점간 효율성을 위한 양방향 소켓 통신과 게시/구독 시나리오를 가능하게 합니다. 

릴레이된 데이터 전송 패턴에서는 온-프레미스 서비스가 아웃바운드 포트를 통해 릴레이 서비스에 연결하고 특정 랑데부 주소와 연결된 통신에 사용할 양방향 소켓을 만듭니다. 그러면 클라이언트는 랑데부 주소를 대상으로 하는 릴레이 서비스에 트래픽을 전송하여 온-프레미스 서비스와 통신할 수 있습니다. 그 후 릴레이 서비스는 각 클라이언트 전용 양방향 소켓을 통해 온-프레미스 서비스에 데이터를 "릴레이"합니다. 클라이언트는 온-프레미스 서비스에 대한 직접 연결이 필요 없고, 서비스가 상주하는 위치를 알 필요가 없고, 온-프레미스 서비스는 방화벽에 열려 있는 인바운드 포트가 필요 없습니다.

릴레이가 제공하는 주요 기능 요소는 TCP와 유사한 제한, 끝점 검색, 연결 상태, 중복된 끝점 보안을 갖춘 네트워크 경계에서 양방향의 버퍼링이 없는 통신입니다. 릴레이의 기능은 VPN이 네트워크 환경 변화에 좌우되기 때문에 VPN 기술이 훨씬 침입적인 반면, 단일 컴퓨터의 단일 응용 프로그램 끝점에 범위를 지정할 수 있는 VPN과 같은 네트워크 수준의 통합 기술과 다릅니다.

Azure 릴레이에는 다음과 같은 두 가지 기능이 있습니다.

1. [하이브리드 연결](#hybrid-connections) - 다중 플랫폼 시나리오를 가능하게 하는 공개 표준 웹 소켓을 사용합니다.
2. [WCF 릴레이](#wcf-relays) - 원격 프로시저 호출이 가능하도록 WCF(Windows Communication Foundation)를 사용합니다. WCF 릴레이는 레거시 릴레이로 많은 고객이 기존의 WCF 프로그래밍 모델과 함께 사용합니다.

하이브리드 연결과 WCF 릴레이는 모두 기업 엔터프라이즈 네트워크 내에 있는 자산에 대해 보안 연결을 사용합니다. 이들 중 무엇을 사용할지는 다음 테이블에 설명되어 있는 구체적인 요구 사항에 따라 달라집니다.

|  | WCF 릴레이 | 하이브리드 연결 |
| --- |:---:|:---:|
| **WCF** |x | |
| **.NET Core** | |x |
| **.NET Framework** |x |x |
| **JavaScript/NodeJS** | |x |
| **표준 기반 개방형 프로토콜** | |x |
| **여러 RPC 프로그래밍 모델** | |x |

## <a name="hybrid-connections"></a>하이브리드 연결
[Azure 릴레이의 하이브리드 연결](relay-hybrid-connections-protocol.md) 기능은 기존 릴레이 기능의 안전한 오픈 프로토콜의 진화된 형태로, 구현 모든 플랫폼에서 그리고 일반적인 웹 브라우저에 WebSocket API를 명시적으로 포함하는 기본 WebSocket 기능을 가진 모든 언어로 구현할 수 있습니다. 하이브리드 연결은 HTTP 및 WebSockets를 기반으로 합니다.

## <a name="wcf-relays"></a>WCF 릴레이
WCF 릴레이는 전체 .NET Framework(NETFX) 및 WCF를 위해 작동합니다. WCF "릴레이" 바인딩 모음을 사용하여 온-프레미스 서비스와 릴레이 서비스 사이의 연결을 시작합니다. 내부적으로, 릴레이 바인딩은 클라우드에서 서비스 버스와 통합하는 WCF 채널 구성 요소를 생성하도록 설계된 새로운 전송 바인딩 요소에 매핑합니다.

## <a name="service-history"></a>서비스 변경 사항
하이브리드 연결은 Azure Service Bus WCF 릴레이에서 빌드된 이전과 비슷한 이름의 "BizTalk Services" 기능을 대체합니다. 새로운 하이브리드 연결 기능은 기존 WCF 릴레이 기능을 보완하고 이러한 두 서비스 기능은 당분간 릴레이 서비스에 공존하게 됩니다. 일반적인 게이트웨이를 공유하지만 구현 방식은 서로 다릅니다.

## <a name="next-steps"></a>다음 단계:
* [릴레이 FAQ](relay-faq.md)
* [네임스페이스 만들기](relay-create-namespace-portal.md)
* [.NET 시작](relay-hybrid-connections-dotnet-get-started.md)
* [노드 시작](relay-hybrid-connections-node-get-started.md)


