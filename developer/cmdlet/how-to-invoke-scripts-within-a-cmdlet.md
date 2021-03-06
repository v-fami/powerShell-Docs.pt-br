---
title: Como invocar Scripts dentro de um Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 4b4d5645785b751eb1390e196f5b9437b4a1e13b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855832"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Como invocar scripts dentro de um cmdlet

Este exemplo mostra como chamar um script que é fornecido para um cmdlet. O script é executado pelo cmdlet e seus resultados são retornados para o cmdlet como uma coleção de [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objetos.

## <a name="to-invoke-a-script-block"></a>Para invocar um bloco de script

1. O comando verifica que um bloco de script foi fornecido para o cmdlet. Se um bloco de script foi fornecido, o comando invoca o bloco de script com os parâmetros necessários.

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. Em seguida, o script itera através da coleção retornada de [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objetos e executar as operações necessárias.

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
