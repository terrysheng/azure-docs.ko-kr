---
title: "Azure CLI 스크립트 샘플 - 운영 체제 디스크 탑재 | Microsoft Docs"
description: "Azure CLI 스크립트 샘플 - 운영 체제 디스크 탑재"
services: virtual-machines-linux
documentationcenter: virtual-machines
author: neilpeterson
manager: timlt
editor: tysonn
tags: azure-service-management
ms.assetid: 
ms.service: virtual-machines-linux
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: vm-linux
ms.workload: infrastructure
ms.date: 02/27/2017
ms.author: nepeters
translationtype: Human Translation
ms.sourcegitcommit: 0d8472cb3b0d891d2b184621d62830d1ccd5e2e7
ms.openlocfilehash: cdd0a11e872d81dfbb35c7a0cbfa2e1f7234dc08
ms.lasthandoff: 03/21/2017

---

# <a name="troubleshoot-a-vms-operating-system-disk"></a>VM 운영 체제 디스크 문제 해결

이 스크립트는 실패했거나 문제가 있는 가상 컴퓨터의 운영 체제 디스크를 두 번째 가상 컴퓨터에 대한 데이터 디스크로 탑재합니다. 디스크 문제를 해결하거나 데이터를 복구할 때 유용할 수 있습니다. 

필요한 경우 [Azure CLI 설치 가이드](https://docs.microsoft.com/cli/azure/install-azure-cli)에 있는 지침을 사용하여 Azure CLI를 설치한 다음, `az login`을 실행하여 Azure와 연결합니다. 또한 기존 가상 컴퓨터가 필요합니다. 스크립트 샘플에서 기존 가상 컴퓨터의 리소스 그룹 및 이름을 업데이트합니다.

이 샘플은 Bash 셸에서 작동합니다. Windows 클라이언트에서 Azure CLI 스크립트 실행과 관련된 옵션은 [Windows에서 Azure CLI 실행](../virtual-machines-windows-cli-options.md)을 참조하세요.

## <a name="sample-script"></a>샘플 스크립트

[!code-azurecli[기본](../../../cli_scripts/virtual-machine/mount-os-disk/mount-os-disk.sh "VM 빠른 생성")]

## <a name="script-explanation"></a>스크립트 설명

이 스크립트는 다음 명령을 사용하여 리소스 그룹, 가상 컴퓨터 및 모든 관련된 리소스를 만듭니다. 테이블에 있는 각 명령은 명령에 해당하는 문서에 연결됩니다.

| 명령 | 참고 사항 |
|---|---|
| [az vm show](https://docs.microsoft.com/cli/azure/vm#show) | 가상 컴퓨터 목록을 반환합니다. 이 경우 가상 컴퓨터 운영 체제 디스크를 반환하는 데 쿼리 옵션이 사용됩니다. 그러면 이 값이 변수 이름 'uri'에 추가됩니다. |
| [az vm delete](https://docs.microsoft.com/cli/azure/vm#delete) | 가상 컴퓨터를 삭제합니다. |
| [az vm create](https://docs.microsoft.com/cli/azure/vm#create) | 가상 컴퓨터를 만듭니다.  |
| [az vm disk attach](https://docs.microsoft.com/cli/azure/vm/disk#attach) | 디스크를 가상 컴퓨터에 연결합니다. |
| [az vm list-ip-addresses](https://docs.microsoft.com/cli/azure/vm#list-ip-addresses) | 가상 컴퓨터의 IP 주소를 반환합니다. |

## <a name="next-steps"></a>다음 단계

Azure CLI에 대한 자세한 내용은 [Azure CLI 설명서](https://docs.microsoft.com/cli/azure/overview)를 참조하세요.

추가 가상 컴퓨터 CLI 스크립트 샘플은 [Azure Linux VM 설명서](../virtual-machines-linux-cli-samples.md?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json)에서 확인할 수 있습니다.

