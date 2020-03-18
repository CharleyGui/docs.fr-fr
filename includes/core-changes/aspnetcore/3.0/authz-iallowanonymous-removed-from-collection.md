---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901741"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a>Autorisation: IAllowAnonymous retiré de AuthorizationFilterContext.Filters

En ce qui concerne ASP.NET Core 3.0, MVC n’ajoute pas [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) pour les attributs [[autorisés]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) qui ont été découverts sur les contrôleurs et les méthodes d’action. Ce changement est abordé localement <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>pour les dérivés de <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> , <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> mais c’est un changement de rupture pour et les implémentations. Ces implémentations enveloppées dans un attribut [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) sont un moyen [populaire](https://stackoverflow.com/a/41348219/608220) et pris en charge d’obtenir une autorisation fortement typée et basée sur des attributs lorsque la configuration et l’injection de dépendance sont nécessaires.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

<xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous>dans la collection [AuthorizationFilterContext.Filters.](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) Le test de la présence de l’interface était une approche valide pour remplacer ou désactiver le filtre sur les méthodes de contrôleur individuels.

#### <a name="new-behavior"></a>Nouveau comportement

`IAllowAnonymous`n’apparaît plus `AuthorizationFilterContext.Filters` dans la collection. `IAsyncAuthorizationFilter`les implémentations qui dépendent de l’ancien comportement causent généralement des réponses intermittentes HTTP 401 Non autorisées ou HTTP 403 Interdites.

#### <a name="reason-for-change"></a>Raison du changement

Une nouvelle stratégie de routage de point final a été introduite dans ASP.NET Core 3.0.

#### <a name="recommended-action"></a>Action recommandée

Rechercher les métadonnées `IAllowAnonymous`de point de terminaison pour . Par exemple :

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

Un exemple de cette technique est vu dans [cette méthode HasAllowAnonymous](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!--

#### Affected APIs

Not detectable via API analysis

-->
