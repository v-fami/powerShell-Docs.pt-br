---
title: Escrevendo um Snap-in do PowerShell do Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.assetid: 875024f4-e02b-4416-80b9-af5e5b50aad6
caps.latest.revision: 7
ms.openlocfilehash: d4f57c062fee09e85c290445082be745ab229985
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795021"
---
# <a name="writing-a-windows-powershell-snap-in"></a>Escrever um snap-in do Windows PowerShell

Este exemplo mostra como escrever um snap-in do Windows PowerShell que pode ser usado para registrar todos os cmdlets e provedores do Windows PowerShell em um assembly.

Com esse tipo de snap-in, você não selecionar quais cmdlets e provedores que você deseja registrar. Para gravar um snap-in que permite que você selecione o que é registrado, consulte [escrevendo um Snap-in PowerShell Windows personalizado](./writing-a-custom-windows-powershell-snap-in.md).

### <a name="writing-a-windows-powershell-snap-in"></a>Escrever um snap-in do Windows PowerShell

1. Adicione o atributo RunInstallerAttribute.

2. Crie uma classe pública que deriva de [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) classe.

    Neste exemplo, o nome de classe é "GetProcPSSnapIn01".

3. Adicione uma propriedade pública para o nome do snap-in (obrigatório). Ao nomear o snap-ins, não use nenhum dos seguintes caracteres: #. , ( ) { } [ ] & - /\ $ ; : " ' \< > ; ? @ ` *

    Neste exemplo, o nome do snap-in é "GetProcPSSnapIn01".

4. Adicione uma propriedade pública para o fornecedor do snap-in (obrigatório).

    Neste exemplo, o fornecedor é "Microsoft".

5. Adicione uma propriedade pública para o recurso de fornecedor do snap-in (opcional).

    Neste exemplo, o recurso de fornecedor é "Microsoft GetProcPSSnapIn01".

6. Adicione uma propriedade pública para a descrição do snap-in (obrigatório).

    Neste exemplo, a descrição é "Isso é um snap-in do Windows PowerShell que registra o cmdlet get-proc".

7. Adicione uma propriedade pública para o recurso de descrição do snap-in (opcional).

    Neste exemplo, o recurso de fornecedor é "GetProcPSSnapIn01, isso é um snap-in do Windows PowerShell que registra o cmdlet get-proc".

## <a name="example"></a>Exemplo

Este exemplo mostra como escrever um snap-in do Windows PowerShell que pode ser usado para registrar o cmdlet Get-Proc no shell do Windows PowerShell. Lembre-se de que neste exemplo, o assembly completo conteria apenas a GetProcPSSnapIn01 snap-in de classe e a classe do cmdlet Get-Proc.

```csharp
[RunInstaller(true)]
public class GetProcPSSnapIn01 : PSSnapIn
{
  /// <summary>
  /// Create an instance of the GetProcPSSnapIn01 class.
  /// </summary>
  public GetProcPSSnapIn01()
         : base()
  {
  }

  /// <summary>
  /// Specify the name of the PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "GetProcPSSnapIn01";
    }
  }

  /// <summary>
  /// Specify the vendor for the PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,VendorName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
      return "GetProcPSSnapIn01,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
      return "GetProcPSSnapIn01,This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }
}
```

## <a name="see-also"></a>Consulte Também

[Como registrar Cmdlets, provedores e aplicativos de Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Shell do Windows PowerShell do SDK](../windows-powershell-reference.md)
