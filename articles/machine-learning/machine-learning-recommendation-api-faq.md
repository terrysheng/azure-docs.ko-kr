---
title: "Machine Learning 권장 사항 API 설정 및 사용 | Microsoft Docs"
description: "Azure 기계 학습을 사용하여 빌드한 Microsoft 권장 사항 API FAQ"
services: machine-learning
documentationcenter: 
author: LuisCabrer
manager: jhubbard
editor: cgronlun
ms.assetid: 1ffc3c16-e040-4225-9d72-105129938dfa
ms.service: machine-learning
ms.workload: data-services
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 03/31/2017
ms.author: luisca
ROBOTS: NOINDEX, NOFOLLOW
redirect_url: machine-learning-datamarket-deprecation
translationtype: Human Translation
ms.sourcegitcommit: 9ac2a1bf5987fc6fc30e20a1b4a10340eeed3825
ms.openlocfilehash: 15cf891b9c31e1f2e2b108e631f32883ce2f36a7
ms.lasthandoff: 01/05/2017


---
# <a name="setting-up-and-using-machine-learning-recommendations-api-faq"></a>기계 학습 권장 사항 API 설정 및 사용에 대한 FAQ
**권장 사항이란 무엇입니까?**

> [!NOTE]
> 이 버전 대신 Recommendations API Cognitive 서비스를 사용하기 시작해야 합니다. Recommendations Cognitive 서비스가 이 서비스를 대체하게 되며, 모든 새로운 기능이 여기에서 개발됩니다. 일괄 처리 지원, 개선된 API 탐색기, 보다 깔끔한 API 노출 영역, 보다 일관적인 등록/청구 경험 등의 새로운 기능이 있습니다.
> [새로운 Cognitive 서비스로 마이그레이션](http://aka.ms/recomigrate)
> 
> 

고객에 대한 교차 판매 및 상향 판매의 권장 사항에 의존하는 조직과 비즈니스를 위한 Azure 기계 학습 권장 사항은 셀프 서비스 권장 사항 엔진을 제공합니다. 이는 행렬 인수분해를 핵심 알고리즘으로 사용한 공동 작업 필터링 구현입니다. 응용 프로그램 개발자는 REST API를 사용하여 RECOMMENDATIONS에 액세스할 수 있습니다. 

[!INCLUDE [machine-learning-free-trial](../../includes/machine-learning-free-trial.md)]

**권장 사항으로 무엇을 수행할 수 있습니까?**

권장 사항은 항목 또는 항목 집합을 입력으로 이용하고 관련 권장 사항 목록을 반환합니다. 예를 들어 한 온라인 소매점의 고객이 제품을 클릭합니다. 온라인 소매점은 해당 제품을 권장 사항에 대한 입력으로 전송하고, 그 결과로 제품 목록을 가져오고, 이러한 제품 중 고객에게 표시할 제품을 결정합니다. 권장 사항을 사용하여 온라인 스토어를 최적화하거나 내부 판매 부서나 콜 센터에 정보를 제공할 수 있습니다.

**사용 제한이 있습니까?**

권장 사항에는 다음과 같은 사용 제한이 있습니다.

* 구독당 최대 모델 수: 10
* 카탈로그에 포함할 수 있는 최대 항목 수: 100,000
* 유지되는 사용 포인트의 최대 수는&5;,000,000개입니다. 새 포인트가 업로드되거나 보고되면 가장 오래된 포인트가 삭제됩니다.
* 메일로 전송할 수 있는 최대 데이터 크기(예: 카탈로그 데이터 가져오기, 사용 현황 데이터 가져오기)는 200MB입니다.
* 활성화되지 않은 권장 사항 모델 빌드에 대한 TPS(초당 트랜잭션 수)는 최대&2;TPS입니다. 활성화된 권장 사항 모델 빌드는 최대 20TPS를 유지할 수 있습니다.

## <a name="purchase-and-billing"></a>구매 및 요금 청구
**출시 기간 동안 권장 사항 비용은 얼마입니까?**

권장 사항은 구독 기반 서비스입니다. 요금 청구는 월별 트랜잭션 볼륨 기준입니다. 가격 정보는 Microsoft Azure 마켓플레이스의 [제품 페이지](https://datamarket.azure.com/dataset/amla/recommendations) 에서 확인할 수 있습니다.

**권장 사항 추적 및 저장 사용자 활동을 포함하는 것과 관련된 비용이 있습니까?**

현재는 없습니다.

**권장 사항에 무료 평가판이 있습니까?**

매월 트랜잭션 10, 000개로 제한되는 무료 평가판이 있습니다.

**권장 사항에 대한 요금은 언제 청구됩니까?**

유료 구독은 월별 요금이 있는 구독입니다. 유료 구독을 구매하면 첫째 달 사용에 대한 요금이 즉시 청구됩니다. 구독 페이지(및 해당 세금)의 제품과 연결된 금액으로 요금이 청구됩니다. 구독을 취소할 때까지 최초 구매와 같은 달력 날짜에 매월 이 월별 요금이 청구됩니다. 

**더 높은 계층 서비스로 업그레이드하려면 어떻게 해야 합니까?**

Microsoft Azure 마켓플레이스의 [제품 페이지](https://datamarket.azure.com/dataset/amla/recommendations) 에서 구독을 구매 또는 업그레이드할 수 있습니다.

구독을 업그레이드할 경우:

* 이전 구독에 남아 있는 트랜잭션은 새 구독에 추가되지 않습니다. 
* 이전 구독에 사용되지 않은 트랜잭션이 있더라도 새 구독에 대한 전체 가격을 지급해야 합니다.

구독 업그레이드 프로세스:

* [제품 페이지](https://datamarket.azure.com/dataset/amla/recommendations)로 이동합니다.
* 아직 로그인하지 않았으면 마켓플레이스에 로그인합니다.
* 오른쪽 창에 사용 가능한 모든 요금제가 나열됩니다. 업그레이드하려는 요금제에 대한 라디오 단추를 클릭합니다.
* 업그레이드하려면 **확인**을 클릭합니다. 업그레이드하지 않으려면 **취소**를 클릭합니다.

**중요** 요금 청구 및 사용에 따라 영향이 있으므로 업그레이드하기 전에 대화 상자를 주의깊게 읽어야 합니다.

**권장 사항에 대한 내 구독은 언제 종료됩니까?**

구독은 고객이 구독을 취소할 때 종료됩니다. 구독을 취소하려면 다음 지침을 참조하세요.

**권장 사항 구독을 취소하려면 어떻게 해야 합니까?**

구독을 취소하려면 다음 단계를 따릅니다. 현재 구독이 유료 구독이면 구독은 현재 청구 기간이 끝날 때까지 계속 유효합니다. 취소를 즉시 적용하려면 [Microsoft 지원](https://support.microsoft.com/oas/default.aspx?gprid=17024&st=1&wfxredirect=1&sd=gn)으로 문의하세요.

**참고** 청구 기간이 끝나기 전에 취소하는 경우나 청구 기간에 사용되지 않은 트랜잭션에 대해서는 환불이 제공되지 않습니다.

* [제품 페이지](https://datamarket.azure.com/dataset/amla/recommendations)로 이동합니다.
* 아직 로그인하지 않았으면 마켓플레이스에 로그인합니다.
* 데이터 집합 이름 및 상태의 오른쪽에서 **취소** 를 클릭합니다. 현재 청구 기간이 끝나거나 트랜잭션 제한에 도달할 때 중 먼저 발생하는 시기까지 이 구독을 사용할 수 있습니다.

새 구독을 구입할 수 있도록 즉시 구독을 취소하려면 [Microsoft 지원](https://support.microsoft.com/oas/default.aspx?gprid=17024&st=1&wfxredirect=1&sd=gn)에서 티켓을 발행하세요.

## <a name="getting-started-with-recommendations"></a>권장 사항 시작하기
**권장 사항이 고객에게 적합합니까?** 

기계 학습 권장 사항은 고객에 대한 제품 또는 서비스의 교차 판매 및 상향 판매에 대한 권장 사항에 의존하는 조직과 비즈니스에 적합합니다. 고객을 응대하는 웹 사이트, 영업 인력, 내부 판매 인력 또는 콜 센터가 있고 수십 개의 제품이나 서비스가 포함된 카탈로그를 제공하는 경우 권장 사항을 활용하여 수익을 높일 수 있습니다. 

권장 사항을 사용한 실험은 매우 간단하게 디자인되었습니다. 현재 API 기반 버전은 필수 기본 프로그래밍 기술이 필요하지 않습니다. 지원이 필요한 경우 웹사이트를 개발한 공급업체에 문의하세요. 내부 IT 부서 또는 사내 개발자가 있는 경우 권장 사항을 작업에 사용할 수 있어야 합니다. 

**권장 사항을 설정하기 위한 필수 구성 요소는 무엇입니까?**

권장 사항을 사용하려면 카탈로그와 관련된 사용자 선택 로그가 있어야 합니다. 해당 로그가 없고 고객 응대 웹 사이트를 운영하는 경우 권장 사항에서 대신 사용자 활동을 수집할 수 있습니다. 

권장 사항에는 제품 또는 서비스에 대한 카탈로그도 필요합니다. 카탈로그가 없을 경우 권장 사항에서는 실제 고객 사용 데이터를 사용하고 카탈로그를 추출할 수 있습니다. "묵시적" 카탈로그에는 사용자 트랜잭션의 일부로 "보고"되지 않은 항목이 포함되지 않습니다.

**처음에 권장 사항을 설정하려면 어떻게 해야 합니까?**

권장 사항을 [구독](https://datamarket.azure.com/dataset/amla/recommendations)한 후 [Azure 기계 학습 권장 사항 – 빠른 시작 가이드](machine-learning-recommendation-api-quick-start-guide.md)의 API 설명서를 사용하여 서비스를 설정해야 합니다.

**API 설명서는 어디서 찾을 수 있습니까?** 

API 설명서는 [Azure Machine Learning 권장 사항 - 빠른 시작 가이드](machine-learning-recommendation-api-quick-start-guide.md)에 있습니다.

**카탈로그 및 사용 데이터를 권장 사항에 업로드하는 데 사용할 수 있는 옵션은 무엇입니까?**

카탈로그 및 사용 데이터를 업로드하는 두 가지 옵션이 있습니다. CRM 시스템 또는 기타 로그에서 이러한 데이터를 내보내고 권장 사항에 업로드하거나, 사용자 활동을 추적할 웹 사이트에 태그를 추가할 수 있습니다. 두 번째 방법을 사용하면 데이터가 Azure에 저장됩니다.

## <a name="maintenance-and-support"></a>유지 관리 및 지원
**내 데이터 집합은 얼마나 확장할 수 있습니까?**

각 데이터 집합은 카탈로그 항목 최대 100,000 개와 사용 데이터 최대 2048MB를 포함할 수 있습니다.
또한 구독은 데이터 집합(모델) 최대 10개를 포함할 수 있습니다.

**권장 사항에 대한 기술 지원은 어디서 받을 수 있습니까?**

기술 지원은 [Microsoft Azure 지원](https://social.msdn.microsoft.com/forums/azure/home?forum=MachineLearning) 사이트에서 받을 수 있습니다.

**사용 약관은 어디서 찾을 수 있습니까?**

[Microsoft Azure 기계 학습 권장 사항 API 서비스 약관](https://datamarket.azure.com/dataset/amla/recommendations#terms)에서 찾을 수 있습니다.


