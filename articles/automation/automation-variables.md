---
title: "Azure 자동화의 변수 자산 | Microsoft Docs"
description: "변수 자산은 Azure 자동화의 모든 runbook과 DSC 구성에서 사용할 수 있는 값입니다.  이 문서에서는 변수에 대해 자세히 알아보고 텍스트 작성과 그래픽 작성 모두에서 변수를 사용하는 방법을 설명합니다."
services: automation
documentationcenter: 
author: mgoedtel
manager: carmonm
editor: tysonn
ms.assetid: b880c15f-46f5-4881-8e98-e034cc5a66ec
ms.service: automation
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: infrastructure-services
ms.date: 03/10/2017
ms.author: magoedte;bwren
translationtype: Human Translation
ms.sourcegitcommit: 24d86e17a063164c31c312685c0742ec4a5c2f1b
ms.openlocfilehash: 4c0c4f8c0d6c7cdc98406559f1cd36c87d33bf47
ms.lasthandoff: 03/11/2017


---
# <a name="variable-assets-in-azure-automation"></a>Azure 자동화의 변수 자산

변수 자산은 자동화 계정의 모든 runbook 및 DSC 구성에 사용할 수 있는 값입니다. 이 값을 Azure 포털, Windows PowerShell 및 runbook 또는 DSC 구성 내에서 생성, 수정 및 검색할 수 있습니다. 자동화 변수는 다음과 같은 시나리오에 유용합니다.

- 여러 runbook 또는 DSC 구성 간에 값을 공유합니다.

- 동일한 runbook의 여러 작업 또는 DSC 구성 간에 값을 공유합니다.

- 포털에서 값을 관리하거나 runbook 또는 DSC 구성에 사용되는 Windows PowerShell 명령줄에서 값을 관리합니다(예: 특정 VM 이름 목록, 특정 리소스 그룹, AD 도메인 이름과 같은 공통 구성 항목 집합).  

runbook 또는 DSC 구성이 실패할지라도 계속 사용 가능할 수 있도록 자동화 변수는 유지됩니다.  값은 또 다른 runbook에 의해 사용되었던 runbook 또는 동일한 runbook에 사용되거나 다음에 실행되는 DSC 구성에 의해 설정됩니다.     

