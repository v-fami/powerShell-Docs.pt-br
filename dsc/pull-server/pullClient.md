---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Configurando um cliente de pull de DSC
ms.openlocfilehash: b7cd6dc0087eb8368c5467df4c3c7266ed704451
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400119"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="d5c35-103">Configurando um cliente de pull de DSC</span><span class="sxs-lookup"><span data-stu-id="d5c35-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="d5c35-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d5c35-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d5c35-105">O Servidor de Recepção (Recurso do Windows *Serviço DSC*) é um componente compatível com o Windows Server, no entanto, não há planos de oferecer novos recursos ou funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="d5c35-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="d5c35-106">É recomendável começar a fazer a transição dos clientes gerenciados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started) (inclui recursos além do Servidor de Recepção no Windows Server) ou para uma das soluções da comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="d5c35-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="d5c35-107">Cada nó de destino deve ser instruído a usar o modo de pull e receber a URL ou local do arquivo em que possa contatar o servidor de pull para obter as configurações e recursos e para onde deve enviar os dados de relatório.</span><span class="sxs-lookup"><span data-stu-id="d5c35-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="d5c35-108">Os tópicos a seguir explicam como configurar clientes de pull:</span><span class="sxs-lookup"><span data-stu-id="d5c35-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="d5c35-109">Configurando um cliente de pull usando nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="d5c35-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="d5c35-110">Configurando um cliente de pull usando uma ID de configuração</span><span class="sxs-lookup"><span data-stu-id="d5c35-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="d5c35-111">**Observação**: Estes tópicos se aplicam ao PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="d5c35-111">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="d5c35-112">Para configurar um cliente de pull no PowerShell 4.0, consulte [Configurando um cliente de pull usando uma ID de configuração no PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="d5c35-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>