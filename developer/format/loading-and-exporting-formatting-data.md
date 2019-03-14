---
title: Carregar e exportar dados de formatação | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 86a0e8b7e8967280daa57faf5c323efcd3b1368b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794188"
---
# <a name="loading-and-exporting-formatting-data"></a><span data-ttu-id="01d70-102">Carregar e exportar dados de formatação</span><span class="sxs-lookup"><span data-stu-id="01d70-102">Loading and Exporting Formatting Data</span></span>

<span data-ttu-id="01d70-103">Depois de criar seu arquivo de formatação, você precisará atualizar os dados de formato da sessão ao carregar seus arquivos para a sessão atual.</span><span class="sxs-lookup"><span data-stu-id="01d70-103">Once you have created your formatting file, you need to update the format data of the session by loading your files into the current session.</span></span> <span data-ttu-id="01d70-104">(Os arquivos de formatação fornecidos pelo Windows PowerShell são carregados pelo snap-ins que são registrados quando a sessão atual é aberta.) Depois que os dados de formato da sessão atual for atualizados, o Windows PowerShell usa esses dados para exibir os objetos .NET associados com os modos de exibição definidos nos arquivos de formatação carregados.</span><span class="sxs-lookup"><span data-stu-id="01d70-104">(The formatting files provided by Windows PowerShell are loaded by snap-ins that are registered when the current session is opened.) Once the format data of the current session is updated, Windows PowerShell uses that data to display the .NET objects associated with the views defined in the loaded formatting files.</span></span> <span data-ttu-id="01d70-105">Não há nenhum limite para o número de arquivos de formatação que pode ser carregado para a sessão atual.</span><span class="sxs-lookup"><span data-stu-id="01d70-105">There is no limit to the number of formatting files that you can load into the current session.</span></span> <span data-ttu-id="01d70-106">Além de atualizar os dados de formatação, você pode exportar os dados de formatação na sessão atual para um arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="01d70-106">In addition to updating the formatting data, you can export the format data in the current session back to a formatting file.</span></span>

## <a name="loading-format-data"></a><span data-ttu-id="01d70-107">Carregamento de dados de formato</span><span class="sxs-lookup"><span data-stu-id="01d70-107">Loading format data</span></span>

<span data-ttu-id="01d70-108">Arquivos de formatação podem ser carregados para a sessão atual usando os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="01d70-108">Formatting files can be loaded into the current session using the following methods:</span></span>

