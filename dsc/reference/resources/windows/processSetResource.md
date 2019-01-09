---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso ProcessSet da DSC
ms.openlocfilehash: 91a2d5b562864addcb8e11062916d291448bbf57
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046994"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="faa4d-103">Recurso WindowsProcess de DSC</span><span class="sxs-lookup"><span data-stu-id="faa4d-103">DSC WindowsProcess Resource</span></span>

<span data-ttu-id="faa4d-104">_Aplica-se a: Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="faa4d-104">_Applies To: Windows PowerShell 5.0_</span></span>

<span data-ttu-id="faa4d-105">O recurso **ProcessSet** na DSC (Configuração de Estado Desejado) do Windows PowerShell fornece um mecanismo para configurar processos em um nó de destino.</span><span class="sxs-lookup"><span data-stu-id="faa4d-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="faa4d-106">Esse recurso é um [recurso composto](../../../resources/authoringResourceComposite.md) que chama o [Recurso do WindowsProcess](windowsProcessResource.md) para cada grupo especificado no parâmetro `GroupName`.</span><span class="sxs-lookup"><span data-stu-id="faa4d-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="faa4d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="faa4d-107">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="faa4d-108">Propriedades</span><span class="sxs-lookup"><span data-stu-id="faa4d-108">Properties</span></span>

| <span data-ttu-id="faa4d-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="faa4d-109">Property</span></span> | <span data-ttu-id="faa4d-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="faa4d-110">Description</span></span> |
| --- | --- |
| <span data-ttu-id="faa4d-111">Argumentos</span><span class="sxs-lookup"><span data-stu-id="faa4d-111">Arguments</span></span>| <span data-ttu-id="faa4d-112">Uma cadeia de caracteres que contém os argumentos a serem passados ao processo no estado em que se encontram.</span><span class="sxs-lookup"><span data-stu-id="faa4d-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="faa4d-113">Se você precisar passar vários argumentos, coloque todos nessa cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="faa4d-113">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="faa4d-114">Caminho</span><span class="sxs-lookup"><span data-stu-id="faa4d-114">Path</span></span>| <span data-ttu-id="faa4d-115">Os caminhos para os executáveis do processo.</span><span class="sxs-lookup"><span data-stu-id="faa4d-115">The paths to the process executables.</span></span> <span data-ttu-id="faa4d-116">Se esses forem os nomes dos arquivos executáveis (caminhos não totalmente qualificados), o recurso DSC pesquisará a variável de ambiente **Path** (`$env:Path`) para localizar os arquivos.</span><span class="sxs-lookup"><span data-stu-id="faa4d-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="faa4d-117">Se os valores dessa propriedade forem caminhos totalmente qualificados, a DSC não usará a variável de ambiente **Path** para localizar os arquivos e gerará um erro se qualquer um dos caminhos não existir.</span><span class="sxs-lookup"><span data-stu-id="faa4d-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="faa4d-118">Caminhos relativos não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="faa4d-118">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="faa4d-119">Credential</span><span class="sxs-lookup"><span data-stu-id="faa4d-119">Credential</span></span>| <span data-ttu-id="faa4d-120">Indica as credenciais para iniciar o processo.</span><span class="sxs-lookup"><span data-stu-id="faa4d-120">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="faa4d-121">Ensure</span><span class="sxs-lookup"><span data-stu-id="faa4d-121">Ensure</span></span>| <span data-ttu-id="faa4d-122">Especifica se os processos existem.</span><span class="sxs-lookup"><span data-stu-id="faa4d-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="faa4d-123">Defina essa propriedade como "Present" para garantir que o processo exista.</span><span class="sxs-lookup"><span data-stu-id="faa4d-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="faa4d-124">Caso contrário, defina-a como "Absent".</span><span class="sxs-lookup"><span data-stu-id="faa4d-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="faa4d-125">O padrão é "Present".</span><span class="sxs-lookup"><span data-stu-id="faa4d-125">The default is "Present".</span></span>|
| <span data-ttu-id="faa4d-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="faa4d-126">StandardErrorPath</span></span>| <span data-ttu-id="faa4d-127">O caminho para o qual os processos gravam o erro padrão.</span><span class="sxs-lookup"><span data-stu-id="faa4d-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="faa4d-128">Qualquer arquivo existente será substituído.</span><span class="sxs-lookup"><span data-stu-id="faa4d-128">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="faa4d-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="faa4d-129">StandardInputPath</span></span>| <span data-ttu-id="faa4d-130">O fluxo do qual o processo recebe entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="faa4d-130">The stream from which the process receives standard input.</span></span>|
| <span data-ttu-id="faa4d-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="faa4d-131">StandardOutputPath</span></span>| <span data-ttu-id="faa4d-132">O caminho do arquivo para o qual os processos gravam a saída padrão.</span><span class="sxs-lookup"><span data-stu-id="faa4d-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="faa4d-133">Qualquer arquivo existente será substituído.</span><span class="sxs-lookup"><span data-stu-id="faa4d-133">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="faa4d-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="faa4d-134">WorkingDirectory</span></span>| <span data-ttu-id="faa4d-135">O local usado como diretório de trabalho atual para os processos.</span><span class="sxs-lookup"><span data-stu-id="faa4d-135">The location used as the current working directory for the processes.</span></span>|
| <span data-ttu-id="faa4d-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="faa4d-136">DependsOn</span></span> | <span data-ttu-id="faa4d-137">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="faa4d-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="faa4d-138">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **_ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="faa4d-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"` .</span></span>|