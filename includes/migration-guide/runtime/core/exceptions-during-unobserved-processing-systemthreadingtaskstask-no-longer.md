---
ms.openlocfilehash: bae211e5684dc1fbbb1d7e69c928e37c1c532096
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497492"
---
### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>Les exceptions qui sont levées pendant un traitement non pris en charge dans System.Threading.Tasks.Task ne se propagent plus sur le thread finaliseur

#### <a name="details"></a>Détails

Comme la classe <xref:System.Threading.Tasks.Task?displayProperty=fullName> représente une opération asynchrone, elle intercepte toutes les exceptions sans gravité qui se produisent pendant le traitement asynchrone. Dans le .NET Framework 4.5, si une exception n’est pas prise en charge et si votre code n’attend jamais la tâche, l’exception ne se propagera plus sur le thread finaliseur et arrêtera le processus pendant l’opération garbage collection. Cette modification améliore la fiabilité des applications qui utilisent la classe Task pour exécuter un traitement asynchrone non pris en charge.

#### <a name="suggestion"></a>Suggestion

Si une application dépend d’exceptions asynchrones non prises en charge qui se propagent au thread finaliseur, le comportement précédent peut être restauré en fournissant un gestionnaire approprié pour l’événement <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> ou en définissant un [élément de configuration du runtime](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md).

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

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
