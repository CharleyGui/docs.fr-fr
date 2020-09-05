---
ms.openlocfilehash: 5a96b40e5e0df6a47415acecab410444a713632b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496100"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>Les EventListeners ETW ne capturent pas les événements provenant de fournisseurs avec des mots clés explicites (comme le fournisseur TPL)

#### <a name="details"></a>Détails

Les EventListeners ETW avec un masque de mot clé vide ne capturent pas correctement les événements provenant de fournisseurs ayant des mots clés explicites. Dans le .NET Framework 4.5, le fournisseur TPL fournissait des mots clés explicites et provoquait ce problème. Dans le .NET Framework 4.6, les EventListeners ont été mis à jour pour ne plus causer ce problème.

#### <a name="suggestion"></a>Suggestion

Pour contourner ce problème, remplacez les appels à <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> par des appels à la surcharge EnableEvents qui spécifie explicitement le masque &quot;tous les mots clés&quot; à utiliser : <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>. Étant donné que ce problème a été résolu dans .NET Framework 4.6, vous pouvez également effectuer la mise à niveau vers cette version du .NET Framework.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)`

-->
