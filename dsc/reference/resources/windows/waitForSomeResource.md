---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso de DSC WaitForSome
ms.openlocfilehash: 906375a8fcf9b87d4b7487e63e6fae3f05b86d0d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046997"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="40598-103">Recurso de DSC WaitForSome</span><span class="sxs-lookup"><span data-stu-id="40598-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="40598-104">Aplica-se a: Windows PowerShell 5.0 e posterior</span><span class="sxs-lookup"><span data-stu-id="40598-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="40598-105">O recurso de DSC (Desired State Configuration) **WaitForAny** pode ser usado dentro de um bloco de nó em uma [configuração DSC](../../../configurations/configurations.md) para especificar dependências de configurações em outros nós.</span><span class="sxs-lookup"><span data-stu-id="40598-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="40598-106">O recurso terá êxito se o recurso especificado pela propriedade **ResourceName** estiver no estado desejado em um número mínimo de nós (especificado por **NodeCount**) definidos pela propriedade **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="40598-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="40598-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40598-107">Syntax</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a><span data-ttu-id="40598-108">Propriedades</span><span class="sxs-lookup"><span data-stu-id="40598-108">Properties</span></span>

|  <span data-ttu-id="40598-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="40598-109">Property</span></span>  |  <span data-ttu-id="40598-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="40598-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="40598-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="40598-111">NodeCount</span></span>| <span data-ttu-id="40598-112">O número mínimo de nós que devem estar no estado desejado para que esse recurso tenha êxito.</span><span class="sxs-lookup"><span data-stu-id="40598-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="40598-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="40598-113">NodeName</span></span>| <span data-ttu-id="40598-114">Os nós de destino do recurso do qual dependerá.</span><span class="sxs-lookup"><span data-stu-id="40598-114">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="40598-115">ResourceName</span><span class="sxs-lookup"><span data-stu-id="40598-115">ResourceName</span></span>| <span data-ttu-id="40598-116">O nome do recurso do qual dependerá.</span><span class="sxs-lookup"><span data-stu-id="40598-116">The resource name to depend on.</span></span> <span data-ttu-id="40598-117">Se esse recurso pertence a uma configuração diferente, formate o nome como "[__TipoDoRecurso__]__NomeDoRecurso__::[__NomeDaConfiguração__]::[__NomeDaConfiguração__]"</span><span class="sxs-lookup"><span data-stu-id="40598-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="40598-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="40598-118">RetryIntervalSec</span></span>| <span data-ttu-id="40598-119">O número de segundos antes de tentar novamente.</span><span class="sxs-lookup"><span data-stu-id="40598-119">The number of seconds before retrying.</span></span> <span data-ttu-id="40598-120">O mínimo é 1.</span><span class="sxs-lookup"><span data-stu-id="40598-120">Minimum is 1.</span></span>|
| <span data-ttu-id="40598-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="40598-121">RetryCount</span></span>| <span data-ttu-id="40598-122">O número máximo de tentativas.</span><span class="sxs-lookup"><span data-stu-id="40598-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="40598-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="40598-123">ThrottleLimit</span></span>| <span data-ttu-id="40598-124">O número de máquinas para conectar-se simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="40598-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="40598-125">O padrão é new-cimsession padrão.</span><span class="sxs-lookup"><span data-stu-id="40598-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="40598-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="40598-126">DependsOn</span></span> | <span data-ttu-id="40598-127">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="40598-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="40598-128">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="40598-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="40598-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="40598-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="40598-130">Confira [Usar DSC com credenciais do usuário](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="40598-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="40598-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="40598-131">Example</span></span>

<span data-ttu-id="40598-132">Para obter um exemplo de como usar esse recurso, consulte [Especificando dependências de nó cruzado](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="40598-132">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>