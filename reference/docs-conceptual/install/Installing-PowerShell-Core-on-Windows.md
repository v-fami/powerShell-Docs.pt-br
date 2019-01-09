---
title: Instalar o PowerShell Core no Windows
description: Informações sobre a instalação do PowerShell Core no Windows
ms.date: 08/06/2018
ms.openlocfilehash: 7c109c7e1848af2349092c1e70fe4a7a25be54b8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400288"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="20614-103">Instalar o PowerShell Core no Windows</span><span class="sxs-lookup"><span data-stu-id="20614-103">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="20614-104">MSI</span><span class="sxs-lookup"><span data-stu-id="20614-104">MSI</span></span>

<span data-ttu-id="20614-105">Para instalar o PowerShell em um cliente do Windows ou Windows Server (funciona no Windows 7 SP1, no Server 2008 R2 e posterior), baixe o pacote MSI da nossa página [versões][] do GitHub.</span><span class="sxs-lookup"><span data-stu-id="20614-105">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="20614-106">O arquivo MSI tem esta aparência – `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span><span class="sxs-lookup"><span data-stu-id="20614-106">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span></span>

<span data-ttu-id="20614-107">Após o download, clique duas vezes no instalador e siga os prompts.</span><span class="sxs-lookup"><span data-stu-id="20614-107">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="20614-108">Há um atalho colocado no Menu Iniciar após a instalação.</span><span class="sxs-lookup"><span data-stu-id="20614-108">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="20614-109">Por padrão, o pacote é instalado em `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="20614-109">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="20614-110">Você pode iniciar o PowerShell por meio do Menu Iniciar ou `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="20614-110">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="20614-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="20614-111">Prerequisites</span></span>

<span data-ttu-id="20614-112">Para habilitar a comunicação remota do PowerShell pelo WSMan, os pré-requisitos a seguir precisam ser atendidos:</span><span class="sxs-lookup"><span data-stu-id="20614-112">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="20614-113">Instale o [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) em versões do Windows antes do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="20614-113">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="20614-114">Ele está disponível por meio do Windows Update ou de download direto.</span><span class="sxs-lookup"><span data-stu-id="20614-114">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="20614-115">Sistemas operacionais com suporte totalmente corrigidos (incluindo pacotes opcionais) já o terão instalado.</span><span class="sxs-lookup"><span data-stu-id="20614-115">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="20614-116">Instale o Windows Management Framework (WMF) 4.0 ou mais recente no Windows 7 e no Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="20614-116">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="20614-117">ZIP</span><span class="sxs-lookup"><span data-stu-id="20614-117">ZIP</span></span>

<span data-ttu-id="20614-118">Arquivos binários de ZIP do PowerShell são fornecidos para habilitar cenários de implantação avançada.</span><span class="sxs-lookup"><span data-stu-id="20614-118">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="20614-119">Observe que, ao usar o arquivo ZIP, você não obtém a verificação de pré-requisitos, como ocorre no pacote MSI.</span><span class="sxs-lookup"><span data-stu-id="20614-119">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="20614-120">Para que a comunicação remota pelo WSMan funcione corretamente em versões do Windows antes do Windows 10, é necessário garantir que os [pré-requisitos](#prerequisites) sejam atendidos.</span><span class="sxs-lookup"><span data-stu-id="20614-120">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="20614-121">Implantar no Windows IoT</span><span class="sxs-lookup"><span data-stu-id="20614-121">Deploying on Windows IoT</span></span>

<span data-ttu-id="20614-122">O Windows IoT já é fornecido com o Windows PowerShell, o qual usaremos para implantar o PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="20614-122">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="20614-123">Crie `PSSession` no dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="20614-123">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="20614-124">Copie o pacote ZIP no dispositivo</span><span class="sxs-lookup"><span data-stu-id="20614-124">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.1.0-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="20614-125">Conecte-se ao dispositivo e expanda o arquivo</span><span class="sxs-lookup"><span data-stu-id="20614-125">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.1.0-win-arm32.zip
   ```

4. <span data-ttu-id="20614-126">Configuração de comunicação remota no PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="20614-126">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-6.1.0-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="20614-127">Conecte-se ao ponto de extremidade do PowerShell Core 6 no dispositivo</span><span class="sxs-lookup"><span data-stu-id="20614-127">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.1.0
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="20614-128">Implantação no Nano Server</span><span class="sxs-lookup"><span data-stu-id="20614-128">Deploying on Nano Server</span></span>

