---
ms.openlocfilehash: 8049bf01bc10c5913fa11b25e49afd1b1317eecc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802974"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>La correction orthographique dans WPF échoue de façon inattendue

|   |   |
|---|---|
|Détails|Ceci inclut plusieurs problèmes du vérificateur orthographique de WPF :<ul><li>Le vérificateur orthographique de WPF lève parfois <xref:System.Runtime.InteropServices.COMException?displayProperty=name></li><li>Le vérificateur orthographique de WPF échoue avec <xref:System.UnauthorizedAccessException> quand les applications sont lancées avec « Exécuter en tant qu’autre utilisateur »</li><li>Le vérificateur orthographique de WPF identifie incorrectement des fautes d’orthographe dans les mots composés, comme « Hausnummer » en allemand.</li></ul>|
|Suggestion|Problème n° 1 : ce problème a été corrigé dans le .NET Framework 4.6.2. Problème n° 2 : le vérificateur orthographique de WPF n’est plus pris en charge quand les applications sont lancées avec « Exécuter en tant qu’autre utilisateur ». À compter du .NET Framework 4.6.2, les applications lancées de cette manière ne plantent plus de façon inattendue : à la place, le vérificateur orthographique est désactivé en mode silencieux. Problème n° 3 : ce problème a été corrigé dans le .NET Framework 4.6.2.|
|Portée|Microsoft Edge|
|Version|4.6.1|
|Type|Runtime|

