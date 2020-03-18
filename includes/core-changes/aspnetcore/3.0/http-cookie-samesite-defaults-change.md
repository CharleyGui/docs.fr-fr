---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74282524"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a>HTTP: Certains cookies SameSite défauts changés à Aucun

`SameSite`est une option pour les cookies qui peuvent aider à atténuer certaines attaques cross-Site Request Forgery (CSRF). Lorsque cette option a été introduite au départ, des défauts de paiement incohérents ont été utilisés dans divers ASP.NET API de base. L’incohérence a conduit à des résultats confus. En ce qui concerne ASP.NET Core 3.0, ces défauts sont mieux alignés. Vous devez adhérer à cette fonctionnalité par composante.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Des API de base similaires <xref:Microsoft.AspNetCore.Http.SameSiteMode> ASP.NET ont utilisé différentes valeurs par défaut. Un exemple de l’incohérence est `HttpResponse.Cookies.Append(String, String)` `HttpResponse.Cookies.Append(String, String, CookieOptions)`vu dans et `SameSiteMode.None` `SameSiteMode.Lax`, qui a manqué à et , respectivement.

#### <a name="new-behavior"></a>Nouveau comportement

Toutes les API `SameSiteMode.None`affectées par défaut à .

#### <a name="reason-for-change"></a>Raison du changement

La valeur par défaut `SameSite` a été modifiée pour faire une fonction d’opt-in.

#### <a name="recommended-action"></a>Action recommandée

Chaque composant qui émet des `SameSite` cookies doit décider s’il est approprié pour ses scénarios. Examinez votre utilisation des API `SameSite` touchées et reconfigurez au besoin.

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
