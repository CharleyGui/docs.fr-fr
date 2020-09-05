---
ms.openlocfilehash: d4e60f2a59980263916718ebcc71cc359952c031
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497876"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>La correction orthographique dans WPF échoue de façon inattendue

#### <a name="details"></a>Détails

Ceci inclut plusieurs problèmes du vérificateur orthographique de WPF :<ul><li>Le vérificateur orthographique de WPF lève parfois <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></li><li>Le vérificateur orthographique de WPF échoue avec <xref:System.UnauthorizedAccessException> quand les applications sont lancées avec « Exécuter en tant qu’autre utilisateur »</li><li>Le vérificateur orthographique de WPF identifie incorrectement des fautes d’orthographe dans les mots composés, comme « Hausnummer » en allemand.</li></ul>

#### <a name="suggestion"></a>Suggestion

Problème n° 1 : ce problème a été corrigé dans le .NET Framework 4.6.2. Problème n° 2 : le vérificateur orthographique de WPF n’est plus pris en charge quand les applications sont lancées avec « Exécuter en tant qu’autre utilisateur ». À compter du .NET Framework 4.6.2, les applications lancées de cette manière ne plantent plus de façon inattendue : à la place, le vérificateur orthographique est désactivé en mode silencieux. Problème n° 3 : ce problème a été corrigé dans le .NET Framework 4.6.2.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.6.1|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
