---
ms.openlocfilehash: 9d0791f00db7d830fc5d327af30218a0bbfcb25f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496956"
---
### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a><span data-ttu-id="1b463-101">Changement de comportement des méthodes Task.WaitAll avec des arguments de délai d’attente</span><span class="sxs-lookup"><span data-stu-id="1b463-101">Change in behavior for Task.WaitAll methods with time-out arguments</span></span>

#### <a name="details"></a><span data-ttu-id="1b463-102">Détails</span><span class="sxs-lookup"><span data-stu-id="1b463-102">Details</span></span>

<span data-ttu-id="1b463-103">Le comportement de <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> est devenu plus cohérent dans .NET Framework 4.5. Dans .NET Framework 4, le comportement de ces méthodes n’était pas cohérent.</span><span class="sxs-lookup"><span data-stu-id="1b463-103"><xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> behavior was made more consistent in .NET Framework 4.5.In the .NET Framework 4, these methods behaved inconsistently.</span></span> <span data-ttu-id="1b463-104">Lorsque le délai d'attente expirait, si une ou plusieurs tâches étaient terminées ou annulées avant l'appel de la méthode, la méthode levait une exception <xref:System.AggregateException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="1b463-104">When the time-out expired, if one or more tasks were completed or canceled before the method call, the method threw an <xref:System.AggregateException?displayProperty=fullName> exception.</span></span> <span data-ttu-id="1b463-105">Lorsque le délai d’attente expirait, si aucune tâche n’était terminée ou annulée avant l’appel de la méthode alors qu’une ou plusieurs tâches adoptaient ces états après l’appel de la méthode, la méthode retournait la valeur false.</span><span class="sxs-lookup"><span data-stu-id="1b463-105">When the time-out expired, if no tasks were completed or canceled before the method call, but one or more tasks entered these states after the method call, the method returned false.</span></span><br/><br/><span data-ttu-id="1b463-106">Dans .NET Framework 4.5, ces surcharges de méthode retournent désormais la valeur false si des tâches sont toujours en cours d’exécution quand l’intervalle de délai d’attente expire, et elles ne lèvent une exception <xref:System.AggregateException?displayProperty=fullName> que si une tâche d’entrée a été annulée (que cette annulation soit intervenue avant ou après l’appel de méthode) et qu’aucune autre tâche n’est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="1b463-106">In the .NET Framework 4.5, these method overloads now return false if any tasks are still running when the time-out interval expired, and they throw an <xref:System.AggregateException?displayProperty=fullName> exception only if an input task was cancelled (regardless of whether it was before or after the method call) and no other tasks are still running.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1b463-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="1b463-107">Suggestion</span></span>

<span data-ttu-id="1b463-108">Si une exception <xref:System.AggregateException?displayProperty=fullName> a été interceptée dans le but de détecter une tâche ayant été annulée avant l’appel de <xref:System.Threading.Tasks.Task.WaitAll%2A>, ce code doit procéder à la même détection par le biais de la propriété <xref:System.Threading.Tasks.Task.IsCanceled%2A> (par exemple, .Any(t =&gt; t.IsCanceled)), puisque .NET Framework 4.6 lève une exception seulement si toutes les tâches attendues sont terminées avant le délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="1b463-108">If an <xref:System.AggregateException?displayProperty=fullName> was being caught as a means of detecting a task that was cancelled prior to the <xref:System.Threading.Tasks.Task.WaitAll%2A> call being invoked, that code should instead do the same detection via the  <xref:System.Threading.Tasks.Task.IsCanceled%2A> property (for example: .Any(t =&gt; t.IsCanceled)) since .NET Framework 4.6 will only throw in that case if all awaited tasks are completed prior to the timeout.</span></span>

| <span data-ttu-id="1b463-109">Name</span><span class="sxs-lookup"><span data-stu-id="1b463-109">Name</span></span>    | <span data-ttu-id="1b463-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="1b463-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1b463-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="1b463-111">Scope</span></span>   |<span data-ttu-id="1b463-112">Secondaire</span><span class="sxs-lookup"><span data-stu-id="1b463-112">Minor</span></span>|
|<span data-ttu-id="1b463-113">Version</span><span class="sxs-lookup"><span data-stu-id="1b463-113">Version</span></span>|<span data-ttu-id="1b463-114">4,5</span><span class="sxs-lookup"><span data-stu-id="1b463-114">4.5</span></span>|
|<span data-ttu-id="1b463-115">Type</span><span class="sxs-lookup"><span data-stu-id="1b463-115">Type</span></span>|<span data-ttu-id="1b463-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="1b463-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1b463-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="1b463-117">Affected APIs</span></span>

- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)`
- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)`
- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)`

-->
