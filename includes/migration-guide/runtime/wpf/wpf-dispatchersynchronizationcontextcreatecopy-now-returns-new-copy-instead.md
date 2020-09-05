---
ms.openlocfilehash: a806107456a65a4919592da9535a2617f677cfe0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497464"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>Le DispatcherSynchronizationContext.CreateCopy WPF retourne désormais une nouvelle copie au lieu de l’instance actuelle

#### <a name="details"></a>Détails

Dans .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> retournait une référence à l’instance actuelle, principalement pour optimiser les performances. Dans le .NET Framework 4.5, il retourne une nouvelle instance, ce qui permet, pour la première fois, de conclure que les références égales indiquent que le thread en cours d’exécution se trouve dans le bon contexte de synchronisation.  Il est peu probable que le code qui vérifie l’identité de ces références soit affecté. Cependant, en raison de cette modification, le code qui appelle <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> doit être testé dans le cadre de la migration vers .NET Framework 4.5 ou ultérieur.

#### <a name="suggestion"></a>Suggestion

N’oubliez pas que <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> retourne désormais un nouvel objet <xref:System.Threading.SynchronizationContext?displayProperty=fullName>. Avant, le code qui utilisait l’équivalence des références générées de cette manière ne vérifiait pas réellement si le contexte était approprié. À présent, avec .NET Framework 4.5 ou ultérieur, le contexte est bien vérifié.  Bien que cela soit peu susceptible de provoquer des problèmes, l’utilisation des chemins de code concernés doit suffire à déterminer si cela peut poser un problème.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy`

-->
