---
title: "5분 내에 Azure에서 첫 번째 PHP 웹앱 만들기 | Microsoft Docs"
description: "샘플 PHP 앱을 배포하여 App Service에서 웹앱을 실행하는 작업이 얼마나 쉬운지 알아봅니다."
services: app-service\web
documentationcenter: 
author: cephalin
manager: wpickett
editor: 
ms.assetid: 6feac128-c728-4491-8b79-962da9a40788
ms.service: app-service-web
ms.workload: web
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: hero-article
ms.date: 03/17/2017
ms.author: cephalin
translationtype: Human Translation
ms.sourcegitcommit: 0d8472cb3b0d891d2b184621d62830d1ccd5e2e7
ms.openlocfilehash: afecc8997631bf507c797e56a9e3fc0d1df27614
ms.lasthandoff: 03/21/2017


---
# <a name="create-your-first-php-web-app-in-azure-in-five-minutes"></a>5분 내에 Azure에서 첫 번째 PHP 웹앱 만들기
[!INCLUDE [app-service-web-selector-get-started](../../includes/app-service-web-selector-get-started.md)]

이 빠른 시작을 사용하면 몇 분 만에 [Azure App Service](../app-service/app-service-value-prop-what-is.md)에 첫 번째 PHP 웹앱을 배포할 수 있습니다.

시작하기 전에 Azure CLI가 설치되었는지 확인합니다. 자세한 내용은 [Azure CLI 설치 가이드](https://docs.microsoft.com/cli/azure/install-azure-cli)를 참조하세요.

## <a name="log-in-to-azure"></a>Azure에 로그인
`az login`을 실행하고 화면상의 지침을 따라 Azure에 로그인합니다.
   
```azurecli
az login
```
   
## <a name="create-a-resource-group"></a>리소스 그룹 만들기   
[리소스 그룹](../azure-resource-manager/resource-group-overview.md)을 만듭니다. 함께 관리하려는 웹앱 및 해당 SQL Database 백 엔드와 같은 모든 Azure 리소스를 배치하는 위치입니다.

```azurecli
az group create --location "West Europe" --name myResourceGroup
```

`---location`에 사용할 수 있는 가능한 값을 보려면 `az appservice list-locations` Azure CLI 명령을 사용합니다.

## <a name="create-an-app-service-plan"></a>앱 서비스 계획 만들기
Linux 컨테이너를 실행하는 "표준" [App Service 계획](../app-service/azure-web-sites-web-hosting-plans-in-depth-overview.md)을 만듭니다. 

```azurecli
az appservice plan create --name my-free-appservice-plan --resource-group myResourceGroup --is-linux --sku S1
```

## <a name="create-a-web-app"></a>웹앱 만들기
`<app_name>`에 고유한 이름이 있는 웹앱을 만듭니다.

```azurecli
az appservice web create --name <app_name> --resource-group myResourceGroup --plan my-free-appservice-plan
```

## <a name="configure-the-linux-container"></a>Linux 컨테이너 구성
기본 PHP 7.0.6 이미지를 사용하도록 Linux 컨테이너를 구성합니다.

```azurecli
az appservice web config update --php-version 7.0.6 --name <app_name> --resource-group myResourceGroup
```
## <a name="deploy-sample-application"></a>샘플 응용 프로그램 배포
GitHub에서 샘플 PHP 앱을 배포합니다.

```azurecli
az appservice web source-control config --name <app_name> --resource-group myResourceGroup \
--repo-url "https://github.com/Azure-Samples/app-service-web-php-get-started.git" --branch master --manual-integration 
```

## <a name="browse-to-web-app"></a>웹앱으로 이동
Azure에서 실시간으로 실행 중인 앱을 확인하려면 다음 명령을 실행합니다.

```azurecli
az appservice web browse --name <app_name> --resource-group myResourceGroup
```

축하합니다. 첫 번째 PHP 웹앱이 Azure App Service에서 실시간으로 실행 중입니다.

[!INCLUDE [cli-samples-clean-up](../../includes/cli-samples-clean-up.md)]

## <a name="next-steps"></a>다음 단계

미리 만든 [웹앱 CLI 스크립트](app-service-cli-samples.md)를 탐색합니다.

