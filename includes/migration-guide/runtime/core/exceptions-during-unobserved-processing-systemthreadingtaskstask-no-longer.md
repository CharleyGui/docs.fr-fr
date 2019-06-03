---
ms.openlocfilehash: b0e6d6f228647148083d3df64e65f817dc3455d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379563"
---
### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>Les exceptions qui sont levées pendant un traitement non pris en charge dans System.Threading.Tasks.Task ne se propagent plus sur le thread finaliseur

|   |   |
|---|---|
|Détails|Comme la classe <xref:System.Threading.Tasks.Task?displayProperty=name> représente une opération asynchrone, elle intercepte toutes les exceptions sans gravité qui se produisent pendant le traitement asynchrone. Dans le .NET Framework 4.5, si une exception n’est pas prise en charge et si votre code n’attend jamais la tâche, l’exception ne se propagera plus sur le thread finaliseur et arrêtera le processus pendant l’opération garbage collection. Cette modification améliore la fiabilité des applications qui utilisent la classe Task pour exécuter un traitement asynchrone non pris en charge.|
|Suggestion|Si une application dépend d’exceptions asynchrones non prises en charge qui se propagent au thread finaliseur, le comportement précédent peut être restauré en fournissant un gestionnaire approprié pour l’événement <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> ou en définissant un [élément de configuration du runtime](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md).|
|Portée|Microsoft Edge|
|Version|4.5|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType></li></ul>|
