---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Fornecendo comentários por meio de mídia social ou do recurso Comentários
ms.openlocfilehash: a8e6097de4a565b504189b0b0488c45b6d78a8b6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="providing-feedback-via-social-media-or-comments"></a>Fornecendo comentários por meio de mídia social ou do recurso Comentários

A Galeria do Powershell dá suporte a duas abordagens para que os usuários forneçam comentários públicos sobre um item:

- Use os links na borda esquerda para “compartilhar” um item nos sites de mídia social Facebook, LinkedIn ou Twitter;
- Use o recurso Comentário para enviar comentários sobre um item e para permitir que os autores detectem comentários sobre os itens que eles publicaram.

## <a name="social-media-feedback"></a>Comentários em mídia social

No lado esquerdo da página de cada item da Galeria do PowerShell, há links para o LinkedIn, o Facebook e o Twitter.
Clicar nesses links abrirá o site de mídia social e permitirá o compartilhamento rápido de um link para o item.

Os usuários devem fazer logon no site que escolheram para compartilhar o item da Galeria do PowerShell.

Recomenda-se fazer isso quando o usuário acha que um item é algo que ele recomendaria a outros usuários.
A Galeria do PowerShell verificará cada site de mídia social buscando "compartilhamentos" do item e exibirá quantas vezes o item foi compartilhado em cada um dos sites de mídia social.
Como isso mostra apenas o número de vezes que algo foi compartilhado, isso será interpretado como: se os outros usuários “gostaram” do item.


## <a name="comments"></a>Comentários

A Galeria do PowerShell usa o serviço LiveFyre para permitir que os usuários comentem sobre os itens.
Os usuários que têm recomendações ou comentários podem usar esse recurso para fornecer comentários que ficam visível para qualquer pessoa que visitar a página do item.
Os proprietários do item podem Seguir este comentário e ser notificados quando alguém postar um comentário.

O sistema de Comentário é baseado no LiveFyre, que é um serviço separado que não é gerenciado pela Microsoft e requer o uso de logon exclusivo.
Na primeira vez que desejar deixar um comentário ou Seguir os comentários em um de seus itens, será solicitado que você crie uma conta do LiveFyre.

Se você tiver criado uma conta do LiveFyre e feito logon, você poderá criar um comentário que forneça comentários sobre o item e, em seguida, clicar em "Postar comentário..." O comentário não ficará visível imediatamente.
Os comentários para itens da galeria são moderados pelos administradores da Galeria do PowerShell e todas as postagens são examinadas pelos moderadores antes de serem publicadas e ficarem visíveis para outras pessoas.
Nosso objetivo ao moderar os comentários é garantir que eles se alinhem a um comportamento público consistente com os [Termos de uso](https://www.powershellgallery.com/policies/Terms) da Galeria do PowerShell.

Os proprietários de item são incentivados a seguir os Comentários que são postados no LiveFyre.
É necessária uma conta do LiveFyre e é recomendável usar o mesmo endereço de email usado para publicar o item no LiveFyre.
Para Seguir comentários, faça logon no LiveFyre e navegue para qualquer item em que você esteja listado como Proprietário.
Abaixo da caixa Comentário na parte inferior de cada item, será exibido "+Seguir".
Depois de clicar nisso, o LiveFyre enviará um email para o endereço de email registrado sempre que novos comentários forem feitos no item.