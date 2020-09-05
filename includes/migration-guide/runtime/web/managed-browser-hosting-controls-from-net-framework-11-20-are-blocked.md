---
ms.openlocfilehash: 26539011f0650c7a3bac9e1c41847561905fff58
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497229"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a>Les navigateurs managés hébergeant des contrôles de .NET Framework 1.1 et 2.0 sont bloqués

#### <a name="details"></a>Détails

L'hébergement de ces contrôles est bloqué dans Internet Explorer.

#### <a name="suggestion"></a>Suggestion

Internet Explorer ne démarrera pas les applications qui utilisent des contrôles d'hébergement de navigateur géré. Le comportement précédent peut être restauré en définissant la valeur de EnableIEHosting de la sous-clé de Registre <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> sur <code>1</code> pour les systèmes x86 et pour les processus 32 bits sur les systèmes x64, et définissant la valeur <code>EnableIEHosting</code> de la sous-clé de Registre <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> sur <code>1</code> pour les processus 64 bits sur les systèmes x64.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
