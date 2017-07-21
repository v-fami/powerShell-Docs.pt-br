---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: "Módulo Get PowerShellGet"
ms.openlocfilehash: a5a323b17709e519ec57623a9dd7499e591bbed5
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a name="get-powershellget-module"></a><span data-ttu-id="54155-103">Módulo Get PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="54155-103">Get PowerShellGet Module</span></span>
========================

### <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="54155-104">PowerShellGet é um módulo nativo nas seguintes versões</span><span class="sxs-lookup"><span data-stu-id="54155-104">PowerShellGet is an in-box module in the following releases</span></span>
- <span data-ttu-id="54155-105">[Windows 10](https://www.microsoft.com/en-us/windows/get-windows-10) ou mais recente</span><span class="sxs-lookup"><span data-stu-id="54155-105">[Windows 10](https://www.microsoft.com/en-us/windows/get-windows-10) or newer</span></span>
- <span data-ttu-id="54155-106">[Windows Server 2016](https://technet.microsoft.com/en-us/windows-server-docs/get-started/windows-server-2016) ou mais recente</span><span class="sxs-lookup"><span data-stu-id="54155-106">[Windows Server 2016](https://technet.microsoft.com/en-us/windows-server-docs/get-started/windows-server-2016) or newer</span></span>
- <span data-ttu-id="54155-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) ou mais recente</span><span class="sxs-lookup"><span data-stu-id="54155-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="54155-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="54155-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

### <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="54155-109">Módulo Get PowerShellGet para o PowerShell versões 3.0 e 4.0</span><span class="sxs-lookup"><span data-stu-id="54155-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>
- [<span data-ttu-id="54155-110">MSI do PackageManagement</span><span class="sxs-lookup"><span data-stu-id="54155-110">PackageManagement MSI</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) 

### <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="54155-111">Obter a versão mais recente da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="54155-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="54155-112">Antes de atualizar o PowerShellGet, você sempre deve instalar o provedor do Nuget mais recente.</span><span class="sxs-lookup"><span data-stu-id="54155-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="54155-113">Para fazer isso, execute o seguinte em uma sessão do PowerShell com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="54155-113">To do that, run the following in an elevated PowerShell session.</span></span>
```powershell
Install-PackageProvider Nuget –Force
Exit
```

#### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="54155-114">Para sistemas com o PowerShell 5.0 (ou mais recente), você pode instalar o PowerShellGet mais recente</span><span class="sxs-lookup"><span data-stu-id="54155-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span> 
- <span data-ttu-id="54155-115">Para fazer isso no Windows 10, no Windows Server 2016, em qualquer sistema com o WMF 5.0 ou 5.1 instalado ou em qualquer sistema com o PowerShell 6, execute os seguintes comandos em uma sessão do PowerShell com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="54155-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>
```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- <span data-ttu-id="54155-116">Use Update-Module para obter versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="54155-116">Use Update-Module to get newer versions.</span></span>
```powershell
Update-Module -Name PowerShellGet
Exit
```

#### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a><span data-ttu-id="54155-117">Para sistemas que executam o PowerShell 3 ou o PowerShell 4 que têm o [MSI do PackageManagement](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) instalado</span><span class="sxs-lookup"><span data-stu-id="54155-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span></span>

- <span data-ttu-id="54155-118">Use o cmdlet do PowerShellGet abaixo em uma sessão do PowerShell com privilégios elevados para salvar os módulos em um diretório local</span><span class="sxs-lookup"><span data-stu-id="54155-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- <span data-ttu-id="54155-119">Verifique se os módulos PowerShellGet e PackageManagment não estão carregados em nenhum outro processo.</span><span class="sxs-lookup"><span data-stu-id="54155-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="54155-120">Exclua o conteúdo das pastas `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` e `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="54155-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="54155-121">Reabra o Console do PS com permissões elevadas e execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="54155-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force