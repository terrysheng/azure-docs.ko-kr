---
title: "Azure Marketplace에서 가상 컴퓨터 이미지 관리 | Microsoft Docs"
description: "초기 게시 후 Azure 마켓플레이스에서 가상 컴퓨터 이미지를 관리하는 방법에 대한 자세한 가이드입니다."
services: Azure Marketplace
documentationcenter: 
author: HannibalSII
manager: hascipio
editor: 
ms.assetid: cc8648d4-59c2-4678-b47d-992300677537
ms.service: marketplace
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: Azure
ms.workload: na
ms.date: 08/03/2016
ms.author: hascipio;
translationtype: Human Translation
ms.sourcegitcommit: 5919c477502767a32c535ace4ae4e9dffae4f44b
ms.openlocfilehash: ed2921750f93f344a4c3dbef31d9f523dedc0aae


---
# <a name="post-production-guide-for-virtual-machine-offers-in-the-azure-marketplace"></a>Azure 마켓플레이스의 가상 컴퓨터 제품에 대한 프로덕션 이후 가이드
이 문서에서는 Azure 마켓플레이스의 라이브 가상 컴퓨터 제품을 업데이트하는 방법을 설명합니다. 또한 기존 제품에 하나 이상의 새 SKU를 추가 및 Azure 마켓플레이스에서 라이브 가상 컴퓨터 제품 또는 SKU를 제거하는 과정을 안내합니다.

