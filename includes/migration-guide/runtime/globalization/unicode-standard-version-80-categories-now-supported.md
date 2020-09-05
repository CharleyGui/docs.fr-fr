---
ms.openlocfilehash: f389a9e9bcf4ac1777db66731a085d74889c4a98
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497924"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a>Catégories de version Unicode standard 8.0 maintenant prises en charge

#### <a name="details"></a>Détails

Dans .NET Framework 4.6.2, les données Unicode ont été mises à niveau de la version Unicode Standard 6.3 vers la version 8.0.  Quand vous demandez des catégories de caractères Unicode dans .NET Framework 4.6.2, certains résultats peuvent ne pas correspondre à ceux des versions précédentes du .NET Framework.  Ce changement affecte principalement les syllabes Cherokee et voyelles diacritiques nouveau taï-lue ainsi que les accents toniques.

#### <a name="suggestion"></a>Suggestion

Passez en revue le code et supprimez ou modifiez la logique qui varie selon les catégories de caractères Unicode codées en dur.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.6.2|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType>
- <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType>
- <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Char.GetUnicodeCategory(System.Char)`
- `M:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)`
- `M:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)`

-->
