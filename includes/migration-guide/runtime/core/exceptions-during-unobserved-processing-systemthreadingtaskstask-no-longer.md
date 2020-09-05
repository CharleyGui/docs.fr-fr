---
ms.openlocfilehash: bae211e5684dc1fbbb1d7e69c928e37c1c532096
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497492"
---
### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a><span data-ttu-id="33c70-101">Les exceptions qui sont levées pendant un traitement non pris en charge dans System.Threading.Tasks.Task ne se propagent plus sur le thread finaliseur</span><span class="sxs-lookup"><span data-stu-id="33c70-101">Exceptions during unobserved processing in System.Threading.Tasks.Task no longer propagate on finalizer thread</span></span>

#### <a name="details"></a><span data-ttu-id="33c70-102">Détails</span><span class="sxs-lookup"><span data-stu-id="33c70-102">Details</span></span>

<span data-ttu-id="33c70-103">Comme la classe <xref:System.Threading.Tasks.Task?displayProperty=fullName> représente une opération asynchrone, elle intercepte toutes les exceptions sans gravité qui se produisent pendant le traitement asynchrone.</span><span class="sxs-lookup"><span data-stu-id="33c70-103">Because the <xref:System.Threading.Tasks.Task?displayProperty=fullName> class represents an asynchronous operation, it catches all non-severe exceptions that occur during asynchronous processing.</span></span> <span data-ttu-id="33c70-104">Dans le .NET Framework 4.5, si une exception n’est pas prise en charge et si votre code n’attend jamais la tâche, l’exception ne se propagera plus sur le thread finaliseur et arrêtera le processus pendant l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="33c70-104">In the .NET Framework 4.5, if an exception is not observed and your code never waits on the task, the exception will no longer propagate on the finalizer thread and crash the process during garbage collection.</span></span> <span data-ttu-id="33c70-105">Cette modification améliore la fiabilité des applications qui utilisent la classe Task pour exécuter un traitement asynchrone non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="33c70-105">This change enhances the reliability of applications that use the Task class to perform unobserved asynchronous processing.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="33c70-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="33c70-106">Suggestion</span></span>

<span data-ttu-id="33c70-107">Si une application dépend d’exceptions asynchrones non prises en charge qui se propagent au thread finaliseur, le comportement précédent peut être restauré en fournissant un gestionnaire approprié pour l’événement <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> ou en définissant un [élément de configuration du runtime](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md).</span><span class="sxs-lookup"><span data-stu-id="33c70-107">If an app depends on unobserved asynchronous exceptions propagating to the finalizer thread, the previous behavior can be restored by providing an appropriate handler for the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event, or by setting a [runtime configuration element](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md).</span></span>

| <span data-ttu-id="33c70-108">Name</span><span class="sxs-lookup"><span data-stu-id="33c70-108">Name</span></span>    | <span data-ttu-id="33c70-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="33c70-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="33c70-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="33c70-110">Scope</span></span>   |<span data-ttu-id="33c70-111">Edge</span><span class="sxs-lookup"><span data-stu-id="33c70-111">Edge</span></span>|
|<span data-ttu-id="33c70-112">Version</span><span class="sxs-lookup"><span data-stu-id="33c70-112">Version</span></span>|<span data-ttu-id="33c70-113">4,5</span><span class="sxs-lookup"><span data-stu-id="33c70-113">4.5</span></span>|
|<span data-ttu-id="33c70-114">Type</span><span class="sxs-lookup"><span data-stu-id="33c70-114">Type</span></span>|<span data-ttu-id="33c70-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="33c70-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="33c70-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="33c70-116">Affected APIs</span></span>

- <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600},System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}},System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Start?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Threading.Tasks.Task.Run(System.Action)`
- `M:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)`
- `M:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})`
- `M:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)`
- ``M:System.Threading.Tasks.Task.Run``1(System.Func{``0})``
- ``M:System.Threading.Tasks.Task.Run``1(System.Func{``0},System.Threading.CancellationToken)``
- ``M:System.Threading.Tasks.Task.Run``1(System.Func{System.Threading.Tasks.Task{``0}})``
- ``M:System.Threading.Tasks.Task.Run``1(System.Func{System.Threading.Tasks.Task{``0}},System.Threading.CancellationToken)``
- `M:System.Threading.Tasks.Task.Start`
- `M:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)`

-->
