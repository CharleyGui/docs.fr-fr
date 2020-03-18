---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901741"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a><span data-ttu-id="99cd3-101">Autorisation: IAllowAnonymous retiré de AuthorizationFilterContext.Filters</span><span class="sxs-lookup"><span data-stu-id="99cd3-101">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>

<span data-ttu-id="99cd3-102">En ce qui concerne ASP.NET Core 3.0, MVC n’ajoute pas [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) pour les attributs [[autorisés]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) qui ont été découverts sur les contrôleurs et les méthodes d’action.</span><span class="sxs-lookup"><span data-stu-id="99cd3-102">As of ASP.NET Core 3.0, MVC doesn't add [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) for [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) attributes that were discovered on controllers and action methods.</span></span> <span data-ttu-id="99cd3-103">Ce changement est abordé localement <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>pour les dérivés de <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> , <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> mais c’est un changement de rupture pour et les implémentations.</span><span class="sxs-lookup"><span data-stu-id="99cd3-103">This change is addressed locally for derivatives of <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, but it's a breaking change for <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> and <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementations.</span></span> <span data-ttu-id="99cd3-104">Ces implémentations enveloppées dans un attribut [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) sont un moyen [populaire](https://stackoverflow.com/a/41348219/608220) et pris en charge d’obtenir une autorisation fortement typée et basée sur des attributs lorsque la configuration et l’injection de dépendance sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="99cd3-104">Such implementations wrapped in a [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) attribute are a [popular](https://stackoverflow.com/a/41348219/608220) and supported way to achieve strongly-typed, attribute-based authorization when both configuration and dependency injection are required.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="99cd3-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="99cd3-105">Version introduced</span></span>

<span data-ttu-id="99cd3-106">3.0</span><span class="sxs-lookup"><span data-stu-id="99cd3-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="99cd3-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="99cd3-107">Old behavior</span></span>

<span data-ttu-id="99cd3-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous>dans la collection [AuthorizationFilterContext.Filters.](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A)</span><span class="sxs-lookup"><span data-stu-id="99cd3-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> appeared in the [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) collection.</span></span> <span data-ttu-id="99cd3-109">Le test de la présence de l’interface était une approche valide pour remplacer ou désactiver le filtre sur les méthodes de contrôleur individuels.</span><span class="sxs-lookup"><span data-stu-id="99cd3-109">Testing for the interface's presence was a valid approach to override or disable the filter on individual controller methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="99cd3-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="99cd3-110">New behavior</span></span>

<span data-ttu-id="99cd3-111">`IAllowAnonymous`n’apparaît plus `AuthorizationFilterContext.Filters` dans la collection.</span><span class="sxs-lookup"><span data-stu-id="99cd3-111">`IAllowAnonymous` no longer appears in the `AuthorizationFilterContext.Filters` collection.</span></span> <span data-ttu-id="99cd3-112">`IAsyncAuthorizationFilter`les implémentations qui dépendent de l’ancien comportement causent généralement des réponses intermittentes HTTP 401 Non autorisées ou HTTP 403 Interdites.</span><span class="sxs-lookup"><span data-stu-id="99cd3-112">`IAsyncAuthorizationFilter` implementations that are dependent on the old behavior typically cause intermittent HTTP 401 Unauthorized or HTTP 403 Forbidden responses.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="99cd3-113">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="99cd3-113">Reason for change</span></span>

<span data-ttu-id="99cd3-114">Une nouvelle stratégie de routage de point final a été introduite dans ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="99cd3-114">A new endpoint routing strategy was introduced in ASP.NET Core 3.0.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="99cd3-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="99cd3-115">Recommended action</span></span>

<span data-ttu-id="99cd3-116">Rechercher les métadonnées `IAllowAnonymous`de point de terminaison pour .</span><span class="sxs-lookup"><span data-stu-id="99cd3-116">Search the endpoint metadata for `IAllowAnonymous`.</span></span> <span data-ttu-id="99cd3-117">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="99cd3-117">For example:</span></span>

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

<span data-ttu-id="99cd3-118">Un exemple de cette technique est vu dans [cette méthode HasAllowAnonymous](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span><span class="sxs-lookup"><span data-stu-id="99cd3-118">An example of this technique is seen in [this HasAllowAnonymous method](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span></span>

#### <a name="category"></a><span data-ttu-id="99cd3-119">Category</span><span class="sxs-lookup"><span data-stu-id="99cd3-119">Category</span></span>

<span data-ttu-id="99cd3-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="99cd3-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="99cd3-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="99cd3-121">Affected APIs</span></span>

<span data-ttu-id="99cd3-122">None</span><span class="sxs-lookup"><span data-stu-id="99cd3-122">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
