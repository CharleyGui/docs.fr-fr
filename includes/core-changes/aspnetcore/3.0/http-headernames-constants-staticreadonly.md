---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901909"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP: HeaderNames constantes changé à statique readonly

À partir de ASP.NET Core 3.0 Aperçu 5, `const` `static readonly`les champs dans <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changé de .

Pour discussion, voir [dotnet/aspnetcore 9514](https://github.com/dotnet/aspnetcore/issues/9514).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Ces champs étaient `const`autrefois .

#### <a name="new-behavior"></a>Nouveau comportement

Ces champs `static readonly`sont maintenant .

#### <a name="reason-for-change"></a>Raison du changement

Le changement:

* Empêche les valeurs d’être intégrées au-delà des limites de l’assemblage, ce qui permet des corrections de valeur au besoin.
* Permet des contrôles plus rapides de l’égalité des références.

#### <a name="recommended-action"></a>Action recommandée

Recomplez contre 3.0. Le code source utilisant ces champs de la manière suivante ne peut plus le faire :

* Comme argument d’attribut
* Comme `case` un `switch` dans une déclaration
* Lors de la définition d’un autre`const`

Pour contourner le changement de rupture, passez à l’utilisation de constantes de noms d’en-tête auto-définies ou de littérals de cordes.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
