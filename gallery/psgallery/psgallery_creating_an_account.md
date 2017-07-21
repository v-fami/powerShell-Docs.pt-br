---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: Criando uma conta da Galeria do PowerShell
ms.openlocfilehash: e21575320f220c1ba7ecd9bd464a814b3ebf49d9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
## <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="d0a9f-103">Criando uma conta da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0a9f-103">Creating a PowerShell Gallery Account</span></span>

<span data-ttu-id="d0a9f-104">Uma conta da Galeria do PowerShell deve ser estabelecida antes de publicar algo na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0a9f-104">A PowerShell Gallery account must be established before publishing anything to the PowerShell Gallery.</span></span> <span data-ttu-id="d0a9f-105">As contas da Galeria do PowerShell devem ser vinculadas a uma conta do Azure Active Directory habilitada por email ou a uma conta de email da Microsoft (com um domínio do outlook.com, do hotmail.com, etc.)</span><span class="sxs-lookup"><span data-stu-id="d0a9f-105">The PowerShell Gallery accounts must be linked to an Azure Active Directory email-enabled account, or a Microsoft email account (with a domain of outlook.com, hotmail.com, etc.)</span></span>

<span data-ttu-id="d0a9f-106">Para criar uma conta de galeria do PowerShell, acesse https://PowerShellGallery.com e clique em "Registrar" (veja a imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="d0a9f-106">To create a PowerShell Gallery account, go to https://PowerShellGallery.com and click on "Register" (see the image below).</span></span> 

![Registrar nova conta](./images/CreatingAccount-Register.png)

<span data-ttu-id="d0a9f-108">Na próxima página, para usar uma conta do Azure Active Directory, selecione "Conta de trabalho ou de escola" e faça logon com sua conta.</span><span class="sxs-lookup"><span data-stu-id="d0a9f-108">In the next page, to use an Azure Active Directory account, select "Work or School Account", and log in with your account.</span></span> <span data-ttu-id="d0a9f-109">Para usar uma conta da Microsoft, como uma no domínio Hotmail.com ou Outlook.com, escolha "Conta pessoal" e faça logon.</span><span class="sxs-lookup"><span data-stu-id="d0a9f-109">To use a Microsoft account - such as one in a Hotmail.com or Outlook.com domain - choose "Personal Account", and log in.</span></span> 

<span data-ttu-id="d0a9f-110">Depois de fazer logon, será solicitado que você crie um nome de usuário para a Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0a9f-110">Once you have logged in, you will be prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="d0a9f-111">Examine os termos de uso e a política de privacidade vinculados, insira um nome de usuário e, em seguida, clique em Registrar.</span><span class="sxs-lookup"><span data-stu-id="d0a9f-111">Review the Terms of Use and Privacy Policy that are linked in, enter a username, and then click Register.</span></span>

<span data-ttu-id="d0a9f-112">Observação: este nome de conta não poderá ser alterado após a criação.</span><span class="sxs-lookup"><span data-stu-id="d0a9f-112">Note: This account name cannot be changed once it is created.</span></span>  
<span data-ttu-id="d0a9f-113">Consulte [Gerenciando proprietários do item](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners) para obter detalhes adicionais relacionados a isso.</span><span class="sxs-lookup"><span data-stu-id="d0a9f-113">See [Managing Item Owners](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners) for additional details related to this.</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="d0a9f-114">Práticas recomendadas para contas da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0a9f-114">Recommended Practices for PowerShell Gallery Accounts</span></span>

<span data-ttu-id="d0a9f-115">É importante que a conta de email usada com sua conta da Galeria do PowerShell seja monitorada ativamente.</span><span class="sxs-lookup"><span data-stu-id="d0a9f-115">It is important that the email account used with your PowerShell Gallery account be actively monitored.</span></span>
<span data-ttu-id="d0a9f-116">Toda a comunicação com os proprietários de itens da Galeria do PowerShell é feita por email usando o endereço associado à sua conta da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0a9f-116">All communiction with owners of PowerShell Gallery items is through the email using the address associated with your PowerShell Gallery account.</span></span>
<span data-ttu-id="d0a9f-117">Quando não for possível entrar em contato com um proprietário de item, a equipe de operações poderá precisar excluir o item em algumas circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="d0a9f-117">If we are unable to contact an item owner, the Operations team may be required to delete an item under some circumstances.</span></span>

<span data-ttu-id="d0a9f-118">As organizações que publicam na Galeria do PowerShell geralmente criam uma conta exclusiva para essa finalidade no Outlook.com ou em outro domínio de conta da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d0a9f-118">Organizations that publish to the PowerShell Gallery often create a unique account for that purpose in Outlook.com, or another Microsoft account domain.</span></span>
<span data-ttu-id="d0a9f-119">Em muitos casos essa conta não é monitorada regularmente.</span><span class="sxs-lookup"><span data-stu-id="d0a9f-119">In many cases that account is not regularly monitored.</span></span> <span data-ttu-id="d0a9f-120">Nesse caso, uma prática recomendada é usar o encaminhamento do Outlook para enviar email para outra conta, normalmente uma conta da organização, que será monitorada pelos proprietários do item.</span><span class="sxs-lookup"><span data-stu-id="d0a9f-120">A best practice in that case is to use Outlook Forwarding to send email to another account, typically one within the organization, that will be monitored by the item owner(s).</span></span>

<span data-ttu-id="d0a9f-121">Se houver vários proprietários associados a um item, todas as comunicações que vierem da Galeria do PowerShell irão para todos os proprietários.</span><span class="sxs-lookup"><span data-stu-id="d0a9f-121">If there are multiple owners associated with an item, all communications that come from the PowerShell Gallery will go to all owners.</span></span>
<span data-ttu-id="d0a9f-122">Consulte [Gerenciando proprietários do item](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners) para obter detalhes adicionais de como adicionar proprietários para um item.</span><span class="sxs-lookup"><span data-stu-id="d0a9f-122">See [Managing Item Owners](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners) for additional details on adding owners to an item.</span></span> 
