---
ms.openlocfilehash: 80e61d4dd5b8d4754a39e95e37475fefff57fcbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617175"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a>Les nouvelles surcharges (ambiguës) Dispatcher.Invoke peuvent entraîner un comportement différent

#### <a name="details"></a>Détails

NET Framework 4.5 ajoute de nouvelles surcharges à <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> qui incluent un paramètre de type <xref:System.Action>. Quand le code existant est recompilé, les compilateurs peuvent résoudre les appels aux méthodes Dispatcher.Invoke dotées d’un paramètre <xref:System.Delegate> comme des appels aux méthodes Dispatcher.Invoke ayant un paramètre <xref:System.Action>. Si un appel à une surcharge Dispatcher.Invoke avec un paramètre <xref:System.Delegate> est résolu comme un appel à une surcharge Dispatcher.Invoke avec un paramètre <xref:System.Action>, les différences de comportement suivantes peuvent survenir :

- Si une exception se produit, les événements <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> et <xref:System.Windows.Threading.Dispatcher.UnhandledException> ne sont pas déclenchés. À la place, les exceptions sont gérées par l'événement <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName>.
- Les appels à certains membres, tels que <xref:System.Windows.Threading.DispatcherOperation.Result>, sont bloqués jusqu'à ce que l'opération soit terminée.

#### <a name="suggestion"></a>Suggestion

Pour éviter toute ambiguïté (et d’éventuelles différences au niveau de la gestion des exceptions et du blocage des comportements), le code Dispatcher.Invoke appelant peut passer un object[] vide en tant que deuxième paramètre à l’appel Invoke de manière à garantir la résolution de la surcharge de méthode .NET Framework 4.0.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4,5         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
