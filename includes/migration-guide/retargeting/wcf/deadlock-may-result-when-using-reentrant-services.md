---
ms.openlocfilehash: f61cf21f9f30662cc8e383bb3aeb5c642f1665b8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497072"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a><span data-ttu-id="04020-101">Un blocage peut se produire lors de l’utilisation de services réentrants</span><span class="sxs-lookup"><span data-stu-id="04020-101">Deadlock may result when using Reentrant services</span></span>

#### <a name="details"></a><span data-ttu-id="04020-102">Détails</span><span class="sxs-lookup"><span data-stu-id="04020-102">Details</span></span>

<span data-ttu-id="04020-103">Un blocage peut survenir dans un service réentrant, ce qui limite les instances du service à un thread d’exécution à la fois.</span><span class="sxs-lookup"><span data-stu-id="04020-103">A deadlock may result in a Reentrant service, which restricts instances of the service to one thread of execution at a time.</span></span> <span data-ttu-id="04020-104">Les services susceptibles de rencontrer ce problème ont le <xref:System.ServiceModel.ServiceBehaviorAttribute> suivant dans leur code :</span><span class="sxs-lookup"><span data-stu-id="04020-104">Services prone to encounter this problem will have the following <xref:System.ServiceModel.ServiceBehaviorAttribute> in their code:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

#### <a name="suggestion"></a><span data-ttu-id="04020-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="04020-105">Suggestion</span></span>

<span data-ttu-id="04020-106">Pour résoudre ce problème, vous pouvez effectuer l’opération suivante :</span><span class="sxs-lookup"><span data-stu-id="04020-106">To address this issue, you can do the following:</span></span>

- <span data-ttu-id="04020-107">Définissez le mode d’accès concurrentiel du service sur <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> ou <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="04020-107">Set the service's concurrency mode to <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> or <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType>.</span></span> <span data-ttu-id="04020-108">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="04020-108">For example:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

- <span data-ttu-id="04020-109">Installez la dernière mise à jour sur .NET Framework 4.6.2 ou effectuez une mise à niveau vers une version ultérieure du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="04020-109">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="04020-110">Cela désactive le flux de l’<xref:System.Threading.ExecutionContext> dans <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04020-110">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>.</span></span> <span data-ttu-id="04020-111">Ce comportement est configurable. Cela équivaut à ajouter le paramètre d’application suivant à votre fichier de configuration :</span><span class="sxs-lookup"><span data-stu-id="04020-111">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span>

```xml
<appSettings>
  <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
</appSettings>
```

<span data-ttu-id="04020-112">La valeur de `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` ne doit jamais être définie sur `false` pour les services réentrants.</span><span class="sxs-lookup"><span data-stu-id="04020-112">The value of `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` should never be set to `false` for Reentrant services.</span></span>

| <span data-ttu-id="04020-113">Name</span><span class="sxs-lookup"><span data-stu-id="04020-113">Name</span></span>    | <span data-ttu-id="04020-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="04020-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="04020-115">Étendue</span><span class="sxs-lookup"><span data-stu-id="04020-115">Scope</span></span>   | <span data-ttu-id="04020-116">Secondaire</span><span class="sxs-lookup"><span data-stu-id="04020-116">Minor</span></span>       |
| <span data-ttu-id="04020-117">Version</span><span class="sxs-lookup"><span data-stu-id="04020-117">Version</span></span> | <span data-ttu-id="04020-118">4.6.2</span><span class="sxs-lookup"><span data-stu-id="04020-118">4.6.2</span></span>       |
| <span data-ttu-id="04020-119">Type</span><span class="sxs-lookup"><span data-stu-id="04020-119">Type</span></span>    | <span data-ttu-id="04020-120">Reciblage</span><span class="sxs-lookup"><span data-stu-id="04020-120">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="04020-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="04020-121">Affected APIs</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType>
