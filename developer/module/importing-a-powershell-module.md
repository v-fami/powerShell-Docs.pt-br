---
title: Importando um módulo do PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: bb5d036e5658c365a4fafa2cac05c0bba9f87019
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854052"
---
# <a name="importing-a-powershell-module"></a><span data-ttu-id="f716f-102">Importar um módulo do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f716f-102">Importing a PowerShell Module</span></span>

<span data-ttu-id="f716f-103">Uma vez o tiver instalado um módulo em um sistema, você provavelmente desejará importar o módulo.</span><span class="sxs-lookup"><span data-stu-id="f716f-103">Once your have installed a module on a system, you will likely want to import the module.</span></span> <span data-ttu-id="f716f-104">Importação é o processo que carrega o módulo na memória ativa, para que um usuário pode acessar esse módulo em sua sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f716f-104">Importing is the process that loads the module into active memory, so that a user can access that module in their PowerShell session.</span></span> <span data-ttu-id="f716f-105">No PowerShell 2.0, você pode importar um módulo do PowerShell instalados recentemente com uma chamada para [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f716f-105">In PowerShell 2.0, you can import a newly-installed PowerShell module with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span> <span data-ttu-id="f716f-106">No PowerShell 3.0, o PowerShell é capaz de importar implicitamente um módulo quando uma das funções ou cmdlets no módulo é chamada por um usuário.</span><span class="sxs-lookup"><span data-stu-id="f716f-106">In PowerShell 3.0, PowerShell is able to implicitly import a module when one of the functions or cmdlets in the module is called by a user.</span></span> <span data-ttu-id="f716f-107">Observe que ambas as versões pressupõem que você instale o módulo em um local onde o PowerShell é capaz de localizá-lo; Para obter mais informações, consulte [instalando um módulo do PowerShell](./installing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="f716f-107">Note that both versions assume that you install your module in a location where PowerShell is able to find it; for more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md).</span></span> <span data-ttu-id="f716f-108">Você pode usar um manifesto de módulo para restringir quais partes do seu módulo são exportados, e você pode usar parâmetros da `Import-Module` chamada para restringir quais partes são importados.</span><span class="sxs-lookup"><span data-stu-id="f716f-108">You can use a module manifest to restrict what parts of your module are exported, and you can use parameters of the `Import-Module` call to restrict what parts are imported.</span></span>

## <a name="importing-a-snap-in-powershell-10"></a><span data-ttu-id="f716f-109">Importando um Snap-In (PowerShell 1.0)</span><span class="sxs-lookup"><span data-stu-id="f716f-109">Importing a Snap-In (PowerShell 1.0)</span></span>

