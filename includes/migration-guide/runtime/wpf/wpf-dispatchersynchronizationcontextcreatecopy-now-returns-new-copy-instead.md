---
ms.openlocfilehash: fc6066fd0b23d299158114cb397934041b99ba47
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620464"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>Le DispatcherSynchronizationContext.CreateCopy WPF retourne désormais une nouvelle copie au lieu de l’instance actuelle

#### <a name="details"></a>Détails

Dans .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> retournait une référence à l’instance actuelle, principalement pour optimiser les performances. Dans le .NET Framework 4.5, il retourne une nouvelle instance, ce qui permet, pour la première fois, de conclure que les références égales indiquent que le thread en cours d’exécution se trouve dans le bon contexte de synchronisation.  Il est peu probable que le code qui vérifie l’identité de ces références soit affecté. Cependant, en raison de cette modification, le code qui appelle <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> doit être testé dans le cadre de la migration vers .NET Framework 4.5 ou ultérieur.

#### <a name="suggestion"></a>Suggestion

N’oubliez pas que <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> retourne désormais un nouvel objet <xref:System.Threading.SynchronizationContext?displayProperty=fullName>. Avant, le code qui utilisait l’équivalence des références générées de cette manière ne vérifiait pas réellement si le contexte était approprié. À présent, avec .NET Framework 4.5 ou ultérieur, le contexte est bien vérifié.  Bien que cela soit peu susceptible de provoquer des problèmes, l’utilisation des chemins de code concernés doit suffire à déterminer si cela peut poser un problème.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|
