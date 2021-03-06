---
title: "Machine Learning 작업 영역 만들기 | Microsoft Docs"
description: "Azure 기계 학습 스튜디오의 작업 영역을 만드는 방법"
services: machine-learning
documentationcenter: 
author: garyericson
manager: jhubbard
editor: cgronlun
ms.assetid: aa96b784-ac6c-44bc-a28a-85d49fbe90a2
ms.service: machine-learning
ms.workload: data-services
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 02/27/2017
ms.author: garye;bradsev;ahgyger
translationtype: Human Translation
ms.sourcegitcommit: 613cf7e34d69afa21b1808ffe57af9a8b64944f5
ms.openlocfilehash: 182a34822e71d63f4d7229548ae3f59d9f195337
ms.lasthandoff: 03/01/2017


---
# <a name="create-and-share-an-azure-machine-learning-workspace"></a>Azure 기계 학습 작업 영역 만들기 및 공유
이 메뉴는 CAPS(Cortana 분석 프로세스)에서 사용하는 다양한 데이터 과학 환경을 설정하는 방법을 설명하는 항목에 연결됩니다.

[!INCLUDE [data-science-environment-setup](../../includes/cap-setup-environments.md)]

Azure 기계 학습 스튜디오를 사용하려면 기계 학습 작업 영역이 있어야 합니다. 이 작업 영역에는 실험을 만들고 관리, 게시하는 데 필요한 도구가 들어 있습니다.

[!INCLUDE [machine-learning-free-trial](../../includes/machine-learning-free-trial.md)]

### <a name="to-create-a-workspace"></a>작업 영역을 만들려면
1. [Azure 포털](https://portal.azure.com/)

    > [!NOTE]
    > 로그인하여 작업 영역을 만들려면 Azure 구독 관리자여야 합니다. 
    >
    > 

2. **+새로 만들기**를 클릭합니다.

3. **인텔리전스 + 분석**을 선택하고 **Machine Learning 작업 영역**을 클릭한 후 **만들기**를 클릭합니다.

4. 작업 영역 정보를 입력합니다.

    - *작업 영역 이름*은 공백으로 끝나지 않고 최대 260자로 구성할 수 있습니다. 이름에는 다음과 같은 문자를 포함하지 않아야 합니다. `< > * % & : \ ? + /`
    - 사용자가 선택하거나 만든 *웹 서비스 계획*은 사용자가 선택한 연결된 *가격 책정 계층*과 함께, 이 작업 영역에서 웹 서비스를 배포하는 경우 사용됩니다.

    ![새 작업 영역 만들기](media/machine-learning-create-workspace/create-new-workspace.png)

5. **만들기**

작업 영역이 배포되면 Machine Learning Studio에서 열 수 있습니다.

1. Machine Learning Studio([https://studio.azureml.net/](https://studio.azureml.net/))로 이동합니다.

2. 오른쪽 위 모서리에서 작업 영역을 선택합니다.

    ![작업 영역 선택](media/machine-learning-create-workspace/open-workspace.png)

3. **내 실험**을 클릭합니다.

    ![실험 열기](media/machine-learning-create-workspace/my-experiments.png)

작업 영역을 관리하는 방법에 대한 자세한 내용은 [Azure 기계 학습 작업 영역 관리](machine-learning-manage-workspace.md)를 참조하세요.
작업 영역을 만드는 데 문제가 발생한 경우 [문제 해결 가이드: Machine Learning 작업 영역 만들기 및 연결](machine-learning-troubleshooting-creating-ml-workspace.md)을 참조하세요.


## <a name="sharing-an-azure-machine-learning-workspace"></a>Azure 기계 학습 작업 영역 공유
Machine Learning 작업 영역이 만들어진 후에는 사용자를 작업 영역에 초대하고 작업 영역과 모든 실험, 데이터 집합, Notebook 등에 대한 액세스를 공유할 수 있습니다. 이 두 역할 중 하나에 사용자를 추가할 수 있습니다.

* **사용자** - 작업 영역 사용자는 작업 영역에서 실험, 데이터 집합 등을 만들기, 열기, 수정 및 삭제할 수 있습니다.
* **소유자** - 소유자는 사용자가 수행할 수 있는 작업 외에도 작업 영역에 사용자를 초대 및 제거할 수 있습니다.

> [!NOTE]
> 작업 영역을 만든 관리자 계정은 작업 영역 소유자 권한으로 작업 영역에 자동으로 추가됩니다. 그러나 구독에 있는 다른 관리자 또는 사용자에게는 작업 영역에 대한 액세스 권한이 자동으로 부여되지 않으며 명시적으로 초대해야 합니다.
> 
> 

### <a name="to-share-a-workspace"></a>작업 영역을 공유하려면

1. Machine Learning Studio([https://studio.azureml.net/Home](https://studio.azureml.net/Home))에 로그인합니다.

2. 왼쪽 패널에서 **설정**을 클릭합니다.

3. **사용자** 탭을 클릭합니다.

4. 페이지 맨 아래에 있는 **더 많은 사용자 초대**를 클릭합니다.

    ![Studio 설정](media/machine-learning-create-workspace/settings.png)

5. 하나 이상의 전자 메일 주소를 입력합니다. 사용자에게는 유효한 Microsoft 계정(Azure Active Directory에서) 또는 Azure Active Directory의 조직 계정만 필요합니다.

6. 사용자를 소유자 또는 사용자로 추가할지 여부를 선택합니다.

7. **확인** 확인 표시 단추를 클릭합니다.

추가된 각 사용자는 공유 작업 영역에 로그인하는 방법에 대한 설명이 포함된 전자 메일을 받게 됩니다.

> [!NOTE]
> 이 작업 영역에서 웹 서비스를 배포 또는 관리할 수 있는 사용자인 경우 Azure 구독에서 참여자 또는 관리자여야 합니다. 




