---
title: "Cmdlets de Catálogo"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: carolz
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: ecf70f38bbf48f410eb59b75f86eea767637757a
ms.openlocfilehash: 72df0311a1d187dc6c7c1d29b0a3d2fd243848f0

---
# <a name="catalog-cmdlets"></a>Cmdlets de Catálogo  

Adicionamos dois novos cmdlets no módulo [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) para gerar e validar os arquivos de catálogo do Windows.  

## <a name="new-filecatalog"></a>New-FileCatalog 
--------------------------------

`New-FileCatalog` cria um arquivo de catálogo do Windows para o conjunto de arquivos e pastas. Um arquivo de catálogo contém hashes para todos os arquivos nos caminhos especificados. Os usuários podem distribuir o conjunto de pastas juntamente com a correspondência do arquivo de catálogo que representa essas pastas. Um arquivo de catálogo pode ser usado pelo destinatário de conteúdo para validar se foram feitas alterações nas pastas depois que o catálogo foi criado.    

```PowerShell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Há suporte para a criação do catálogo nas versões 1 e 2. A versão 1 usa o algoritmo de hash SHA1 para criar hashes de arquivo e a versão 2 usa SHA256. Não há suporte para a versão 2 do catálogo no *Windows Server 2008 R2* e no *Windows 7*. É recomendável usar a versão 2 do catálogo, caso esteja usando as plataformas *Windows 8*, *Windows Server 2012* e superiores.  

Para usar este comando em um módulo existente, especifique as variáveis CatalogFilePath e Path para corresponder ao local do manifesto do módulo. O exemplo a seguir, o manifesto de módulo está em C:\Program Files\Windows PowerShell\Modules\Pester. 

![](../images/NewFileCatalog.jpg)

Isso cria o arquivo de catálogo. 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

Para verificar a integridade de um arquivo de catálogo (Pester.cat no exemplo acima), ele deve ser assinado usando o cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx).   


## <a name="test-filecatalog"></a>Test-FileCatalog 
--------------------------------

`Test-FileCatalog` valida o catálogo que representa um conjunto de pastas. 

```PowerShell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Esse cmdlet compara os hashes de todos os arquivos e seus caminhos relativos encontrados no arquivo de catálogo, com os hashes e caminhos dos arquivos salvos em disco. Se detectar qualquer incompatibilidade entre os hashes e caminhos de arquivo, será retornado o status de `ValidationFailed`. Os usuários podem recuperar todas essas informações usando o comutador `Detailed`. O status da assinatura do catálogo é exibido como o campo `Signature`, que é o mesmo que chamar o cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) no arquivo de catálogo. Os usuários também podem ignorar qualquer arquivo durante a validação usando o parâmetro `FilesToSkip`. 



<!--HONumber=Nov16_HO4-->

