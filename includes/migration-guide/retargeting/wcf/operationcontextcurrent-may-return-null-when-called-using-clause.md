---
ms.openlocfilehash: d25c14f93da5fe8acf06269554fed30ddc6bc95d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614507"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a><span data-ttu-id="ae9d1-101">OperationContext.Current peut retourner null en cas d’appel dans une clause using</span><span class="sxs-lookup"><span data-stu-id="ae9d1-101">OperationContext.Current may return null when called in a using clause</span></span>

#### <a name="details"></a><span data-ttu-id="ae9d1-102">Détails</span><span class="sxs-lookup"><span data-stu-id="ae9d1-102">Details</span></span>

<span data-ttu-id="ae9d1-103"><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> peut retourner `null` et il peut en résulter un <xref:System.NullReferenceException> si toutes les conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="ae9d1-103"><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> may return `null` and a <xref:System.NullReferenceException> may result if all of the following conditions are true:</span></span>

- <span data-ttu-id="ae9d1-104">Vous récupérez la valeur de la propriété <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> dans une méthode qui retourne un <xref:System.Threading.Tasks.Task> ou un <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="ae9d1-104">You retrieve the value of the <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> property in a method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>
- <span data-ttu-id="ae9d1-105">Vous instanciez l’objet <xref:System.ServiceModel.OperationContextScope> dans une clause `using`.</span><span class="sxs-lookup"><span data-stu-id="ae9d1-105">You instantiate the <xref:System.ServiceModel.OperationContextScope> object in a `using` clause.</span></span>
- <span data-ttu-id="ae9d1-106">Vous récupérez la valeur de la propriété <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> dans l’`using statement`.</span><span class="sxs-lookup"><span data-stu-id="ae9d1-106">You retrieve the value of the <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> property within the `using statement`.</span></span> <span data-ttu-id="ae9d1-107">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ae9d1-107">For example:</span></span>

```csharp
using (new OperationContextScope(OperationContext.Current))
{
    // OperationContext.Current is null.
    OperationContext context = OperationContext.Current;

    // ...
}
```

#### <a name="suggestion"></a><span data-ttu-id="ae9d1-108">Suggestion</span><span class="sxs-lookup"><span data-stu-id="ae9d1-108">Suggestion</span></span>

<span data-ttu-id="ae9d1-109">Pour résoudre ce problème, vous pouvez effectuer l’opération suivante :</span><span class="sxs-lookup"><span data-stu-id="ae9d1-109">To address this issue, you can do the following:</span></span>

- <span data-ttu-id="ae9d1-110">Modifiez votre code comme suit pour instancier un nouvel objet non- `null` <xref:System.ServiceModel.OperationContext.Current%2A> :</span><span class="sxs-lookup"><span data-stu-id="ae9d1-110">Modify your code as follows to instantiate a new non- `null` <xref:System.ServiceModel.OperationContext.Current%2A> object:</span></span>

    ```csharp
    OperationContext ocx = OperationContext.Current;
    using (new OperationContextScope(OperationContext.Current))
    {
        OperationContext.Current = new OperationContext(ocx.Channel);

        // ...
    }
    ```

- <span data-ttu-id="ae9d1-111">Installez la dernière mise à jour sur .NET Framework 4.6.2 ou effectuez une mise à niveau vers une version ultérieure du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ae9d1-111">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="ae9d1-112">Cela désactive le flux de <xref:System.Threading.ExecutionContext> dans <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> et restaure le comportement des applications WCF dans .NET Framework 4.6.1 et les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="ae9d1-112">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> and restores the behavior of WCF applications in the .NET Framework 4.6.1 and earlier versions.</span></span> <span data-ttu-id="ae9d1-113">Ce comportement est configurable. Cela équivaut à ajouter le paramètre d’application suivant à votre fichier de configuration :</span><span class="sxs-lookup"><span data-stu-id="ae9d1-113">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span>

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
    </appSettings>
    ```

    <span data-ttu-id="ae9d1-114">Si ce changement n’est pas souhaitable et que votre application dépend du flux de contexte d’exécution entre les contextes d’opération, vous pouvez activer son flux comme suit :</span><span class="sxs-lookup"><span data-stu-id="ae9d1-114">If this change is undesirable and your application depends on execution context flowing between operation contexts, you can enable its flow as follows:</span></span>

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="false" />
    </appSettings>
    ```

| <span data-ttu-id="ae9d1-115">Nom</span><span class="sxs-lookup"><span data-stu-id="ae9d1-115">Name</span></span>    | <span data-ttu-id="ae9d1-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="ae9d1-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ae9d1-117">Étendue</span><span class="sxs-lookup"><span data-stu-id="ae9d1-117">Scope</span></span>   | <span data-ttu-id="ae9d1-118">Edge</span><span class="sxs-lookup"><span data-stu-id="ae9d1-118">Edge</span></span>        |
| <span data-ttu-id="ae9d1-119">Version</span><span class="sxs-lookup"><span data-stu-id="ae9d1-119">Version</span></span> | <span data-ttu-id="ae9d1-120">4.6.2</span><span class="sxs-lookup"><span data-stu-id="ae9d1-120">4.6.2</span></span>       |
| <span data-ttu-id="ae9d1-121">Type</span><span class="sxs-lookup"><span data-stu-id="ae9d1-121">Type</span></span>    | <span data-ttu-id="ae9d1-122">Reciblage</span><span class="sxs-lookup"><span data-stu-id="ae9d1-122">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ae9d1-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="ae9d1-123">Affected APIs</span></span>

- <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>
