---
title: Como solicitar confirmações | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 8cfbcacf93733667ffba63a252c86518c0919b57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863402"
---
# <a name="how-to-request-confirmations"></a>Como solicitar confirmações

Este exemplo mostra como chamar o [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos para solicitar confirmações das usuário antes de uma ação é executada.

> [!IMPORTANT]
> Para obter mais informações sobre como o Windows PowerShell lida com essas solicitações, consulte [solicitando confirmação](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Para solicitar uma confirmação

1. Certifique-se de que o `SupportsShouldProcess` parâmetro do Cmdlet atributo for definido como `true`. (Para funções isso é um parâmetro do atributo CmdletBinding.)

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Adicionar um `Force` parâmetro ao cmdlet, para que o usuário pode substituir uma solicitação de confirmação.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Adicionar um `if` instrução que usa o valor de retorno de [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método para determinar se o [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método é chamado.

4. Adicione um segundo `if` instrução que usa o valor de retorno de [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método e o valor da `Force` parâmetro para determinar se a operação deve ser executada.

## <a name="example"></a>Exemplo

No exemplo de código a seguir, o [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos são chamados de dentro do substituição do [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método. No entanto, você também pode chamar esses métodos de outra métodos de processamento de entrada.

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
