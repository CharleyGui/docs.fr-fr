---
ms.openlocfilehash: d25c14f93da5fe8acf06269554fed30ddc6bc95d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614507"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a>OperationContext.Current peut retourner null en cas d’appel dans une clause using

#### <a name="details"></a>Détails

<xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> peut retourner `null` et il peut en résulter un <xref:System.NullReferenceException> si toutes les conditions suivantes sont remplies :

- Vous récupérez la valeur de la propriété <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> dans une méthode qui retourne un <xref:System.Threading.Tasks.Task> ou un <xref:System.Threading.Tasks.Task%601>.
- Vous instanciez l’objet <xref:System.ServiceModel.OperationContextScope> dans une clause `using`.
- Vous récupérez la valeur de la propriété <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> dans l’`using statement`. Par exemple :

```csharp
using (new OperationContextScope(OperationContext.Current))
{
    // OperationContext.Current is null.
    OperationContext context = OperationContext.Current;

    // ...
}
```

#### <a name="suggestion"></a>Suggestion

Pour résoudre ce problème, vous pouvez effectuer l’opération suivante :

- Modifiez votre code comme suit pour instancier un nouvel objet non- `null` <xref:System.ServiceModel.OperationContext.Current%2A> :

    ```csharp
    OperationContext ocx = OperationContext.Current;
    using (new OperationContextScope(OperationContext.Current))
    {
        OperationContext.Current = new OperationContext(ocx.Channel);

        // ...
    }
    ```

- Installez la dernière mise à jour sur .NET Framework 4.6.2 ou effectuez une mise à niveau vers une version ultérieure du .NET Framework. Cela désactive le flux de <xref:System.Threading.ExecutionContext> dans <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> et restaure le comportement des applications WCF dans .NET Framework 4.6.1 et les versions antérieures. Ce comportement est configurable. Cela équivaut à ajouter le paramètre d’application suivant à votre fichier de configuration :

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
    </appSettings>
    ```

    Si ce changement n’est pas souhaitable et que votre application dépend du flux de contexte d’exécution entre les contextes d’opération, vous pouvez activer son flux comme suit :

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="false" />
    </appSettings>
    ```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.6.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>
