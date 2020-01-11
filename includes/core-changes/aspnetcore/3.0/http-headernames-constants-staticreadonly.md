---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901909"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP : les constantes HeaderNames ont été modifiées en ReadOnly statique

À partir de ASP.NET Core 3,0 Preview 5, les champs de <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changés de `const` à `static readonly`.

Pour plus d’informations, consultez [dotnet/aspnetcore # 9514](https://github.com/dotnet/aspnetcore/issues/9514).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Ces champs servent à `const`.

#### <a name="new-behavior"></a>Nouveau comportement

Ces champs sont désormais `static readonly`.

#### <a name="reason-for-change"></a>Motif de modification

La modification :

* Empêche l’incorporation des valeurs dans les limites de l’assembly, ce qui permet d’obtenir des corrections de valeurs en fonction des besoins.
* Active les vérifications d’égalité de référence plus rapides.

#### <a name="recommended-action"></a>Action recommandée

Recompilation sur 3,0. Le code source qui utilise ces champs de la manière suivante ne peut plus le faire :

* En tant qu’argument d’attribut
* En tant que `case` dans une instruction `switch`
* Lors de la définition d’un autre `const`

Pour contourner la modification avec rupture, basculez vers à l’aide de constantes de nom d’en-tête ou de littéraux de chaîne définis automatiquement.

#### <a name="category"></a>Catégorie

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