변수를 만들 때 암호화된 상태로 저장되도록 지정할 수 있습니다.  변수를 암호화하면 Azure 자동화에 안전하게 저장되며 Azure PowerShell 모듈의 일부로 제공되는 [Get-AzureRmAutomationVariable](https://msdn.microsoft.com/library/mt603849.aspx) cmdlet에서 해당 값을 검색할 수 없습니다.  오직 runbook 또는 DSC 구성의 **Get-AutomationVariable** 에서만 암호화 된 값을 검색할 수 있습니다.

> [!NOTE]
> Azure 자동화의 안전한 자산에는 자격 증명, 인증서, 연결, 암호화된 변수 등이 있습니다. 이러한 자산은 각 자동화 계정에 대해 생성되는 고유 키를 사용하여 암호화되고 Azure 자동화에 저장됩니다. 이 키는 마스터 인증서로 암호화되어 Azure 자동화에 저장됩니다. 자동화 계정에 대한 키는 보안 자산을 저장하기 전에 마스터 인증서를 사용하여 암호가 해독된 후 자산을 암호화하는 데 사용됩니다.

## <a name="variable-types"></a>변수 형식

Azure Portal에서 변수를 만들 때 드롭다운 목록에서 해당 데이터 형식을 지정해야 합니다. 그래야 포털에서 변수 값을 입력할 수 있는 적절한 컨트롤을 표시할 수 있습니다. 변수는 이 데이터 형식으로 제한되지 않으며 다른 형식의 값을 지정하려면 Windows PowerShell을 사용하여 변수를 설정해야 합니다. **정의되지 않음**을 지정하면 변수 값이 **$null**로 설정되므로 [Set-AzureAutomationVariable](http://msdn.microsoft.com/library/dn913767.aspx) cmdlet 또는 **Set-AutomationVariable** 활동을 사용하여 값을 설정해야 합니다.  포털에서는 복잡한 변수 형식의 값을 만들거나 변경할 수 없지만 Windows PowerShell에서는 모든 형식의 값을 제공할 수 있습니다. 복잡한 형식은 [PSCustomObject](http://msdn.microsoft.com/library/system.management.automation.pscustomobject.aspx)로 반환됩니다.

배열 또는 해시 테이블을 만들어 변수에 저장하여 여러 값을 단일 변수에 저장할 수 있습니다.

다음은 자동화에서 사용할 수 있는 변수 형식의 목록입니다.

* 문자열
* Integer
* DateTime
* Boolean
* Null

>[!NOTE]
>변수 자산은 1024자로 제한됩니다. 

## <a name="cmdlets-and-workflow-activities"></a>Cmdlet 및 워크플로 활동

다음 표에 나와있는 cmdlet은 Windows PowerShell을 사용하여 자동화 변수를 만들고 관리하는 데 사용됩니다. Automation Runbook과 DSC 구성에 사용할 수 있는 [Azure PowerShell 모듈](/powershell/azureps-cmdlets-docs)의 일부로 전송됩니다.

|Cmdlet|설명|
|:---|:---|
|[Get-AzureRmAutomationVariable](https://msdn.microsoft.com/library/mt603849.aspx)|기존 변수의 값을 검색합니다.|
|[New-AzureRmAutomationVariable](https://msdn.microsoft.com/library/mt603613.aspx)|새 변수를 만들고 해당 값을 설정합니다.|
|[Remove-AzureRmAutomationVariable](https://msdn.microsoft.com/library/mt619354.aspx)|기존 변수를 제거합니다.|
|[Set-AzureRmAutomationVariable](https://msdn.microsoft.com/library/mt603601.aspx)|기존 변수의 값을 설정합니다.|

다음 표의 워크플로 활동은 Runbook에서 자동화 변수에 액세스하는 데 사용됩니다. 오직 runbook 또는 DSC 구성에서만 사용 가능하며, Azure PowerShell 모듈의 일부로 전송되지 않습니다.

|워크플로 활동|설명|
|:---|:---|
|Get-AutomationVariable|기존 변수의 값을 검색합니다.|
|Set-AutomationVariable|기존 변수의 값을 설정합니다.|

> [!NOTE] 
> **Get-AutomationVariable**의 Name 매개변수에서는 변수를 사용하면 안 됩니다. runbook 또는 DSC 구성과 design time의 자격 증명 간에 종속성이 발견되어 복잡해질 수 있기 때문입니다.

## <a name="creating-an-automation-variable"></a>Automation 변수 만들기

### <a name="to-create-a-variable-with-the-azure-portal"></a>Azure Portal을 사용하여 새 변수를 만들려면

1. Automation 계정에서 **자산** 타일을 클릭하여 **자산** 블레이드를 엽니다.
1. **변수** 타일을 클릭하여 **변수** 블레이드를 엽니다.
1. 블레이드의 위쪽에서 **변수 추가**를 선택합니다.
1. 양식을 완료하고 **만들기** 를 클릭하여 새 변수를 저장합니다.


### <a name="to-create-a-variable-with-windows-powershell"></a>Windows PowerShell을 사용하여 변수를 만들려면

[New-AzureRmAutomationVariable](https://msdn.microsoft.com/library/mt603613.aspx) cmdlet은 변수를 만들고 해당 초기 값을 설정합니다. [Get-AzureRmAutomationVariable](https://msdn.microsoft.com/library/mt603849.aspx)을 사용하여 값을 검색할 수 있습니다. 값이 단순한 형식이면 동일한 해당 형식이 반환되고, 복잡한 형식이면 **PSCustomObject**가 반환됩니다.

다음 명령 예제에서는 문자열 형식의 변수를 만들고 해당 값을 반환하는 방법을 보여 줍니다.

    New-AzureRmAutomationVariable -ResourceGroupName "ResouceGroup01" 
    –AutomationAccountName "MyAutomationAccount" –Name 'MyStringVariable' `
    –Encrypted $false –Value 'My String'
    $string = (Get-AzureRmAutomationVariable -ResourceGroupName "ResouceGroup01" `
    –AutomationAccountName "MyAutomationAccount" –Name 'MyStringVariable').Value

다음 명령 예제에서는 복잡한 형식의 변수를 만들고 해당 속성을 반환하는 방법을 보여 줍니다. 이 예제에서는 **Get-AzureRmVm**의 가상 컴퓨터 개체가 사용되었습니다.

    $vm = Get-AzureRmVm -ResourceGroupName "ResourceGroup01" –Name "VM01"
    New-AzureRmAutomationVariable –AutomationAccountName "MyAutomationAccount" –Name "MyComplexVariable" –Encrypted $false –Value $vm
    
    $vmValue = (Get-AzureRmAutomationVariable -ResourceGroupName "ResourceGroup01" `
    –AutomationAccountName "MyAutomationAccount" –Name "MyComplexVariable").Value
    $vmName = $vmValue.Name
    $vmIpAddress = $vmValue.IpAddress


## <a name="using-a-variable-in-a-runbook-or-dsc-configuration"></a>runbook 또는 DSC 구성에서 변수 사용

**Set-AutomationVariable** 활동을 사용하여 runbook 및 DSC 구성의 자동화 변수의 값을 설정하고, **Get-AutomationVariable**를 사용하여 검색합니다.  워크플로 활동보다 효율이 떨어지기 때문에 **Set-AzureAutomationVariable** 또는 **Get-AzureAutomationVariable** cmdlet을 runbook 및 DSC 구성에서 사용해서는 안됩니다  또한 **Get-AzureAutomationVariable**을 사용하여 보안 변수의 값을 검색할 수 없습니다.  Runbook 또는 DSC 구성 내에서 변수를 만들 수 있는 유일한 방법은 [New-AzureAutomationVariable](http://msdn.microsoft.com/library/dn913771.aspx) cmdlet을 사용하는 것입니다.


### <a name="textual-runbook-samples"></a>텍스트 Runbook 샘플

#### <a name="setting-and-retrieving-a-simple-value-from-a-variable"></a>변수에서 단순한 값 설정 및 검색

다음 명령 예제에서는 텍스트 Runbook에서 변수를 설정 및 검색하는 방법을 보여 줍니다. 이 예제에서는 *NumberOfIterations* 및 *NumberOfRunnings*라는 정수 형식의 변수와 *SampleMessage*라는 문자열 형식의 변수가 이미 만들어진 것으로 가정합니다.

    $NumberOfIterations = Get-AutomationVariable -Name 'NumberOfIterations'
    $NumberOfRunnings = Get-AutomationVariable -Name 'NumberOfRunnings'
    $SampleMessage = Get-AutomationVariable -Name 'SampleMessage'
    
    Write-Output "Runbook has been run $NumberOfRunnings times."
    
    for ($i = 1; $i -le $NumberOfIterations; $i++) {
       Write-Output "$i`: $SampleMessage"
    }
    Set-AutomationVariable –Name NumberOfRunnings –Value ($NumberOfRunnings += 1)

#### <a name="setting-and-retrieving-a-complex-object-in-a-variable"></a>변수에서 복잡한 개체 설정 및 검색

다음 샘플 코드에서는 텍스트 Runbook에서 복잡한 값으로 변수를 업데이트하는 방법을 보여 줍니다. 이 샘플에서는 **Get-AzureVM** 을 사용하여 Azure 가상 컴퓨터를 검색하고 기존 자동화 변수에 저장합니다.  [변수 형식](#variable-types)에 설명된 대로 이 변수는 PSCustomObject로 저장됩니다.

    $vm = Get-AzureVM -ServiceName "MyVM" -Name "MyVM"
    Set-AutomationVariable -Name "MyComplexVariable" -Value $vm


다음 코드에서는 변수에서 값을 검색하고 이를 사용하여 가상 컴퓨터를 시작합니다.

    $vmObject = Get-AutomationVariable -Name "MyComplexVariable"
    if ($vmObject.PowerState -eq 'Stopped') {
       Start-AzureVM -ServiceName $vmObject.ServiceName -Name $vmObject.Name
    }


#### <a name="setting-and-retrieving-a-collection-in-a-variable"></a>변수에서 컬렉션 설정 및 검색

다음 샘플 코드에서는 텍스트 Runbook에서 복잡한 값 컬렉션과 함께 변수를 사용하는 방법을 보여 줍니다. 이 샘플에서는 **Get-AzureVM** 을 사용하여 여러 Azure 가상 컴퓨터를 검색하고 기존 자동화 변수에 저장합니다.  [변수 형식](#variable-types)에 설명된 대로 이 변수는 PSCustomObject 컬렉션으로 저장됩니다.

    $vms = Get-AzureVM | Where -FilterScript {$_.Name -match "my"}     
    Set-AutomationVariable -Name 'MyComplexVariable' -Value $vms

다음 코드에서는 변수에서 컬렉션을 검색하고 이를 사용하여 각 가상 컴퓨터를 시작합니다.

    $vmValues = Get-AutomationVariable -Name "MyComplexVariable"
    ForEach ($vmValue in $vmValues)
    {
       if ($vmValue.PowerState -eq 'Stopped') {
          Start-AzureVM -ServiceName $vmValue.ServiceName -Name $vmValue.Name
       }
    }

#### <a name="setting-and-retrieving-a-secure-string"></a>보안 문자열 설정 및 검색

보안 문자열 또는 자격 증명을 전달해야 하는 경우 먼저 이 자산을 자격 증명 또는 보안 변수로 만들어야 합니다. 

    $securecredential = get-credential

    New-AzureRmAutomationCredential -ResourceGroupName contoso `
    -AutomationAccountName contosoaccount -Name ContosoCredentialAsset -Value $securecredential

그런 다음 Runbook에 이 자산의 이름을 매개 변수로 전달하고 작업에서 기본 제공을 사용하여 다음 샘플 코드와 같이 스크립트에서 검색하고 사용할 수 있습니다.  

    ExampleScript
    Param

      (
         $ContosoCredentialAssetName
      )

    $ContosoCred = Get-AutomationPSCredential -Name $ContosoCredentialAssetName

다음 예제에서는 Runbook을 호출하는 방법을 보여 줍니다.  

    $RunbookParams = @{"ContosoCredentialAssetName"="ContosoCredentialAsset"}

    Start-AzureRMAutomationRunbook -ResourceGroupName contoso `
    -AutomationAccountName contosoaccount -Name ExampleScript -Parameters $RunbookParams

### <a name="graphical-runbook-samples"></a>그래픽 Runbook 샘플

그래픽 Runbook에서는 그래픽 편집기의 라이브러리 창에서 변수를 마우스 오른쪽 단추로 클릭하고 원하는 활동을 선택하여 **Get-AutomationVariable** 또는 **Set-AutomationVariable**을 추가합니다.

![캔버스에 변수 추가](media/automation-variables/runbook-variable-add-canvas.png)

#### <a name="setting-values-in-a-variable"></a>변수에서 값 설정
다음 그림에서는 그래픽 Runbook에서 단순한 값으로 변수를 업데이트하는 샘플 활동을 보여 줍니다. 이 샘플에서는 **Get-AzureRmVM**을 사용하여 단일 Azure 가상 컴퓨터를 검색하고 컴퓨터 이름을 문자열 형식의 기존 자동화 변수에 저장합니다.  출력에 단일 개체만 필요하므로 [링크가 파이프라인인지 시퀀스인지](automation-graphical-authoring-intro.md#links-and-workflow) 는 중요하지 않습니다.

![단순한 변수 설정](media/automation-variables/runbook-set-simple-variable.png)

## <a name="next-steps"></a>다음 단계

* 그래픽 작성에서 모든 연결 활동에 대해 자세히 알아보려면 [그래픽 작성 링크](automation-graphical-authoring-intro.md#links-and-workflow)
* 그래픽 Runbook을 시작하려면 [내 첫 번째 그래픽 Runbook](automation-first-runbook-graphical.md) 


