---
ms.openlocfilehash: 9d0791f00db7d830fc5d327af30218a0bbfcb25f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496956"
---
### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>Changement de comportement des méthodes Task.WaitAll avec des arguments de délai d’attente

#### <a name="details"></a>Détails

Le comportement de <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> est devenu plus cohérent dans .NET Framework 4.5. Dans .NET Framework 4, le comportement de ces méthodes n’était pas cohérent. Lorsque le délai d'attente expirait, si une ou plusieurs tâches étaient terminées ou annulées avant l'appel de la méthode, la méthode levait une exception <xref:System.AggregateException?displayProperty=fullName>. Lorsque le délai d’attente expirait, si aucune tâche n’était terminée ou annulée avant l’appel de la méthode alors qu’une ou plusieurs tâches adoptaient ces états après l’appel de la méthode, la méthode retournait la valeur false.<br/><br/>Dans .NET Framework 4.5, ces surcharges de méthode retournent désormais la valeur false si des tâches sont toujours en cours d’exécution quand l’intervalle de délai d’attente expire, et elles ne lèvent une exception <xref:System.AggregateException?displayProperty=fullName> que si une tâche d’entrée a été annulée (que cette annulation soit intervenue avant ou après l’appel de méthode) et qu’aucune autre tâche n’est en cours d’exécution.

#### <a name="suggestion"></a>Suggestion

Si une exception <xref:System.AggregateException?displayProperty=fullName> a été interceptée dans le but de détecter une tâche ayant été annulée avant l’appel de <xref:System.Threading.Tasks.Task.WaitAll%2A>, ce code doit procéder à la même détection par le biais de la propriété <xref:System.Threading.Tasks.Task.IsCanceled%2A> (par exemple, .Any(t =&gt; t.IsCanceled)), puisque .NET Framework 4.6 lève une exception seulement si toutes les tâches attendues sont terminées avant le délai d’attente.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)`
- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)`
- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)`

-->
