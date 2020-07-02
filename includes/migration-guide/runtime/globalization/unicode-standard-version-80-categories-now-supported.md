---
ms.openlocfilehash: a20fad5f9c95e59c14ffd91f4921cf8bfab443cd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621074"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a>Catégories de version Unicode standard 8.0 maintenant prises en charge

#### <a name="details"></a>Détails

Dans .NET Framework 4.6.2, les données Unicode ont été mises à niveau de la version Unicode Standard 6.3 vers la version 8.0.  Quand vous demandez des catégories de caractères Unicode dans .NET Framework 4.6.2, certains résultats peuvent ne pas correspondre à ceux des versions précédentes du .NET Framework.  Ce changement affecte principalement les syllabes Cherokee et voyelles diacritiques nouveau taï-lue ainsi que les accents toniques.

#### <a name="suggestion"></a>Suggestion

Passez en revue le code et supprimez ou modifiez la logique qui varie selon les catégories de caractères Unicode codées en dur.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.6.2|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