<span data-ttu-id="f716f-110">Módulos não existia no PowerShell 1.0: em vez disso, você precisava registrar e usar o snap-ins. No entanto, não se recomenda que você use essa tecnologia neste ponto, como módulos são geralmente mais fáceis de instalar e importar.</span><span class="sxs-lookup"><span data-stu-id="f716f-110">Modules did not exist in PowerShell 1.0: instead, you had to register and use snap-ins. However, it is not recommended that you use this technology at this point, as modules are generally easier to install and import.</span></span> <span data-ttu-id="f716f-111">Para obter mais informações, consulte [como criar um Snap-in do PowerShell do Windows](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="f716f-111">For more information, see [How to Create a Windows PowerShell Snap-in](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).</span></span>

## <a name="importing-a-module-with-import-module-powershell-20"></a><span data-ttu-id="f716f-112">Importando um módulo com Import-Module (PowerShell 2.0)</span><span class="sxs-lookup"><span data-stu-id="f716f-112">Importing a Module with Import-Module (PowerShell 2.0)</span></span>

<span data-ttu-id="f716f-113">PowerShell 2.0 usa o adequadamente nomeadas [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) para importar módulos.</span><span class="sxs-lookup"><span data-stu-id="f716f-113">PowerShell 2.0 uses the appropriately-named [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet to import modules.</span></span> <span data-ttu-id="f716f-114">Quando esse cmdlet é executado, Windows PowerShell procura o módulo especificado nos diretórios especificados no `PSModulePath` variável.</span><span class="sxs-lookup"><span data-stu-id="f716f-114">When this cmdlet is run, Windows PowerShell searches for the specified module within the directories specified in the `PSModulePath` variable.</span></span> <span data-ttu-id="f716f-115">Quando o diretório especificado for encontrado, o Windows PowerShell procura por arquivos na seguinte ordem: arquivos de manifesto de módulo (. psd1), arquivos de módulo (. psm1), arquivos de módulo binário (. dll) de script.</span><span class="sxs-lookup"><span data-stu-id="f716f-115">When the specified directory is found, Windows PowerShell searches for files in the following order: module manifest files (.psd1), script module files (.psm1), binary module files (.dll).</span></span> <span data-ttu-id="f716f-116">Para obter mais informações sobre como adicionar diretórios à pesquisa, consulte [modificando o caminho de instalação do PSModulePath](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="f716f-116">For more information about adding directories to the search, see [Modifying the PSModulePath Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span> <span data-ttu-id="f716f-117">O código a seguir descreve como importar um módulo:</span><span class="sxs-lookup"><span data-stu-id="f716f-117">The following code describes how to import a module:</span></span>

```powershell
Import-Module myModule
```

<span data-ttu-id="f716f-118">Supondo que myModule estava localizado no `PSModulePath`, PowerShell carregaria myModule na memória ativa.</span><span class="sxs-lookup"><span data-stu-id="f716f-118">Assuming that myModule was located in the `PSModulePath`, PowerShell would load myModule into active memory.</span></span> <span data-ttu-id="f716f-119">Se myModule não foi localizado em um `PSModulePath` caminho, você pode ainda informar explicitamente ao PowerShell onde encontrá-lo:</span><span class="sxs-lookup"><span data-stu-id="f716f-119">If myModule was not located on a `PSModulePath` path, you could still explicitly tell PowerShell where to find it:</span></span>

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

<span data-ttu-id="f716f-120">Você também pode usar o parâmetro - verbose para identificar o que está sendo exportado fora do módulo e o que está sendo importado na memória ativa.</span><span class="sxs-lookup"><span data-stu-id="f716f-120">You can also use the -verbose parameter to identify what is being exported out of the module, and what is being imported into active memory.</span></span> <span data-ttu-id="f716f-121">Importações e exportações restringem o que é exposto ao usuário: a diferença é que está controlando a visibilidade.</span><span class="sxs-lookup"><span data-stu-id="f716f-121">Both exports and imports restrict what is exposed to the user: the difference is who is controlling the visibility.</span></span> <span data-ttu-id="f716f-122">Essencialmente, exportações são controladas pelo código dentro do módulo.</span><span class="sxs-lookup"><span data-stu-id="f716f-122">Essentially, exports are controlled by code within the module.</span></span> <span data-ttu-id="f716f-123">Em contraste, as importações são controladas pelo `Import-Module` chamar.</span><span class="sxs-lookup"><span data-stu-id="f716f-123">In contrast, imports are controlled by the `Import-Module` call.</span></span> <span data-ttu-id="f716f-124">Para obter mais informações, consulte **restringindo os membros que são importados**, abaixo.</span><span class="sxs-lookup"><span data-stu-id="f716f-124">For more information, see **Restricting Members That Are Imported**, below.</span></span>

## <a name="implicitly-importing-a-module-powershell-30"></a><span data-ttu-id="f716f-125">Implicitamente, importando um módulo (PowerShell 3.0)</span><span class="sxs-lookup"><span data-stu-id="f716f-125">Implicitly Importing a Module (PowerShell 3.0)</span></span>

<span data-ttu-id="f716f-126">Módulos a partir do Windows PowerShell 3.0, são importados automaticamente quando qualquer cmdlet ou função no módulo é usada em um comando.</span><span class="sxs-lookup"><span data-stu-id="f716f-126">Beginning in Windows PowerShell 3.0, modules are imported automatically when any cmdlet or function in the module is used in a command.</span></span> <span data-ttu-id="f716f-127">Esse recurso funciona em qualquer módulo em um diretório incluído no valor da **PSModulePath** variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="f716f-127">This feature works on any module in a directory that this included in the value of the **PSModulePath** environment variable.</span></span> <span data-ttu-id="f716f-128">Se você não salvar seu módulo em um caminho válido no entanto, você ainda pode carregá-los usando o explícito [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) opção, descrita acima.</span><span class="sxs-lookup"><span data-stu-id="f716f-128">If you do not save your module on a valid path however, you can still load them using the explicit [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) option, described above.</span></span>

<span data-ttu-id="f716f-129">As seguintes ações disparam a importação automática de um módulo, também conhecido como "módulo de carregamento automático."</span><span class="sxs-lookup"><span data-stu-id="f716f-129">The following actions trigger automatic importing of a module, also known as "module auto-loading."</span></span>

- <span data-ttu-id="f716f-130">Usando um cmdlet em um comando.</span><span class="sxs-lookup"><span data-stu-id="f716f-130">Using a cmdlet in a command.</span></span> <span data-ttu-id="f716f-131">Por exemplo, digitar `Get-ExecutionPolicy` importa o módulo Microsoft.PowerShell.Security que contém o `Get-ExecutionPolicy` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f716f-131">For example, typing `Get-ExecutionPolicy` imports the Microsoft.PowerShell.Security module that contains the `Get-ExecutionPolicy` cmdlet.</span></span>

- <span data-ttu-id="f716f-132">Usando o [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) para obter o comando.</span><span class="sxs-lookup"><span data-stu-id="f716f-132">Using the [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet to get the command.</span></span>  <span data-ttu-id="f716f-133">Por exemplo, digitar `Get-Command Get-JobTrigger` importa os **PSScheduledJob** módulo que contém o `Get-JobTrigger` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f716f-133">For example, typing `Get-Command Get-JobTrigger` imports the **PSScheduledJob** module that contains the `Get-JobTrigger` cmdlet.</span></span> <span data-ttu-id="f716f-134">Um `Get-Command` é considerado como descoberta de comando que inclui caracteres curinga e não aciona a importação de um módulo.</span><span class="sxs-lookup"><span data-stu-id="f716f-134">A `Get-Command` command that includes wildcard characters is considered to be discovery and does not trigger importing of a module.</span></span>

- <span data-ttu-id="f716f-135">Usando o [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet para obter ajuda para um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f716f-135">Using the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet to get help for a cmdlet.</span></span> <span data-ttu-id="f716f-136">Por exemplo, digitar `Get-Help Get-WinEvent` importa o módulo Microsoft.PowerShell.Diagnostics que contém o `Get-WinEvent` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f716f-136">For example, typing `Get-Help Get-WinEvent` imports the Microsoft.PowerShell.Diagnostics module that contains the `Get-WinEvent` cmdlet.</span></span>

<span data-ttu-id="f716f-137">Para dar suporte a importação automática de módulos, o `Get-Command` cmdlet obtém todos os cmdlets e funções em todos os módulos instalados, mesmo se o módulo não será importado para a sessão.</span><span class="sxs-lookup"><span data-stu-id="f716f-137">To support automatic importing of modules, the `Get-Command` cmdlet gets all cmdlets and functions in all installed modules, even if the module is not imported into the session.</span></span> <span data-ttu-id="f716f-138">Para obter mais informações, consulte o tópico de ajuda para o [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f716f-138">For more information, see the help topic for the [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet.</span></span>

## <a name="the-importing-process"></a><span data-ttu-id="f716f-139">O processo de importação</span><span class="sxs-lookup"><span data-stu-id="f716f-139">The Importing Process</span></span>

<span data-ttu-id="f716f-140">Quando um módulo é importado, um estado de sessão nova é criado para o módulo e um [psmoduleinfo](/dotnet/api/System.Management.Automation.PSModuleInfo) objeto é criado na memória.</span><span class="sxs-lookup"><span data-stu-id="f716f-140">When a module is imported, a new session state is created for the module, and a [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) object is created in memory.</span></span> <span data-ttu-id="f716f-141">Um estado de sessão é criado para cada módulo que é importado (Isso inclui o módulo raiz e todos os módulos aninhados).</span><span class="sxs-lookup"><span data-stu-id="f716f-141">A session-state is created for each module that is imported (this includes the root module and any nested modules).</span></span> <span data-ttu-id="f716f-142">Os membros que são exportados do módulo raiz, incluindo todos os membros que foram exportados para o módulo raiz por todos os módulos aninhados, em seguida, são importados para o estado de sessão do chamador.</span><span class="sxs-lookup"><span data-stu-id="f716f-142">The members that are exported from the root module, including any members that were exported to the root module by any nested modules, are then imported into the caller's session state.</span></span>

<span data-ttu-id="f716f-143">Os metadados dos membros que são exportados a partir de um módulo tem uma propriedade de ModuleName.</span><span class="sxs-lookup"><span data-stu-id="f716f-143">The metadata of members that are exported from a module have a ModuleName property.</span></span> <span data-ttu-id="f716f-144">Essa propriedade é preenchida com o nome do módulo que exportou-los.</span><span class="sxs-lookup"><span data-stu-id="f716f-144">This property is populated with the name of the module that exported them.</span></span>

> [!WARNING]
> <span data-ttu-id="f716f-145">Se o nome de um membro exportado utiliza um verbo não aprovado ou se o nome do membro usa caracteres restritos, um aviso é exibido quando o [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet é executado.</span><span class="sxs-lookup"><span data-stu-id="f716f-145">If the name of an exported member uses an unapproved verb or if the name of the member uses restricted characters, a warning is displayed when the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet is run.</span></span>

<span data-ttu-id="f716f-146">Por padrão, o [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet não retorna nenhum objeto no pipeline.</span><span class="sxs-lookup"><span data-stu-id="f716f-146">By default, the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet does not return any objects to the pipeline.</span></span> <span data-ttu-id="f716f-147">No entanto, o cmdlet oferece suporte a um `PassThru` parâmetro que pode ser usado para retornar um [psmoduleinfo](/dotnet/api/System.Management.Automation.PSModuleInfo) objeto para cada módulo que é importado.</span><span class="sxs-lookup"><span data-stu-id="f716f-147">However, the cmdlet supports a `PassThru` parameter that can be used to return a [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) object for each module that is imported.</span></span> <span data-ttu-id="f716f-148">Para enviar a saída para o host, os usuários devem executar o [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f716f-148">To send output to the host, users should run the [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet.</span></span>

## <a name="restricting--the-members-that-are-imported"></a><span data-ttu-id="f716f-149">Restringindo os membros que são importados</span><span class="sxs-lookup"><span data-stu-id="f716f-149">Restricting  the Members That Are Imported</span></span>

<span data-ttu-id="f716f-150">Quando um módulo é importado usando o [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet, por padrão, todos os módulos exportados, os membros são importados para a sessão, incluindo todos os comandos exportados para o módulo por um módulo aninhado.</span><span class="sxs-lookup"><span data-stu-id="f716f-150">When a module is imported by using the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet, by default, all exported module members are imported into the session, including any commands exported to the module by a nested module.</span></span> <span data-ttu-id="f716f-151">Por padrão, variáveis e aliases não são exportadas.</span><span class="sxs-lookup"><span data-stu-id="f716f-151">By default, variables and aliases are not exported.</span></span> <span data-ttu-id="f716f-152">Para restringir os membros que são exportados, use uma [manifesto de módulo](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="f716f-152">To restrict the members that are exported, use a [module manifest](./how-to-write-a-powershell-module-manifest.md).</span></span> <span data-ttu-id="f716f-153">Para restringir os membros que são importados, use os seguintes parâmetros da `Import-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f716f-153">To restrict the members that are imported, use the following parameters of the `Import-Module` cmdlet.</span></span>

- <span data-ttu-id="f716f-154">`Function`: Esse parâmetro restringe as funções que são exportadas.</span><span class="sxs-lookup"><span data-stu-id="f716f-154">`Function`: This parameter restricts the functions that are exported.</span></span> <span data-ttu-id="f716f-155">(Se você estiver usando um manifesto de módulo, consulte a chave FunctionsToExport.)</span><span class="sxs-lookup"><span data-stu-id="f716f-155">(If you are using a module manifest, see the FunctionsToExport key.)</span></span>

- <span data-ttu-id="f716f-156">`Cmdlet`: Esse parâmetro restringe os cmdlets que são exportados (se você estiver usando uma consulte de manifesto, módulo a chave CmdletsToExport.)</span><span class="sxs-lookup"><span data-stu-id="f716f-156">`Cmdlet`: This parameter restricts the cmdlets that are exported (If you are using a module manifest, see the CmdletsToExport key.)</span></span>

- <span data-ttu-id="f716f-157">`Variable`: Esse parâmetro restringe as variáveis que são exportadas (se você estiver usando uma consulte de manifesto, módulo a chave VariablesToExport.)</span><span class="sxs-lookup"><span data-stu-id="f716f-157">`Variable`: This parameter restricts the variables that are exported (If you are using a module manifest, see the VariablesToExport key.)</span></span>

- <span data-ttu-id="f716f-158">`Alias`: Esse parâmetro restringe os aliases exportados (se você estiver usando uma consulte de manifesto, módulo a chave AliasesToExport.)</span><span class="sxs-lookup"><span data-stu-id="f716f-158">`Alias`: This parameter restricts the aliases that are exported (If you are using a module manifest, see the AliasesToExport key.)</span></span>

## <a name="see-also"></a><span data-ttu-id="f716f-159">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f716f-159">See Also</span></span>

[<span data-ttu-id="f716f-160">Escrevendo um módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f716f-160">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)