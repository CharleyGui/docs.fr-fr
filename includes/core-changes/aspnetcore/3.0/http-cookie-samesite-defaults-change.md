---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74282524"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a>HTTP : certaines valeurs par défaut de SameSite de cookie ont été remplacées par None

`SameSite`est une option pour les cookies qui peuvent aider à atténuer certaines attaques de falsification de requête intersites (CSRF). Lorsque cette option a été introduite pour la première fois, des valeurs par défaut incohérentes ont été utilisées dans plusieurs API ASP.NET Core. L’incohérence a conduit à des résultats confuss. À partir de ASP.NET Core 3,0, ces valeurs par défaut sont mieux alignées. Vous devez accepter cette fonctionnalité en fonction de chaque composant.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les API de ASP.NET Core similaires utilisaient des valeurs par défaut <xref:Microsoft.AspNetCore.Http.SameSiteMode> différentes. Un exemple de l’incohérence est visible dans `HttpResponse.Cookies.Append(String, String)` et `HttpResponse.Cookies.Append(String, String, CookieOptions)`, qui est défini par `SameSiteMode.None` défaut `SameSiteMode.Lax`respectivement sur et.

#### <a name="new-behavior"></a>Nouveau comportement

Toutes les API affectées ont `SameSiteMode.None`par défaut la valeur.

#### <a name="reason-for-change"></a>Motif de modification

La valeur par défaut a été modifiée `SameSite` pour rendre une fonctionnalité d’abonnement.

#### <a name="recommended-action"></a>Action recommandée

Chaque composant qui émet des cookies doit décider si `SameSite` est approprié pour ses scénarios. Passez en revue l’utilisation des API affectées et `SameSite` Reconfigurez-les en fonction des besoins.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
