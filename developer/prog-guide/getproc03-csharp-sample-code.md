---
title: GetProc03 (C#) exemplos de código | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 328f4eeea27243102679ab5d139181a878165ad6
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429747"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="3e3e4-102">Código de exemplo GetProc03 (C#)</span><span class="sxs-lookup"><span data-stu-id="3e3e4-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="3e3e4-103">O código a seguir mostra a implementação de um `Get-Process` redirecionasse o cmdlet que aceite entrada.</span><span class="sxs-lookup"><span data-stu-id="3e3e4-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="3e3e4-104">Essa implementação define uma `Name` parâmetro que aceita entrada do pipeline, recupera informações de processo do computador local com base em nomes fornecidos e, em seguida, usa o [System.Management.Automation.Cmdlet.Writeobject% 28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) método como o mecanismo de saída para enviar objetos ao pipeline.</span><span class="sxs-lookup"><span data-stu-id="3e3e4-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="3e3e4-105">Você pode baixar o C# arquivo de origem (getprov03.cs) para esse cmdlet Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="3e3e4-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3e3e4-106">Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="3e3e4-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="3e3e4-107">Os arquivos de origem baixado estão disponíveis na  **\<amostras do PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="3e3e4-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3e3e4-108">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="3e3e4-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="3e3e4-109">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="3e3e4-109">See Also</span></span>

[<span data-ttu-id="3e3e4-110">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e3e4-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="3e3e4-111">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e3e4-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)