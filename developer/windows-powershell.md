---
title: SDK do Windows PowerShell
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 600d43874d9eda04d556a0ece198026dde9174c3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855352"
---
# <a name="windows-powershell"></a><span data-ttu-id="3a424-102">Usando o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3a424-102">Windows PowerShell</span></span>

<span data-ttu-id="3a424-103">Atualizado: 8 de julho de 2013</span><span class="sxs-lookup"><span data-stu-id="3a424-103">Updated: July 8, 2013</span></span>

<span data-ttu-id="3a424-104">O Windows PowerShell® é um shell de linha de comando e linguagem de scripts com base em tarefa, projetado especialmente para a administração de sistemas.</span><span class="sxs-lookup"><span data-stu-id="3a424-104">Windows PowerShell® is a task-based command-line shell and scripting language designed especially for system administration.</span></span> <span data-ttu-id="3a424-105">Compilado no .NET Framework, Windows PowerShell® ajuda os profissionais de TI e usuários avançados a controlar e automatizar a administração do sistema de operacional do Windows e aplicativos executados no Windows.</span><span class="sxs-lookup"><span data-stu-id="3a424-105">Built on the .NET Framework, Windows PowerShell® helps IT professionals and power users control and automate the administration of the Windows operating system and applications that run on Windows.</span></span>

<span data-ttu-id="3a424-106">Os documentos publicados aqui são escritos principalmente para o cmdlet, o provedor e os desenvolvedores de aplicativos de host que precisam de informações de referência sobre as APIs fornecidas pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3a424-106">The documents published here are written primarily for cmdlet, provider, and host application developers who require reference information about the APIs provided by Windows PowerShell.</span></span>
<span data-ttu-id="3a424-107">No entanto, os administradores do sistema também podem encontrar as informações fornecidas por esses documentos úteis.</span><span class="sxs-lookup"><span data-stu-id="3a424-107">However, system administrators might also find the information provided by these documents useful.</span></span>

<span data-ttu-id="3a424-108">Para as informações básicas necessárias para começar a usar o Windows PowerShell, consulte a introdução ao Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3a424-108">For the basic information needed to start using Windows PowerShell, see Getting Started with Windows PowerShell .</span></span>

## <a name="windows-powershell-documents-on-msdn"></a><span data-ttu-id="3a424-109">Documentos do Windows PowerShell no MSDN</span><span class="sxs-lookup"><span data-stu-id="3a424-109">Windows PowerShell Documents on MSDN</span></span>

- <span data-ttu-id="3a424-110">[Instalar o SDK do Windows PowerShell](https://msdn.microsoft.com/en-us/library/ff458115.aspx) fornece informações sobre como instalar o SDK do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3a424-110">[Installing the Windows PowerShell SDK](https://msdn.microsoft.com/en-us/library/ff458115.aspx) Provides information about how to install the Windows PowerShell SDK.</span></span>

- <span data-ttu-id="3a424-111">[Escrevendo um módulo do Windows PowerShell](./module/writing-a-windows-powershell-module.md) fornece informações para administradores, desenvolvedores de script e os desenvolvedores de cmdlet que precisam empacotar e distribuir suas soluções do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3a424-111">[Writing a Windows PowerShell Module](./module/writing-a-windows-powershell-module.md) Provides information for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell solutions.</span></span>

- <span data-ttu-id="3a424-112">[Escrevendo um Cmdlet do Windows PowerShell](./cmdlet/writing-a-windows-powershell-cmdlet.md) fornece informações para projetar e implementar os cmdlets.</span><span class="sxs-lookup"><span data-stu-id="3a424-112">[Writing a Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) Provides information for designing and implementing cmdlets.</span></span>

- <span data-ttu-id="3a424-113">[Escrevendo um provedor do Windows PowerShell](./provider/writing-a-windows-powershell-provider.md) fornece informações para projetar e implementar provedores do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3a424-113">[Writing a Windows PowerShell Provider](./provider/writing-a-windows-powershell-provider.md) Provides information for designing and implementing Windows PowerShell providers.</span></span> <span data-ttu-id="3a424-114">Ele ajudará você a entender o funcionam de provedores do Windows PowerShell e fornece código de exemplo que você pode usar para iniciar a criação ou escrever seus próprios provedores.</span><span class="sxs-lookup"><span data-stu-id="3a424-114">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

- <span data-ttu-id="3a424-115">[Escrevendo um aplicativo de Host do Windows PowerShell](./hosting/writing-a-windows-powershell-host-application.md) fornece informações que podem ser usadas por gerentes de programa que estão criando aplicativos de host e por desenvolvedores que estiverem implementando-los.</span><span class="sxs-lookup"><span data-stu-id="3a424-115">[Writing a Windows PowerShell Host Application](./hosting/writing-a-windows-powershell-host-application.md) Provides information that can be used by program managers who are designing host applications and by developers who are implementing them.</span></span> <span data-ttu-id="3a424-116">O aplicativo host pode definir o espaço de execução onde os comandos são sessões de execução, abra em um computador local ou remoto e invocar os comandos de forma síncrona ou assíncrona com base nas necessidades do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a424-116">The host application can, define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

- <span data-ttu-id="3a424-117">[Gravação de um arquivo de formatação do PowerShell](./format/writing-a-powershell-formatting-file.md) fornece informações para a criação de arquivos de formatação que controlam o formato de exibição para os objetos que são retornados pelos comandos (cmdlets, funções e scripts).</span><span class="sxs-lookup"><span data-stu-id="3a424-117">[Writing a PowerShell Formatting File](./format/writing-a-powershell-formatting-file.md) Provides information for the authoring of formatting files, which control the display format for the objects that are returned by commands (cmdlets, functions, and scripts).</span></span>

- <span data-ttu-id="3a424-118">[Referência do Windows PowerShell](./windows-powershell-reference.md) fornece conteúdo de referência para as APIs usadas na escrita de cmdlets, provedores e aplicativos de host, bem como outros APIs de suporte.</span><span class="sxs-lookup"><span data-stu-id="3a424-118">[Windows PowerShell Reference](./windows-powershell-reference.md) Provides reference content for the APIs used in writing cmdlets, providers, and host applications, as well as other supporting APIs.</span></span>