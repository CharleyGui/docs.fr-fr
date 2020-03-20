---
ms.openlocfilehash: 09e3f0e168e0dcbe79d8ee7216f2671c67bfb87e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802974"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>La correction orthographique dans WPF échoue de façon inattendue

|   |   |
|---|---|
|Détails|Ceci inclut plusieurs problèmes du vérificateur orthographique de WPF :<ul><li>Le vérificateur orthographique de WPF lève parfois <xref:System.Runtime.InteropServices.COMException?displayProperty=name></li><li>Le vérificateur orthographique de WPF échoue avec <xref:System.UnauthorizedAccessException> quand les applications sont lancées avec « Exécuter en tant qu’autre utilisateur »</li><li>Le vérificateur orthographique de WPF identifie incorrectement des fautes d’orthographe dans les mots composés, comme « Hausnummer » en allemand.</li></ul>|
|Suggestion|Problème n° 1 : ce problème a été corrigé dans le .NET Framework 4.6.2. Problème n° 2 : le vérificateur orthographique de WPF n’est plus pris en charge quand les applications sont lancées avec « Exécuter en tant qu’autre utilisateur ». À compter du .NET Framework 4.6.2, les applications lancées de cette manière ne plantent plus de façon inattendue : à la place, le vérificateur orthographique est désactivé en mode silencieux. Problème n° 3 : ce problème a été corrigé dans le .NET Framework 4.6.2.|
|Étendue|Edge|
|Version|4.6.1|
|Type|Runtime|