- <span data-ttu-id="01d70-109">Você pode importar o arquivo de formatação para a sessão atual da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="01d70-109">You can import the formatting file into the current session from the command line.</span></span> <span data-ttu-id="01d70-110">Use o [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet conforme descrito no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="01d70-110">Use the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet as described in the following procedure.</span></span>

- <span data-ttu-id="01d70-111">Você pode criar um manifesto de módulo que faz referência a seu arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="01d70-111">You can create a module manifest that references your formatting file.</span></span> <span data-ttu-id="01d70-112">Módulos permitem que você empacote você formatá-los para distribuição.</span><span class="sxs-lookup"><span data-stu-id="01d70-112">Modules allow you to package you formatting files for distribution.</span></span> <span data-ttu-id="01d70-113">Use o [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) para criar o manifesto e o [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet para carregar o módulo para a sessão atual.</span><span class="sxs-lookup"><span data-stu-id="01d70-113">Use the [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet to create the manifest, and the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet to load the module into the current session.</span></span> <span data-ttu-id="01d70-114">Para obter mais informações sobre os módulos, consulte [escrevendo um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="01d70-114">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- <span data-ttu-id="01d70-115">Você pode criar um snap-in que faz referência a seu arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="01d70-115">You can create a snap-in that references your formatting file.</span></span> <span data-ttu-id="01d70-116">Use o [System.Management.Automation.Pssnapin.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) para fazer referência a arquivos de formatação.</span><span class="sxs-lookup"><span data-stu-id="01d70-116">Use the [System.Management.Automation.Pssnapin.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) to reference your formatting files.</span></span> <span data-ttu-id="01d70-117">É altamente recomendável usar módulos para cmdlets do pacote e qualquer formatação associados e arquivos de tipos para distribuição.</span><span class="sxs-lookup"><span data-stu-id="01d70-117">It is strongly encouraged to use modules to package cmdlets, and any associated formatting and types files for distribution.</span></span> <span data-ttu-id="01d70-118">Para obter mais informações sobre os módulos, consulte [escrevendo um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="01d70-118">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- <span data-ttu-id="01d70-119">Se você estiver chamando comandos por meio de programação, você pode adicionar uma entrada de arquivo de formatação para o estado de sessão inicial do runspace no qual os comandos são executados.</span><span class="sxs-lookup"><span data-stu-id="01d70-119">If you are invoking commands programmatically, you can add a formatting file entry to the initial session state of the runspace where the commands are run.</span></span> <span data-ttu-id="01d70-120">Para obter mais informações sobre o tipo do .NET usado para adicionar o arquivo de formatação, consulte o [System.Management.Automation.Runspaces.Sessionstateformatentry? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) classe.</span><span class="sxs-lookup"><span data-stu-id="01d70-120">For more information about .NET type used to add the formatting file, see the [System.Management.Automation.Runspaces.Sessionstateformatentry?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) class.</span></span>

<span data-ttu-id="01d70-121">Quando um arquivo de formatação é carregado, ele é adicionado a uma lista interna que o Windows PowerShell usa para determinar qual exibição a ser usado ao exibir os objetos na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="01d70-121">When a formatting file is loaded, it is added to an internal list that Windows PowerShell uses to determine which view to use when displaying objects at the command line.</span></span> <span data-ttu-id="01d70-122">Você pode colocar seu arquivo de formatação para o início da lista ou acrescente-ao final da lista.</span><span class="sxs-lookup"><span data-stu-id="01d70-122">You can prepend your formatting file to the beginning of the list, or you can append it to the end of the list.</span></span> <span data-ttu-id="01d70-123">É importante se você estiver carregando um arquivo de formatação que define uma exibição para um objeto que tem uma exibição existente definida, como quando você deseja alterar como um objeto que é retornado por um cmdlet do Windows PowerShell core é saber onde seu arquivo de formatação é adicionado a esta lista  exibido.</span><span class="sxs-lookup"><span data-stu-id="01d70-123">Knowing where your formatting file is added to this list is important if you are loading formatting file that defines a view for an object that has an existing view defined, such as when you want to change how an object that is returned by a Windows PowerShell core cmdlet is displayed.</span></span> <span data-ttu-id="01d70-124">Se você estiver carregando um arquivo de formatação que define o modo de exibição único para um objeto, você pode usar qualquer um dos métodos descritos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="01d70-124">If you are loading a formatting file that defines the only view for an object, you can use any of the methods described previously.</span></span>  <span data-ttu-id="01d70-125">Se você estiver carregando um arquivo de formatação que define outra exibição de um objeto, você deve usar o [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet e preceder seu arquivo para o início da lista.</span><span class="sxs-lookup"><span data-stu-id="01d70-125">If you are loading a formatting file that defines another view for an object, you must use the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet and prepend your file to the beginning of the list.</span></span>

## <a name="storing-your-formatting-file"></a><span data-ttu-id="01d70-126">Armazenar o arquivo de formatação</span><span class="sxs-lookup"><span data-stu-id="01d70-126">Storing Your Formatting File</span></span>

<span data-ttu-id="01d70-127">Não há nenhum requisito para onde os arquivos de formatação são armazenados no disco.</span><span class="sxs-lookup"><span data-stu-id="01d70-127">There is no requirement for where your formatting files are stored on disk.</span></span> <span data-ttu-id="01d70-128">No entanto, é altamente recomendável que você armazene-os na seguinte pasta: `user\documents\windowspowershell\`</span><span class="sxs-lookup"><span data-stu-id="01d70-128">However, it is strongly suggested that you store them in the following folder: `user\documents\windowspowershell\`</span></span>

#### <a name="loading-a-format-file-using-import-formatdata"></a><span data-ttu-id="01d70-129">Carregar um arquivo de formato usando Import-FormatData</span><span class="sxs-lookup"><span data-stu-id="01d70-129">Loading a format file using Import-FormatData</span></span>

1. <span data-ttu-id="01d70-130">Store seu arquivo de formatação para o disco.</span><span class="sxs-lookup"><span data-stu-id="01d70-130">Store your formatting file to disk.</span></span>

2. <span data-ttu-id="01d70-131">Execute o [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet usando um dos comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="01d70-131">Run the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet using one of the following commands.</span></span>

   <span data-ttu-id="01d70-132">Para adicionar sua formatação de arquivo para a frente da lista de usar esse comando.</span><span class="sxs-lookup"><span data-stu-id="01d70-132">To add your formatting file to the front of the list use this command.</span></span> <span data-ttu-id="01d70-133">Use este comando se você estiver alterando como um objeto é exibido.</span><span class="sxs-lookup"><span data-stu-id="01d70-133">Use this command if you are changing how an object is displayed.</span></span>

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   <span data-ttu-id="01d70-134">Para adicionar sua formatação arquivo até o final da lista de usar esse comando.</span><span class="sxs-lookup"><span data-stu-id="01d70-134">To add your formatting file to the end of the list use this command.</span></span>

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   <span data-ttu-id="01d70-135">Depois de adicionar um arquivo usando o [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet, você não pode remover o arquivo da lista durante uma sessão aberta.</span><span class="sxs-lookup"><span data-stu-id="01d70-135">Once you have added a file using the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet, you cannot remove the file from the list while the session is open.</span></span> <span data-ttu-id="01d70-136">Você deve fechar a sessão para remover o arquivo de formatação da lista.</span><span class="sxs-lookup"><span data-stu-id="01d70-136">You must close the session to remove the formatting file from the list.</span></span>

## <a name="exporting-format-data"></a><span data-ttu-id="01d70-137">Exportando dados de formato</span><span class="sxs-lookup"><span data-stu-id="01d70-137">Exporting format data</span></span>

<span data-ttu-id="01d70-138">Insira o corpo da seção aqui.</span><span class="sxs-lookup"><span data-stu-id="01d70-138">Insert section body here.</span></span>