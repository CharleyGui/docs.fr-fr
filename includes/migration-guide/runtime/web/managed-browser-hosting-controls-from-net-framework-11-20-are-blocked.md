---
ms.openlocfilehash: 83d3f24680531d1e447f047151a28c98ce0da04b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620070"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a>Les navigateurs managés hébergeant des contrôles de .NET Framework 1.1 et 2.0 sont bloqués

#### <a name="details"></a>Détails

L'hébergement de ces contrôles est bloqué dans Internet Explorer.

#### <a name="suggestion"></a>Suggestion

Internet Explorer ne démarrera pas les applications qui utilisent des contrôles d'hébergement de navigateur géré. Le comportement précédent peut être restauré en définissant la valeur de EnableIEHosting de la sous-clé de Registre <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> sur <code>1</code> pour les systèmes x86 et pour les processus 32 bits sur les systèmes x64, et définissant la valeur <code>EnableIEHosting</code> de la sous-clé de Registre <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> sur <code>1</code> pour les processus 64 bits sur les systèmes x64.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime|
