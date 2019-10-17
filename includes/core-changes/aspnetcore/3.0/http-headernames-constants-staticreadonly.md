---
ms.openlocfilehash: e0d0a680915f14c2d33f1864ad5ad05aff3dde5f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393949"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP : les constantes HeaderNames ont été modifiées en ReadOnly statique

À partir de ASP.NET Core 3,0 Preview 5, les champs de <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> ont été modifiés de `const` à `static readonly`.

Pour plus d’informations, consultez [ASPNET/AspNetCore # 9514](https://github.com/aspnet/AspNetCore/issues/9514).

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

Ces champs sont `const`.

#### <a name="new-behavior"></a>Nouveau comportement

Ces champs sont maintenant `static readonly`.

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

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
