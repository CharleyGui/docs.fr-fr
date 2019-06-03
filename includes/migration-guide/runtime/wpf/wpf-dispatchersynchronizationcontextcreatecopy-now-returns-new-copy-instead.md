---
ms.openlocfilehash: ff4d67a1c821fc96130c4efbd88eb5c56766da06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379514"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>Le DispatcherSynchronizationContext.CreateCopy WPF retourne désormais une nouvelle copie au lieu de l’instance actuelle

|   |   |
|---|---|
|Détails|Dans .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> retournait une référence à l’instance actuelle, principalement pour optimiser les performances. Dans le .NET Framework 4.5, il retourne une nouvelle instance, ce qui permet, pour la première fois, de conclure que les références égales indiquent que le thread en cours d’exécution se trouve dans le bon contexte de synchronisation.  Il est peu probable que le code qui vérifie l’identité de ces références soit affecté. Cependant, en raison de cette modification, le code qui appelle <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> doit être testé dans le cadre de la migration vers .NET Framework 4.5 ou ultérieur.|
|Suggestion|N’oubliez pas que <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> retourne désormais un nouvel objet <xref:System.Threading.SynchronizationContext?displayProperty=name>. Avant, le code qui utilisait l’équivalence des références générées de cette manière ne vérifiait pas réellement si le contexte était approprié. À présent, avec .NET Framework 4.5 ou ultérieur, le contexte est bien vérifié.  Bien que cela soit peu susceptible de provoquer des problèmes, l’utilisation des chemins de code concernés doit suffire à déterminer si cela peut poser un problème.|
|Portée|Mineur|
|Version|4.5|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|
