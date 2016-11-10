---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet, galeria
ms.date: 2016-10-14
contributor: manikb
title: psget_unregister psrepository
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 7d9c24ebb20756a2f7852692532ac6ec7e558ca9

---

# Unregister-PSRepository

Cancela o registro de um repositório.

## Descrição

O cmdlet Unregister-PSRepository cancela o registro de um repositório para o usuário atual.
- O cancelamento de registros e a realização de novos registros do repositório PSGallery são permitidos para cenários empresariais e desconectados.
- Os usuários podem registrar novamente PSGallery apenas executando `Register-PSRepository -Default`
- Como PSGallery é o repositório de publicação padrão nos cmdlets Publish-Module e Publish-Script, um erro será gerado se PSGallery não estiver disponível na lista de repositórios registrados.

## Sintaxe do cmdlet

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## Referência da ajuda online sobre cmdlets

[Unregister-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## Comandos de exemplo

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### O cancelamento de registros e a realização de novos registros do repositório PSGallery são permitidos para cenários empresariais e desconectados.
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```




<!--HONumber=Oct16_HO2-->

