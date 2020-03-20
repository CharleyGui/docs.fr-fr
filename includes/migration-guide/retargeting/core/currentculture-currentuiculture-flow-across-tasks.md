---
ms.openlocfilehash: efe8a2dd98865f6a24b65ce0f08eb0c574b708f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804614"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a>CurrentCulture et CurrentUICulture se propagent d’une tâche à l’autre

|   |   |
|---|---|
|Détails|À compter de .NET Framework 4.6, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> et <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> sont stockés dans le <xref:System.Threading.ExecutionContext?displayProperty=name> du thread, qui circulent d’une opération asynchrone à une autre. Cela signifie que les changements apportés à <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> ou <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> sont reflétés dans des tâches qui sont exécutées de façon asynchrone par la suite. Cela diffère du comportement des précédentes versions du .NET Framework (qui réinitialisaient <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> et <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> dans toutes les tâches asynchrones).|
|Suggestion|Si vos applications sont affectées par ce changement, vous pouvez le contourner en définissant explicitement le <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> ou <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> souhaité comme première opération dans une tâche asynchrone. L’ancien comportement (qui ne transmet pas <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>) peut également être adopté en définissant le commutateur de compatibilité suivant :<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>Ce problème a été résolu par WPF dans le .NET Framework 4.6.2. Il a également été résolu dans .NET Framework versions 4.6 et 4.6.1 par le biais du correctif décrit dans [l’article 3139549 de la Base de connaissances](https://support.microsoft.com/kb/3139549). Les applications qui ciblent .NET Framework 4.6 ou ultérieur obtiennent automatiquement le comportement approprié dans les applications WPF. <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> est conservé d’une opération de répartiteur à l’autre.|
|Étendue|Secondaire|
|Version|4.6|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType></li></ul>|
