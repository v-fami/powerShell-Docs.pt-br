---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Gerenciamento de serviços
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: 81fd8802215da80ce22fa3fd4750b1df6efe8206
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400524"
---
# <a name="managing-services"></a><span data-ttu-id="767df-103">Gerenciamento de serviços</span><span class="sxs-lookup"><span data-stu-id="767df-103">Managing Services</span></span>

<span data-ttu-id="767df-104">Há oito cmdlets de Serviço principal, projetados para uma ampla variedade de tarefas de serviço.</span><span class="sxs-lookup"><span data-stu-id="767df-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="767df-105">Abordaremos somente a listagem e a alteração do estado de execução para os serviços, porém, é possível obter uma lista de cmdlets Service usando `Get-Help \*-Service`. Você também pode encontrar informações sobre cada cmdlet Service usando `Get-Help <Cmdlet-Name>`, como `Get-Help New-Service`.</span><span class="sxs-lookup"><span data-stu-id="767df-105">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using `Get-Help \*-Service`, and you can find information about each Service cmdlet by using `Get-Help <Cmdlet-Name>`, such as `Get-Help New-Service`.</span></span>

## <a name="getting-services"></a><span data-ttu-id="767df-106">Obtendo serviços</span><span class="sxs-lookup"><span data-stu-id="767df-106">Getting Services</span></span>

<span data-ttu-id="767df-107">É possível obter os serviços em um computador local ou remoto usando o cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="767df-107">You can get the services on a local or remote computer by using the `Get-Service` cmdlet.</span></span> <span data-ttu-id="767df-108">Assim como acontece com `Get-Process`, usar o comando `Get-Service` sem parâmetros retornará todos os serviços.</span><span class="sxs-lookup"><span data-stu-id="767df-108">As with `Get-Process`, using the `Get-Service` command without parameters returns all services.</span></span> <span data-ttu-id="767df-109">Você pode filtrar por nome, até mesmo usando um asterisco como um caractere curinga:</span><span class="sxs-lookup"><span data-stu-id="767df-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="767df-110">Como nem sempre é óbvio qual é o nome real do serviço, você pode achar necessário localizar os serviços por nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="767df-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="767df-111">Você pode fazer isso pelo nome específico, usando caracteres curinga ou usando uma lista de nomes de exibição:</span><span class="sxs-lookup"><span data-stu-id="767df-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

