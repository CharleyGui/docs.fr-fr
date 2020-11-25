---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032534"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP : les constantes HeaderNames ont été modifiées en ReadOnly statique

À partir de ASP.NET Core 3,0 Preview 5, les champs de <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> ont été remplacés par `const` `static readonly` .

Pour plus d’informations, consultez [dotnet/aspnetcore # 9514](https://github.com/dotnet/aspnetcore/issues/9514).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Ces champs sont utilisés comme `const` .

#### <a name="new-behavior"></a>Nouveau comportement

Ces champs sont maintenant `static readonly` .

#### <a name="reason-for-change"></a>Motif de modification

La modification :

* Empêche l’incorporation des valeurs dans les limites de l’assembly, ce qui permet d’obtenir des corrections de valeurs en fonction des besoins.
* Active les vérifications d’égalité de référence plus rapides.

#### <a name="recommended-action"></a>Action recommandée

Recompilation sur 3,0. Le code source qui utilise ces champs de la manière suivante ne peut plus le faire :

* En tant qu’argument d’attribut
* En tant que `case` dans une `switch` instruction
* Lors de la définition d’un autre `const`

Pour contourner la modification avec rupture, basculez vers à l’aide de constantes de nom d’en-tête ou de littéraux de chaîne définis automatiquement.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