[Azure 포털](http://portal.azure.com)에서 제품/SKU가 준비되면 아래에 지정된 필드를 변경할 수 없습니다.

* **제품 식별자:** [게시 포털 -> 가상 컴퓨터 -> 제품 선택 -> VM 이미지 탭 -> 제품 식별자]
* **SKU 식별자:** [게시 포털 -> 가상 컴퓨터 -> 제품 선택 -> SKU 탭 -> SKU 추가]
* **게시자 네임스페이스:** [게시 포털 -> 가상 컴퓨터 -> 연습 탭 -> 회사에 대한 정보 제공("2단계 회사 등록" 참조) -> 게시자 네임스페이스 -> 네임스페이스]

[Azure 마켓플레이스](http://azure.microsoft.com/marketplace)에서 제품/SKU가 나열되면 아래에 지정된 필드를 변경할 수 없습니다.

* **제품 식별자:** [게시 포털 -> 가상 컴퓨터 -> 제품 선택 -> VM 이미지 탭 -> 제품 식별자]
* **SKU 식별자:** [게시 포털 -> 가상 컴퓨터 -> 제품 선택 -> SKU 탭 -> SKU 추가]
* **게시자 네임스페이스:** [게시 포털 -> 가상 컴퓨터 -> 연습 탭 -> 회사에 대한 정보 제공(2단계 등록 참조) -> 게시자 네임스페이스 -> 네임스페이스]
* **포트:** [게시 포털 -> 가상 컴퓨터 -> 제품 선택 -> VM 이미지 탭 -> 포트 열기]
* **나열된 SKU의 가격 책정 변경**
* **나열된 SKU의 청구 모델 변경**
* **나열된 SKU의 청구 지역 제거**
* **나열된 SKU의 데이터 디스크 수 변경**

## <a name="1-how-to-update-the-technical-details-of-a-sku"></a>1. SKU의 기술 세부 정보를 업데이트하는 방법
나열된 SKU에 새 버전을 추가하고 아래 제공된 단계에 따라 제품을 다시 게시할 수 있습니다.

1. [게시 포털](https://publish.windowsazure.com)에 로그인합니다.
2. **가상 컴퓨터** 탭으로 이동하고 제품을 선택합니다.
3. 왼쪽 메뉴에서 **VM 이미지** 탭을 클릭합니다.
4.  **계획** 탭의 **VM 이미지** 섹션에서 업데이트하려는 SKU를 찾습니다.
5. 그런 후에 SKU의 새 버전 번호를 추가하고 **"+"** 버튼을 클릭합니다. 새 버전은 X, Y, Z가 정수인 X.Y.Z 형식이어야 합니다. 버전 변경은 증분되어야만 합니다.
6. **OS VHD URL** 상자에 운영 체제 VHD에 대해 만들어진 공유 액세스 서명 URI를 추가하고 변경 내용을 저장합니다.
   
   > [!IMPORTANT]
   > 나열된 SKU의 데이터 디스크 수를 늘리거나 줄일 수는 없습니다. 이 경우 새로운 SKU를 만들어야 합니다. 자세한 내용은 [3. 나열된 제품에 새 SKU를 추가하는 방법](#3-how-to-add-a-new-sku-under-a-live-offer) 섹션을 참조하세요.
   > 
   > 
7. 변경 후 **게시** 탭으로 이동하고 **스테이징으로 푸시** 버튼을 클릭합니다. 스테이징 환경에서 제품 테스트에 대한 자세한 지침은 이 [링크](marketplace-publishing-vm-image-test-in-staging.md)
8. 스테이징에서 제품을 테스트한 후 게시 포털의 **게시** 탭으로 이동하고 **프로덕션으로 푸시 승인 요청** 버튼을 클릭하여 Azure Marketplace에 제품을 다시 게시합니다.
   
    ![drawing](media/marketplace-publishing-vm-image-post-publishing/img01_07.png)

## <a name="2-how-to-update-the-non-technical-details-of-an-offer-or-a-sku"></a>2. 제품 또는 SKU의 비기술적인 세부 정보를 업데이트하는 방법
Azure 마켓플레이스에서 라이브 제품 또는 SKU의 비기술적인(마케팅, 법률, 지원, 범주) 세부 정보를 업데이트할 수 있습니다.

### <a name="21-update-the-offer-description-and-logos"></a>2.1 제품 설명 및 로고 업데이트
제품 세부 정보를 업데이트하고 아래 제공된 단계에 따라 제품을 다시 게시할 수 있습니다.

1. [게시 포털](https://publish.windowsazure.com)에 로그인합니다.
2. **가상 컴퓨터** 탭으로 이동하고 제품을 선택합니다.
3. 왼쪽 메뉴에서 **마케팅** 탭을 클릭합니다.
4. **영어(미국)** 버튼을 클릭합니다.
5. 왼쪽 메뉴에서 **세부 정보** 탭을 클릭합니다. *세부 정보* 탭의 **설명** 섹션 아래에서 제품 제목, 제품 요약, 제품 세부 요약을 업데이트하고 변경 내용을 저장할 수 있습니다.
   
   > [!NOTE]
   > SKU 세부 정보를 업데이트하는 동안 다음을 주의하세요.
   > **제품 설명 및 SKU 설명에 중복 텍스트는 입력하지 않습니다. SKU 제목 및 제품 세부 요약에 중복 텍스트는 입력하지 않습니다. SKU 제목 및 제품 요약에 중복 텍스트는 입력하지 않습니다.**
   > 
   > 
   
    ![drawing](media/marketplace-publishing-vm-image-post-publishing/img02.1_05.png)
6. *세부 정보* 탭의 **로고** 섹션 아래에서 로고를 업데이트할 수 있습니다. 그러나 로고가 [Azure Marketplace 지침](marketplace-publishing-push-to-staging.md#step-1-provide-marketplace-marketing-content)을 따르는지 확인합니다(1단계: Marketplace 마케팅 콘텐츠 제공 -> 세부 정보 -> Azure Marketplace 로고 지침 섹션 참고).
   
   > [!NOTE]
   > 대표 아이콘은 선택 사항입니다. 대표 아이콘을 업로드하지 않아도 됩니다. 그러나 대표 아이콘을 업로드하면 게시 포털에서 삭제할 프로비전이 없습니다. 이 경우 [대표 아이콘 지침](marketplace-publishing-push-to-staging.md#step-1-provide-marketplace-marketing-content)을 따라야 합니다(1단계: Marketplace 마케팅 콘텐츠 제공 -> 세부 정보 -> 대표 로고 배너에 대한 추가 지침 섹션 참고).
   > 
   > 
7. 변경 후 **게시** 탭으로 이동하고 **스테이징으로 푸시** 버튼을 클릭합니다. 스테이징 환경에서 제품 테스트에 대한 자세한 지침은 이 [링크](marketplace-publishing-vm-image-test-in-staging.md)를 참조하세요.
8. 스테이징에서 제품을 테스트한 후 게시 포털의 **게시** 탭으로 이동하고 **프로덕션으로 푸시 승인 요청** 버튼을 클릭하여 Azure Marketplace에 제품을 다시 게시합니다.
   
    ![drawing](media/marketplace-publishing-vm-image-post-publishing/img02.1_08.png)

### <a name="22-update-the-sku-description"></a>2.2. SKU 설명 업데이트
SKU 세부 정보를 업데이트하고 아래 제공된 단계에 따라 제품을 다시 게시할 수 있습니다.

1.  [게시 포털](https://publish.windowsazure.com)
2. **가상 컴퓨터** 탭으로 이동하고 제품을 선택합니다.
3. 왼쪽 메뉴에서 **마케팅** 탭을 클릭합니다.
4. **영어(미국)** 버튼을 클릭합니다.
5. 왼쪽 메뉴에서 **계획** 탭을 클릭합니다. *계획* 탭의 **SKU** 섹션 아래에서 SKU 제목, SKU 요약 및 SKU 설명 세부 정보를 업데이트하고 변경 내용을 저장할 수 있습니다.
   
   > [!NOTE]
   > SKU 세부 정보를 업데이트하는 동안 다음을 주의하세요. **제품 설명 및 SKU 설명에 중복 텍스트는 입력하지 않습니다. SKU 제목 및 제품 세부 요약에 중복 텍스트는 입력하지 않습니다. SKU 제목 및 제품 요약에 중복 텍스트는 입력하지 않습니다.**
   > 
   > 
6. 변경 후 **게시** 탭으로 이동하고 **스테이징으로 푸시** 버튼을 클릭합니다. 스테이징 환경에서 제품 테스트에 대한 자세한 지침은 이 링크를 참조하세요.
7. 스테이징에서 제품을 테스트한 후 게시 포털의 **게시** 탭으로 이동하고 **프로덕션으로 푸시 승인 요청** 버튼을 클릭하여 Azure Marketplace에 제품을 다시 게시합니다.
   
    ![drawing](media/marketplace-publishing-vm-image-post-publishing/img02.2_07.png)

### <a name="23-change-the-existing-links-or-add-new-links"></a>2.3 기존 링크 변경 또는 새 링크 추가
기존 링크를 변경하거나 새 링크를 추가한 다음 아래 단계를 수행하여 제품을 다시 게시할 수 있습니다.

1.  [게시 포털](https://publish.windowsazure.com)
2. **가상 컴퓨터** 탭으로 이동하고 제품을 선택합니다.
3. 왼쪽 메뉴에서 **마케팅** 탭을 클릭합니다.
4. **영어(미국)** 버튼을 클릭합니다.
5. 왼쪽 메뉴에서 **링크** 탭을 클릭합니다.
6. 새 링크를 추가하려는 경우 *링크* 섹션 아래에서 **링크 추가** 버튼을 클릭합니다. *"링크 추가"* 대화 상자가 열립니다. 이 대화 상자에서 링크 제목 및 URL 필드를 추가하고 변경 내용을 저장할 수 있습니다. 고객에게 도움이 될 수 있는 정보를 포함하는 모든 링크를 입력할 수 있습니다.
7. 기존 링크를 업데이트 또는 삭제하려는 경우 적절한 링크를 선택하고 편집 단추 또는 삭제 단추를 적절하게 클릭합니다.
   
   > [!NOTE]
   > 이러한 링크는 프로덕션 요청 프로세스 동안 유효성 검사를 받으므로 이 섹션에서 입력한 링크가 제대로 작동하는지 확인합니다.
   > 
   > 
8. 변경 후 **게시** 탭으로 이동하고 **스테이징으로 푸시** 버튼을 클릭합니다. 스테이징 환경에서 제품 테스트에 대한 자세한 지침은 이 [링크](marketplace-publishing-vm-image-test-in-staging.md)를 참조하세요.
9. 스테이징에서 제품을 테스트한 후 게시 포털의 **게시** 탭으로 이동하고 **프로덕션으로 푸시 승인 요청** 버튼을 클릭하여 Azure Marketplace에 제품을 다시 게시합니다.
   
    ![drawing](media/marketplace-publishing-vm-image-post-publishing/img02.3_09-01.png)
   
    ![drawing](media/marketplace-publishing-vm-image-post-publishing/img02.3-2.png)

### <a name="24-change-an-existing-sample-image-or-add-a-new-sample-image"></a>2.4 기존 샘플 이미지 변경 또는 새 샘플 이미지 추가
기존 샘플 이미지를 변경하거나 새 샘플 이미지를 추가한 다음 아래 단계를 수행하여 제품을 다시 게시할 수 있습니다.

> [!NOTE]
> 하나의 샘플 이미지만 [https://portal.azure.com](https://portal.azure.com)에 표시됩니다.
> 
> 

1.  [게시 포털](https://publish.windowsazure.com)
2. **가상 컴퓨터** 탭으로 이동하고 제품을 선택합니다.
3. 왼쪽 메뉴에서 **마케팅** 탭을 클릭합니다.
4. **영어(미국)** 버튼을 클릭합니다.
5. 왼쪽 메뉴에서 **샘플 이미지** 탭을 클릭합니다.
6. 새 샘플 이미지를 추가하려는 경우 *샘플 이미지* 섹션 아래에서 **새 이미지 업로드** 버튼을 클릭한 다음 변경 내용을 저장합니다.
   
   > [!NOTE]
   > 샘플 이미지를 포함하는 것은 선택적인 단계입니다.
   > 
   > 
7. 기존 샘플 이미지를 업데이트 또는 삭제하려는 경우 적절한 샘플 이미지를 찾은 다음 **이미지 바꾸기** 버튼 또는 삭제 버튼을 적절하게 클릭합니다.
8. 변경 후 **게시** 탭으로 이동하고 **스테이징으로 푸시** 버튼을 클릭합니다. 스테이징 환경에서 제품 테스트에 대한 자세한 지침은 이 [링크](marketplace-publishing-vm-image-test-in-staging.md)를 참조하세요.
9. 스테이징에서 제품을 테스트한 후 게시 포털의 **게시** 탭으로 이동하고 **프로덕션으로 푸시 승인 요청** 버튼을 클릭하여 Azure Marketplace에 제품을 다시 게시합니다.
   
    ![drawing](media/marketplace-publishing-vm-image-post-publishing/img02.4_09.png)

### <a name="25-update-the-legal-content"></a>2.5 법적 콘텐츠 업데이트
법적 콘텐츠를 업데이트하고 아래 제공된 단계에 따라 제품을 다시 게시할 수 있습니다.

1.  [게시 포털](https://publish.windowsazure.com)
2. **가상 컴퓨터** 탭으로 이동하고 제품을 선택합니다.
3. 왼쪽 메뉴에서 **마케팅** 탭을 클릭합니다.
4. **영어(미국)** 버튼을 클릭합니다.
5. 왼쪽 메뉴에서 **법적 고지 사항** 탭을 클릭합니다. *법적 고지 사항* 섹션 아래에서 정책/사용 약관을 업데이트할 수 있습니다. *사용 약관* 텍스트 상자에 정책/용어를 입력하거나 붙여 넣고 변경 내용을 저장합니다.
6. 사용 약관의 문자 제한은 1,000,000자입니다.
7. 변경 후 **게시** 탭으로 이동하고 **스테이징으로 푸시** 버튼을 클릭합니다. 스테이징 환경에서 제품 테스트에 대한 자세한 지침은 이 [링크](marketplace-publishing-vm-image-test-in-staging.md)
8. 스테이징에서 제품을 테스트한 후 게시 포털의 **게시** 탭으로 이동하고 **프로덕션으로 푸시 승인 요청** 버튼을 클릭하여 Azure Marketplace에 제품을 다시 게시합니다.
   
    ![drawing](media/marketplace-publishing-vm-image-post-publishing/img02.5_08.png)

### <a name="26-update-the-support-information"></a>2.6 지원 정보 업데이트
지원 정보를 업데이트하고 아래 제공된 단계에 따라 제품을 다시 게시할 수 있습니다.

1.  [게시 포털](https://publish.windowsazure.com)
2. **가상 컴퓨터** 탭으로 이동하고 제품을 선택합니다.
3. 왼쪽 메뉴에서 **지원** 탭을 클릭합니다.
4. *지원* 탭의 **엔지니어링 연락처** 섹션 아래에서 연락처 세부 정보를 업데이트할 수 있습니다. 세부 정보는 파트너와 Microsoft 간의 내부 통신에만 사용됩니다.
5. **지원** 탭의 *고객 지원* 섹션 아래에서 **이름, 전자 메일, 전화 번호** 및 **지원 URL**과 같은 지원 연락처 세부 정보를 업데이트할 수 있습니다. 세부 정보는 파트너와 Microsoft 간의 내부 통신에만 사용됩니다.
   
   > [!NOTE]
   > 전자 메일 지원만 제공하려는 경우 **고객 지원** 섹션 아래에 더미 전화번호를 제공합니다. 이 경우에 제공된 전자 메일이 대신 사용됩니다.
   > 
   > 
6. 변경 후 **게시** 탭으로 이동하고 **스테이징으로 푸시** 버튼을 클릭합니다. 스테이징 환경에서 제품 테스트에 대한 자세한 지침은 이 [링크](marketplace-publishing-vm-image-test-in-staging.md)
7. 스테이징에서 제품을 테스트한 후 게시 포털의 **게시** 탭으로 이동하고 **프로덕션으로 푸시 승인 요청** 버튼을 클릭하여 Azure Marketplace에 제품을 다시 게시합니다.
   
    ![drawing](media/marketplace-publishing-vm-image-post-publishing/img02.6_07.png)

### <a name="27-update-the-categories"></a>2.7 범주 업데이트
제품에 대한 범주 섹션을 업데이트하고 아래 제공된 단계에 따라 제품을 다시 게시할 수 있습니다.

1.  [게시 포털](https://publish.windowsazure.com)
2. **가상 컴퓨터** 탭으로 이동하고 제품을 선택합니다.
3. 왼쪽 메뉴에서 **범주** 탭을 클릭합니다.
4. *범주* 섹션 아래에서 제품에 대한 범주를 업데이트하고 변경 내용을 저장할 수 있습니다. Azure 마켓플레이스 갤러리에 대해 최대 5개의 범주를 선택할 수 있습니다.
5. 변경 후 **게시** 탭으로 이동하고 **스테이징으로 푸시** 버튼을 클릭합니다. 스테이징 환경에서 제품 테스트에 대한 자세한 지침은 이 [링크](marketplace-publishing-vm-image-test-in-staging.md)
6. 스테이징에서 제품을 테스트한 후 게시 포털의 **게시** 탭으로 이동하고 **프로덕션으로 푸시 승인 요청** 버튼을 클릭하여 Azure Marketplace에 제품을 다시 게시합니다.
   
    ![drawing](media/marketplace-publishing-vm-image-post-publishing/img02.7_06.png)

## <a name="3-how-to-add-a-new-sku-under-a-listed-offer"></a>3. 나열된 제품에 새 SKU를 추가하는 방법
아래에서 제공하는 단계를 수행하여 라이브 제품 아래에 새로운 SKU를 추가할 수 있습니다.

1. [게시 포털](https://publish.windowsazure.com)에 로그인합니다.
2. **가상 컴퓨터** 탭으로 이동하고 제품을 선택합니다.
3. 왼쪽 메뉴에서 **계획** 탭을 클릭합니다. 그다음에 **SKU 추가** 버튼을 클릭합니다.  새 대화 상자가 열립니다. 소문자로 SKU 식별자를 입력합니다. BYOL 청구 모델로 새 SKU를 게시하려는 경우 BYOL(Bring-your-own billing model)에 대한 확인란을 선택합니다. 그렇지 않으면 BYOL에 대한 확인란의 선택을 취소합니다. 그 다음 대화 상자의 확인 표시를 클릭하여 새로운 SKU를 만듭니다. 새로운 SKU에 대한 BYOL 청구 모델에 대해 선택하지 않은 경우 청구 모델은 새 SKU에 대해 자동으로 Hourly로 설정됩니다. Hourly 청구 모델에 대해 30일 무료 평가판을 사용하도록 설정하려는 경우 "무료 평가판이 있나요?"에 대해 "1개월" 옵션을 클릭합니다. 그렇지 않은 경우 "평가판 없음"을 선택합니다. [참고: 새 SKU를 만드는 동안 대화 상자에서 BYOL을 선택하지 않은 경우에만  "무료 평가판이 있나요?" 옵션이 표시됩니다.]
   
   > [!IMPORTANT]
   > Azure 마켓플레이스에서 솔루션 템플릿 제품 게시에 대해 승인한 경우 "솔루션 템플릿을 통해 항상 구입되어야 하기 때문에 마켓플레이스에서 이 SKU를 숨깁니다" 옵션은 "예"로 표시되어야 합니다. 그렇지 않은 경우 이 옵션은 항상 "아니요"로 표시되어야 합니다.
   > 
   > 
4. 이제 왼쪽 메뉴에서 **VM 이미지** 탭을 클릭하고 생성한 새로운 SKU를 찾습니다.
5. 새로운 SKU를 설정하려면 이 [링크](marketplace-publishing-vm-image-creation.md#5-obtain-certification-for-your-vm-image) 의 5단계의 지침을 참조하세요.
6. 새로운 SKU에 대한 마케팅 자료를 추가하려면 1단계: 마켓플레이스 마케팅 콘텐츠 제공 -> 세부 정보 -> 이 [링크](marketplace-publishing-push-to-staging.md#step-1-provide-marketplace-marketing-content)의 2~5 섹션을 참조하세요.
7. 새로운 SKU에 대한 가격 정보를 추가하려면 2.1 섹션을 참조하세요. 이 [링크](marketplace-publishing-push-to-staging.md#step-2-set-your-prices)
8. 변경 후 **게시** 탭으로 이동하고 **스테이징으로 푸시** 버튼을 클릭합니다. 스테이징 환경에서 제품 테스트에 대한 자세한 지침은 이 [링크](marketplace-publishing-vm-image-test-in-staging.md)
9. 스테이징에서 제품을 테스트한 후 게시 포털의 **게시** 탭으로 이동하고 **프로덕션으로 푸시 승인 요청** 버튼을 클릭하여 Azure Marketplace에 제품을 다시 게시합니다.
   
    ![drawing](media/marketplace-publishing-vm-image-post-publishing/img03_09-01.png)
   
    ![drawing](media/marketplace-publishing-vm-image-post-publishing/img03_09-02.png)

## <a name="4-how-to-change-the-data-disk-count-for-a-listed-sku"></a>4. 나열된 SKU에 대한 데이터 디스크 수를 변경하는 방법
나열된 SKU의 데이터 디스크 수를 늘리거나 줄일 수는 없습니다. 이 경우 새로운 SKU를 만들어야 합니다. 자세한 내용은 [3. 라이브 제품에 새 SKU를 추가하는 방법](#3-how-to-add-a-new-sku-under-a-live-offer) 섹션을 참조하세요.

## <a name="5-how-to-delete-a-listed-offer-from-the-azure-marketplace"></a>5.    Azure 마켓플레이스에서 나열된 제품을 삭제하는 방법
라이브 제품을 제거하는 요청 시 해결해야 하는 다양한 측면이 있습니다. Azure 마켓플레이스에서 나열된 제품을 제거하려면 다음 단계를 수행하여 지원 팀의 지침을 확인하세요.

1. 이 [링크](https://support.microsoft.com/en-us/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=15635&ccsid=635993707583706681)를 사용하여 지원 티켓 제기
2. **"제품 관리"**로 문제 형식 선택 및 **"프로덕션 환경에서 제품 및/또는 SKU 수정"**으로 범주 선택
3. 요청 제출

지원 팀은 제품/SKU 삭제 프로세스를 안내합니다.

> [!NOTE]
> 제품이 초안 상태(예: 스테이징 또는 프로덕션에 있지 않은 경우)에 있는 동안 **내역** 탭 아래의 **초안 삭제** 버튼을 클릭하여 항상 제품을 삭제할 수 있습니다.
> 
> 

## <a name="6-how-to-delete-a-listed-sku-from-the-azure-marketplace"></a>6. Azure 마켓플레이스에서 나열된 SKU를 삭제하는 방법
아래에 제공된 단계를 수행하여 Azure 마켓플레이스에서 나열된 SKU를 삭제할 수 있습니다.

1. [게시 포털](https://publish.windowsazure.com)에 로그인합니다.
2. **가상 컴퓨터** 탭으로 이동하고 제품을 선택합니다.
3. 왼쪽 창에서 **SKU** 탭을 클릭합니다.
4. 삭제할 SKU를 선택하고 해당 SKU에 대한 삭제 버튼을 클릭합니다.
5. 완료되면 게시 포털의 게시 탭으로 이동하고 **프로덕션으로 푸시 승인 요청** 버튼을 클릭하여 Azure 마켓플레이스에 제품을 다시 게시합니다.
6. Azure 마켓플레이스에 제품이 다시 게시되면 SKU가 Azure 마켓플레이스 및 Azure 포털에서 삭제됩니다.

## <a name="7-how-to-delete-the-current-version-of-a-listed-sku-from-the-azure-marketplace"></a>7. Azure 마켓플레이스에서 나열된 현재 버전의 SKU를 삭제하는 방법
아래에 제공된 단계를 수행하여 Azure 마켓플레이스에서 나열된 SKU의 현재 버전을 삭제할 수 있습니다. 프로세스가 완료되면 SKU가 이전 버전으로 롤백됩니다.

1. [게시 포털](https://publish.windowsazure.com)에 로그인합니다.
2. **가상 컴퓨터** 탭으로 이동하고 제품을 선택합니다.
3. 왼쪽 창에서 **VM 이미지** 탭을 클릭합니다.
4. 현재 버전을 삭제할 SKU를 선택하고 해당 버전에 대한 삭제 버튼을 클릭합니다.
5. 완료되면 게시 포털의 **게시** 탭으로 이동하고 **프로덕션으로 푸시 승인 요청** 버튼을 클릭하여 Azure Marketplace에 제품을 다시 게시합니다.
6. Azure 마켓플레이스에 제품이 다시 게시되면 나열된 SKU의 현재 버전이 Azure 마켓플레이스 및 Azure 포털에서 삭제됩니다. SKU는 이전 버전으로 롤백됩니다.

## <a name="8-how-to-revert-listing-price-to-production-values"></a>8. 목록 가격을 프로덕션 값으로 되돌리는 방법
나열된 SKU의 가격을 변경했습니다(또는 나열된 SKU의 청구 지역을 제거함). Azure 마켓플레이스에서 지원되지 않으므로 내 가격을 프로덕션 값으로 되돌리려고 합니다. 어떻게 해야 하나요?

아래 제공된 단계를 따릅니다.

1. [게시 포털](https://publish.windowsazure.com)에 로그인합니다.
2. **가상 컴퓨터** 탭으로 이동하고 제품을 선택합니다.
3. 왼쪽 메뉴에서 **가격 책정** 탭을 클릭합니다.
4. 가격 책정 탭 아래에서 가격을 재설정할 지역을 선택합니다.
   
    ![그리기](media/marketplace-publishing-vm-image-post-publishing/img08-04.png)
5. 시간당 청구 모델의 SKU를 사용하는 경우 선택한 지역에 대한 프로덕션에 있으므로 모든 코어에 대한 가격을 재설정합니다. BYOL 청구 모델의 SKU를 사용하는 경우 외부 라이선스(BYOL) SKU 가용성 섹션에서 SKU에 대한 확인란을 선택하여 해당 지역에서 SKU를 사용할 수 있게 합니다(아래 스크린숏 참조).
   
    ![그리기](media/marketplace-publishing-vm-image-post-publishing/img08-05.png)
6. 이제 **미국의 가격에 따라 다른 마켓의 가격 자동 설정**버튼을 클릭합니다.
   
   > [!NOTE]
   > 버튼의 레이블은 선택한 지역에 따라 달라질 수 있습니다. 이 문서를 작성할 당시에, 미국을 선택했으므로 아래 스크린숏과 같이 "미국의 가격에 따라 다른 마켓의 가격 자동 설정"으로 버튼 레이블이 표시됩니다.
   > 
   > 
   
    ![그리기](media/marketplace-publishing-vm-image-post-publishing/img08-06.png)
7. 자동 가격 설정 마법사가 열립니다. 첫 번째 페이지에는 기본 마켓의 선택 옵션이 표시됩니다. 섹션을 만든 후 **“->”** 버튼을 클릭하여 다음 페이지로 이동합니다.
   
    ![drawing](media/marketplace-publishing-vm-image-post-publishing/img08-07.png)
8. 코어 및 계획을 선택하기 위한 옵션이 2페이지에 표시됩니다. 원하는 계획 및 코어를 선택하고 "->" 버튼을 클릭합니다.
   
    ![그리기](media/marketplace-publishing-vm-image-post-publishing/img08-08.png)
9. 3페이지에 마켓/지역이 표시됩니다. 모두 설정/해제 버튼을 클릭하여 모든 지역을 선택하거나 해당 지역의 확인란을 수동으로 선택합니다. "->" 버튼을 클릭하여 다음 페이지로 이동합니다.
   
    ![그리기](media/marketplace-publishing-vm-image-post-publishing/img08-09.png)
10. 4페이지에는 환율이 표시됩니다. 마침 버튼을 클릭하여 단계를 완료합니다. 마법사는 선택 항목에 따라 가격 책정을 재설정합니다.
11. 이제 가격 책정 탭으로 이동한 후 "요약 및 변경 내용 보기" 버튼을 클릭합니다.
    "버전 보기" 섹션의 "초안"과 "비교 대상" 섹션의 "프로덕션"을 선택합니다(아래 스크린숏 참조). 가격 책정에 차이점이 없으면 가격이 프로덕션 값으로 복귀된 것입니다.
    
    ![그리기](media/marketplace-publishing-vm-image-post-publishing/img08-11.png)
12. 변경 후 게시 탭으로 이동하고 **스테이징으로 푸시**버튼을 클릭합니다. 스테이징 환경에서 제품 테스트에 대한 자세한 지침은 이 [링크](marketplace-publishing-vm-image-test-in-staging.md)
13. 스테이징에서 제품을 테스트한 후 게시 포털의 게시 탭으로 이동하고 **프로덕션으로 푸시 승인 요청** 버튼을 클릭하여 Azure 마켓플레이스에 제품을 다시 게시합니다.

## <a name="9-how-to-revert-billing-model-to-production-values"></a>9. 청구 모델을 프로덕션 값으로 되돌리는 방법
나열된 SKU의 청구 모델을 변경했습니다. Azure 마켓플레이스에서 지원되지 않으므로 내 가격을 프로덕션 값으로 되돌리려고 합니다. 어떻게 해야 하나요?

다음 단계를 따르세요.

1. [게시 포털](https://publish.windowsazure.com)에 로그인합니다.
2. **가상 컴퓨터** 탭으로 이동하고 제품을 선택합니다.
3. 왼쪽 메뉴에서 **SKU** 탭을 클릭합니다.
4. 편집 버튼을 클릭하여 요금 청구 모델을 되돌립니다. 창이 열립니다. 그에 따라 **'청구 및 라이선스를 Azure 외부에서 수행(사용자 라이선스 필요)'** 확인란을 선택하거나 선택 취소합니다.
   
    ![그리기](media/marketplace-publishing-vm-image-post-publishing/img09-04.png)
5. 일단 완료되면 이 문서의 질문 8에 대한 답변을 참조하여 가격 책정을 되돌립니다.
6. 게시 포털의 **게시** 탭으로 이동한 후 제품을 스테이징으로 푸시하여 테스트합니다. 제품 테스트를 마친 후에는 **프로덕션으로 푸시 요청 승인** 버튼을 클릭하여 제품을 Azure 마켓플레이스에 다시 게시합니다.

## <a name="10-how-to-revert-visibility-setting-of-a-listed-sku-to-the-production-value"></a>10. 나열된 SKU의 표시 유형 설정을 프로덕션 값으로 복귀하는 방법
다음 단계를 따르세요.

1. [게시 포털](https://publish.windowsazure.com)에 로그인합니다.
2. **가상 컴퓨터** 탭으로 이동하고 제품을 선택합니다.
3. 왼쪽 메뉴에서 **SKU** 탭을 클릭합니다.
4. SKU를 선택하고 SKU의 표시 여부 설정을 프로덕션 값으로 되돌립니다.
   
    ![그리기](media/marketplace-publishing-vm-image-post-publishing/img10-04.png)
5. 변경을 수행한 후에는 **프로덕션으로 푸시 요청 승인** 버튼을 클릭하여 제품을 Azure 마켓플레이스에 다시 게시합니다.

## <a name="see-also"></a>참고 항목
* [시작: Azure 마켓플레이스에 제품을 게시하는 방법](marketplace-publishing-getting-started.md)
* [판매자 통찰력 보고 이해](marketplace-publishing-report-seller-insights.md)
* [지급 보고 이해](marketplace-publishing-report-payout.md)
* [클라우드 솔루션 공급자 대리점 인센티브를 변경하는 방법](marketplace-publishing-csp-incentive.md)
* [마켓플레이스에서 일반적인 게시 문제 해결](marketplace-publishing-support-common-issues.md)
* [게시자로 지원 받기](marketplace-publishing-get-publisher-support.md)
* [온-프레미스로 VM 이미지 만들기](marketplace-publishing-vm-image-creation-on-premise.md)
* [Azure Preview 포털에서 Windows를 실행하는 가상 컴퓨터 만들기](../virtual-machines/virtual-machines-windows-hero-tutorial.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json)




<!--HONumber=Nov16_HO3-->