<span data-ttu-id="20614-129">Estas instruções pressupõem que uma versão do PowerShell já está em execução na imagem do Nano Server e que ela foi gerada pelo [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="20614-129">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="20614-130">Nano Server é um sistema operacional "sem periféricos".</span><span class="sxs-lookup"><span data-stu-id="20614-130">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="20614-131">Os principais binários podem ser implantados usando dois métodos diferentes.</span><span class="sxs-lookup"><span data-stu-id="20614-131">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="20614-132">Offline – monte o VHD do Nano Server e descompacte o conteúdo do arquivo zip para o local escolhido na imagem montada.</span><span class="sxs-lookup"><span data-stu-id="20614-132">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="20614-133">Online – transfira o arquivo zip em uma sessão do PowerShell e descompacte-o em seu local escolhido.</span><span class="sxs-lookup"><span data-stu-id="20614-133">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="20614-134">Em ambos os casos, você precisa do pacote da versão ZIP do Windows 10 x64 e precisa executar os comandos em uma instância "Administrador" do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20614-134">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="20614-135">Implantação offline do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="20614-135">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="20614-136">Use o utilitário zip favorito para descompactar o pacote para um diretório na imagem montada do Nano Server.</span><span class="sxs-lookup"><span data-stu-id="20614-136">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="20614-137">Desmonte a imagem e inicialize-a.</span><span class="sxs-lookup"><span data-stu-id="20614-137">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="20614-138">Conecte-se à instância da caixa de entrada do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20614-138">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="20614-139">Siga as instruções para criar um ponto de extremidade de comunicação remota usando a ["outra técnica de instância"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="20614-139">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="20614-140">Implantação online do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="20614-140">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="20614-141">As etapas a seguir servem de orientação para a implantação do PowerShell Core em uma instância em execução do Nano Server, e a configuração do seu ponto de extremidade de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="20614-141">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="20614-142">Conectar-se à instância da caixa de entrada do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="20614-142">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="20614-143">Copiar o arquivo para a instância do Nano Server</span><span class="sxs-lookup"><span data-stu-id="20614-143">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="20614-144">Entrar na sessão</span><span class="sxs-lookup"><span data-stu-id="20614-144">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="20614-145">Extrair o arquivo ZIP</span><span class="sxs-lookup"><span data-stu-id="20614-145">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="20614-146">Se você deseja comunicação remota baseada no WSMan, siga as instruções para criar um ponto de extremidade de comunicação remota usando a ["outra técnica de instância"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="20614-146">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="20614-147">Instruções para criar um ponto de extremidade de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="20614-147">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="20614-148">O PowerShell Core dá suporte ao protocolo PSRP (comunicação remota do PowerShell) por WSMan e SSH.</span><span class="sxs-lookup"><span data-stu-id="20614-148">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="20614-149">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="20614-149">For more information, see:</span></span>

- <span data-ttu-id="20614-150">[Comunicação remota do SSH no PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="20614-150">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="20614-151">[Comunicação remota do WSMan no PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="20614-151">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="20614-152">Instruções de instalação do artefato</span><span class="sxs-lookup"><span data-stu-id="20614-152">Artifact Installation Instructions</span></span>

<span data-ttu-id="20614-153">Publicamos um arquivo com os bits de CoreCLR em cada build de CI com [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="20614-153">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="20614-154">Para instalar o PowerShell Core do artefato CoreCLR:</span><span class="sxs-lookup"><span data-stu-id="20614-154">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="20614-155">Baixe o pacote ZIP da guia **artefatos** do build particular.</span><span class="sxs-lookup"><span data-stu-id="20614-155">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="20614-156">Desbloqueie o arquivo ZIP: clique com o botão direito em Explorador de Arquivos -> Propriedades -> marque a caixa "Desbloquear" -> aplicar</span><span class="sxs-lookup"><span data-stu-id="20614-156">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="20614-157">Extraia o arquivo zip para o diretório `bin`</span><span class="sxs-lookup"><span data-stu-id="20614-157">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[versões]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell