---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901741"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a>Autorisation : IAllowAnonymous supprimé de AuthorizationFilterContext. filters

À partir de ASP.NET Core 3,0, MVC n’ajoute pas de [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) pour les attributs [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) qui ont été découverts sur les contrôleurs et les méthodes d’action. Cette modification est traitée localement pour les dérivés <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>de, mais il s’agit d’une <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> modification <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> avec rupture pour les implémentations et. Ces implémentations encapsulées dans un attribut [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) sont un moyen [populaire](https://stackoverflow.com/a/41348219/608220) et pris en charge pour obtenir une autorisation fortement typée basée sur les attributs lorsque la configuration et l’injection de dépendances sont requises.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

<xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous>apparaît dans la collection [AuthorizationFilterContext. filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) . Le test de la présence de l’interface était une approche valide pour remplacer ou désactiver le filtre sur des méthodes de contrôleur individuelles.

#### <a name="new-behavior"></a>Nouveau comportement

`IAllowAnonymous`n’apparaît plus dans la `AuthorizationFilterContext.Filters` collection. `IAsyncAuthorizationFilter`les implémentations qui dépendent de l’ancien comportement entraînent généralement une réponse intermittente HTTP 401 non autorisée ou HTTP 403 interdit.

#### <a name="reason-for-change"></a>Motif de modification

Une nouvelle stratégie de routage des points de terminaison a été introduite dans ASP.NET Core 3,0.

#### <a name="recommended-action"></a>Action recommandée

Recherchez dans les métadonnées `IAllowAnonymous`de point de terminaison. Par exemple :

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

Un exemple de cette technique est illustré dans [cette méthode HasAllowAnonymous](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucun

<!--

#### Affected APIs

Not detectable via API analysis

-->
