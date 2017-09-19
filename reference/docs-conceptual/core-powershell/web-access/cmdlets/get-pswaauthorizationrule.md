---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet
ms.date: 2016-12-12
title: get pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: eb9f42ab4d9cec111e03a096b2f00740e97ee1b7
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2017
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="25e20-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="25e20-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="25e20-104">SINOPSE</span><span class="sxs-lookup"><span data-stu-id="25e20-104">SYNOPSIS</span></span>

<span data-ttu-id="25e20-105">Retorna um conjunto de regras de autorização do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="25e20-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="25e20-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25e20-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="25e20-107">ID</span><span class="sxs-lookup"><span data-stu-id="25e20-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="25e20-108">Nome</span><span class="sxs-lookup"><span data-stu-id="25e20-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="25e20-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="25e20-109">DESCRIPTION</span></span>

<span data-ttu-id="25e20-110">O cmdlet **Get-PswaAuthorizationRule** retorna um conjunto de regras de autorização do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="25e20-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="25e20-111">Se nem o parâmetro **Id** nem o parâmetro **RuleName** for especificado, esse cmdlet listará todas as regras.</span><span class="sxs-lookup"><span data-stu-id="25e20-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="25e20-112">O parâmetro **Id** pode ser usado para filtrar os resultados.</span><span class="sxs-lookup"><span data-stu-id="25e20-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="25e20-113">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="25e20-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="25e20-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="25e20-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="25e20-115">Especifica as IDs (identificadores) das regras que este cmdlet deve obter.</span><span class="sxs-lookup"><span data-stu-id="25e20-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="25e20-116">Se nenhuma ID for especificada, esse cmdlet retornará todas as regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="25e20-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="25e20-117">Aliases</span><span class="sxs-lookup"><span data-stu-id="25e20-117">Aliases</span></span>                              | <span data-ttu-id="25e20-118">none</span><span class="sxs-lookup"><span data-stu-id="25e20-118">none</span></span>                                 |
| <span data-ttu-id="25e20-119">Necessário?</span><span class="sxs-lookup"><span data-stu-id="25e20-119">Required?</span></span>                            | <span data-ttu-id="25e20-120">false</span><span class="sxs-lookup"><span data-stu-id="25e20-120">false</span></span>                                |
| <span data-ttu-id="25e20-121">Posição?</span><span class="sxs-lookup"><span data-stu-id="25e20-121">Position?</span></span>                            | <span data-ttu-id="25e20-122">2</span><span class="sxs-lookup"><span data-stu-id="25e20-122">2</span></span>                                    |
| <span data-ttu-id="25e20-123">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="25e20-123">Default Value</span></span>                        | <span data-ttu-id="25e20-124">none</span><span class="sxs-lookup"><span data-stu-id="25e20-124">none</span></span>                                 |
| <span data-ttu-id="25e20-125">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="25e20-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="25e20-126">Verdadeiro (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="25e20-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="25e20-127">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="25e20-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="25e20-128">false</span><span class="sxs-lookup"><span data-stu-id="25e20-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="25e20-129">-RuleName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="25e20-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="25e20-130">Especifica os nomes das regras de autorização a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="25e20-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="25e20-131">Este parâmetro retorna todas as regras que corresponderem exatamente aos nomes de regra das cadeias de caracteres nesta matriz.</span><span class="sxs-lookup"><span data-stu-id="25e20-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||  
|-|-|
| <span data-ttu-id="25e20-132">Aliases</span><span class="sxs-lookup"><span data-stu-id="25e20-132">Aliases</span></span>                              | <span data-ttu-id="25e20-133">none</span><span class="sxs-lookup"><span data-stu-id="25e20-133">none</span></span>                                 |
| <span data-ttu-id="25e20-134">Necessário?</span><span class="sxs-lookup"><span data-stu-id="25e20-134">Required?</span></span>                            | <span data-ttu-id="25e20-135">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="25e20-135">true</span></span>                                 |
| <span data-ttu-id="25e20-136">Posição?</span><span class="sxs-lookup"><span data-stu-id="25e20-136">Position?</span></span>                            | <span data-ttu-id="25e20-137">2</span><span class="sxs-lookup"><span data-stu-id="25e20-137">2</span></span>                                    |
| <span data-ttu-id="25e20-138">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="25e20-138">Default Value</span></span>                        | <span data-ttu-id="25e20-139">none</span><span class="sxs-lookup"><span data-stu-id="25e20-139">none</span></span>                                 |
| <span data-ttu-id="25e20-140">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="25e20-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="25e20-141">Verdadeiro (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="25e20-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="25e20-142">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="25e20-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="25e20-143">false</span><span class="sxs-lookup"><span data-stu-id="25e20-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="25e20-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="25e20-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="25e20-145">Esse cmdlet oferece suporte aos parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="25e20-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="25e20-146">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="25e20-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="25e20-147">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="25e20-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="25e20-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="25e20-148">int\[\]</span></span>

<span data-ttu-id="25e20-149">Este cmdlet aceita uma matriz de inteiros ou uma matriz de valores de cadeia de caracteres como entrada.</span><span class="sxs-lookup"><span data-stu-id="25e20-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="25e20-150">String\[\]</span><span class="sxs-lookup"><span data-stu-id="25e20-150">String\[\]</span></span>

<span data-ttu-id="25e20-151">Este cmdlet aceita uma matriz de inteiros ou uma matriz de valores de cadeia de caracteres como entrada.</span><span class="sxs-lookup"><span data-stu-id="25e20-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="25e20-152">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="25e20-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="25e20-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="25e20-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="25e20-154">Este cmdlet gera um objeto PswaAuthorizationRule como saída.</span><span class="sxs-lookup"><span data-stu-id="25e20-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="25e20-155">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="25e20-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="25e20-156">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="25e20-156">EXAMPLE 1</span></span>

<span data-ttu-id="25e20-157">Este exemplo obtém todas as regras.</span><span class="sxs-lookup"><span data-stu-id="25e20-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="25e20-158">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="25e20-158">EXAMPLE 2</span></span>

<span data-ttu-id="25e20-159">Este exemplo obtém uma regra com uma ID igual a *2*.</span><span class="sxs-lookup"><span data-stu-id="25e20-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="25e20-160">EXEMPLO 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="25e20-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="25e20-161">Este exemplo ilustra como o cmdlet aceita um valor do pipeline.</span><span class="sxs-lookup"><span data-stu-id="25e20-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="25e20-162">Uma ID de regra e um nome de regra são passados nesse cmdlet.</span><span class="sxs-lookup"><span data-stu-id="25e20-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="25e20-163">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="25e20-163">Related topics</span></span>

- [<span data-ttu-id="25e20-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="25e20-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="25e20-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="25e20-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="25e20-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="25e20-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="25e20-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="25e20-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)