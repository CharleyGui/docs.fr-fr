---
ms.openlocfilehash: d4f0095bc9fde98087dce528c8154d9c9ac6ddb7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621792"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>La correction orthographique dans WPF échoue de façon inattendue

#### <a name="details"></a>Détails

Ceci inclut plusieurs problèmes du vérificateur orthographique de WPF :<ul><li>Le vérificateur orthographique de WPF lève parfois <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></li><li>Le vérificateur orthographique de WPF échoue avec <xref:System.UnauthorizedAccessException> quand les applications sont lancées avec « Exécuter en tant qu’autre utilisateur »</li><li>Le vérificateur orthographique de WPF identifie incorrectement des fautes d’orthographe dans les mots composés, comme « Hausnummer » en allemand.</li></ul>

#### <a name="suggestion"></a>Suggestion

Problème n° 1 : ce problème a été corrigé dans le .NET Framework 4.6.2. Problème n° 2 : le vérificateur orthographique de WPF n’est plus pris en charge quand les applications sont lancées avec « Exécuter en tant qu’autre utilisateur ». À compter du .NET Framework 4.6.2, les applications lancées de cette manière ne plantent plus de façon inattendue : à la place, le vérificateur orthographique est désactivé en mode silencieux. Problème n° 3 : ce problème a été corrigé dans le .NET Framework 4.6.2.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.6.1|
|Type|Runtime|