```powershell
PS> Get-Service -DisplayName se*

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center

PS> Get-Service -DisplayName ServiceLayer,Server

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="767df-112">Você pode usar o parâmetro ComputerName do cmdlet Get-Service para obter os serviços em computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="767df-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="767df-113">O parâmetro ComputerName aceita vários valores e caracteres curinga, por isso você pode obter os serviços em vários computadores com um único comando.</span><span class="sxs-lookup"><span data-stu-id="767df-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="767df-114">Esse comando obtém os serviços no computador remoto Server01.</span><span class="sxs-lookup"><span data-stu-id="767df-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="767df-115">Obtendo os serviços necessários e dependentes</span><span class="sxs-lookup"><span data-stu-id="767df-115">Getting Required and Dependent Services</span></span>

<span data-ttu-id="767df-116">O cmdlet Get-Service tem dois parâmetros que são muito úteis na administração de serviços.</span><span class="sxs-lookup"><span data-stu-id="767df-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="767df-117">O parâmetro DependentServices obtém os serviços que dependem do serviço.</span><span class="sxs-lookup"><span data-stu-id="767df-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="767df-118">O parâmetro RequiredServices obtém os serviços dos quais esse serviço depende.</span><span class="sxs-lookup"><span data-stu-id="767df-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="767df-119">Esses parâmetros exibem apenas os valores das propriedades DependentServices e ServicesDependedOn (alias=RequiredServices) do objeto System.ServiceProcess.ServiceController que o Get-Service retorna, porém, eles simplificam comandos e facilitam muito o processo de obter essas informações.</span><span class="sxs-lookup"><span data-stu-id="767df-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="767df-120">O comando a seguir obtém os serviços exigidos pelo serviço LanmanWorkstation.</span><span class="sxs-lookup"><span data-stu-id="767df-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="767df-121">O comando a seguir obtém os serviços que exigem o serviço LanmanWorkstation.</span><span class="sxs-lookup"><span data-stu-id="767df-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="767df-122">É possível obter todos os serviços que têm dependências.</span><span class="sxs-lookup"><span data-stu-id="767df-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="767df-123">O comando a seguir faz exatamente isso e, em seguida, ele usa o cmdlet Format-Table para exibir as propriedades Status, Name, RequiredServices e DependentServices dos serviços no computador.</span><span class="sxs-lookup"><span data-stu-id="767df-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="767df-124">Parar, iniciar, suspender e reiniciar serviços</span><span class="sxs-lookup"><span data-stu-id="767df-124">Stopping, Starting, Suspending, and Restarting Services</span></span>

<span data-ttu-id="767df-125">Todos os cmdlets de serviço têm o mesmo formato geral.</span><span class="sxs-lookup"><span data-stu-id="767df-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="767df-126">Os serviços podem ser especificados pelo nome comum ou pelo nome de exibição, assumindo listas e caracteres curinga como valores.</span><span class="sxs-lookup"><span data-stu-id="767df-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="767df-127">Para interromper o spooler de impressão, use:</span><span class="sxs-lookup"><span data-stu-id="767df-127">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="767df-128">Para iniciar o spooler de impressão depois que ele é interrompido, use:</span><span class="sxs-lookup"><span data-stu-id="767df-128">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="767df-129">Para suspender o spooler de impressão, use:</span><span class="sxs-lookup"><span data-stu-id="767df-129">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="767df-130">O cmdlet `Restart-Service` funciona da mesma maneira que outros cmdlets Service, porém, vamos mostrar alguns exemplos mais complexos para ele.</span><span class="sxs-lookup"><span data-stu-id="767df-130">The `Restart-Service` cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="767df-131">Em seu uso mais simples, você deve especificar o nome do serviço:</span><span class="sxs-lookup"><span data-stu-id="767df-131">In the simplest use, you specify the name of the service:</span></span>

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="767df-132">Você observará que receberá uma mensagem de aviso repetida sobre o Spooler de Impressão iniciado.</span><span class="sxs-lookup"><span data-stu-id="767df-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="767df-133">Quando você executa uma operação de serviço que leva algum tempo, o Windows PowerShell notificará que ainda está tentando executar a tarefa.</span><span class="sxs-lookup"><span data-stu-id="767df-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="767df-134">Se você quiser reiniciar vários serviços, poderá obter uma lista de serviços, filtrá-los e então executar a reinicialização:</span><span class="sxs-lookup"><span data-stu-id="767df-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

```powershell
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service

WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

<span data-ttu-id="767df-135">Esses cmdlets Service não tem um parâmetro ComputerName, mas você pode executá-los em um computador remoto usando o cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="767df-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="767df-136">Esse comando reinicia o serviço de Spooler no computador remoto Server01.</span><span class="sxs-lookup"><span data-stu-id="767df-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="767df-137">Configurando propriedades do serviço</span><span class="sxs-lookup"><span data-stu-id="767df-137">Setting Service Properties</span></span>

<span data-ttu-id="767df-138">O cmdlet `Set-Service` altera as propriedades de um serviço em um computador local ou remoto.</span><span class="sxs-lookup"><span data-stu-id="767df-138">The `Set-Service` cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="767df-139">Como o status do serviço é uma propriedade, você pode usar este cmdlet para iniciar, parar e suspender um serviço.</span><span class="sxs-lookup"><span data-stu-id="767df-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span>
<span data-ttu-id="767df-140">O cmdlet Set-Service também tem um parâmetro StartupType que permite alterar o tipo de inicialização do serviço.</span><span class="sxs-lookup"><span data-stu-id="767df-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="767df-141">Para usar `Set-Service` no Windows Vista e em versões posteriores do Windows, abra o Windows PowerShell com a opção "Executar como administrador".</span><span class="sxs-lookup"><span data-stu-id="767df-141">To use `Set-Service` on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="767df-142">Para obter mais informações, consulte [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3).</span><span class="sxs-lookup"><span data-stu-id="767df-142">For more information, see [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>

## <a name="see-also"></a><span data-ttu-id="767df-143">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="767df-143">See Also</span></span>

- <span data-ttu-id="767df-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span><span class="sxs-lookup"><span data-stu-id="767df-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span></span>
- <span data-ttu-id="767df-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="767df-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>
- <span data-ttu-id="767df-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span><span class="sxs-lookup"><span data-stu-id="767df-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span></span>
- <span data-ttu-id="767df-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span><span class="sxs-lookup"><span data-stu-id="767df-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span></span>