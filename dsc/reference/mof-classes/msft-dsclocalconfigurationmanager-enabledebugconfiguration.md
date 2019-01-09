---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047008"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="aaa33-103">Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="aaa33-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="aaa33-104">Habilita a depuração do recurso DSC.</span><span class="sxs-lookup"><span data-stu-id="aaa33-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="aaa33-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aaa33-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="aaa33-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aaa33-106">Parameters</span></span>

<span data-ttu-id="aaa33-107">*BreakAll* \[in\] Define um ponto de interrupção em cada linha do script de recurso.</span><span class="sxs-lookup"><span data-stu-id="aaa33-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="aaa33-108">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="aaa33-108">Return value</span></span>

<span data-ttu-id="aaa33-109">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="aaa33-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="aaa33-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="aaa33-110">Remarks</span></span>

<span data-ttu-id="aaa33-111">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="aaa33-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="aaa33-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aaa33-112">Requirements</span></span>

<span data-ttu-id="aaa33-113">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="aaa33-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="aaa33-114">namespace {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="aaa33-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="aaa33-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aaa33-115">See also</span></span>

[<span data-ttu-id="aaa33-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="aaa33-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)