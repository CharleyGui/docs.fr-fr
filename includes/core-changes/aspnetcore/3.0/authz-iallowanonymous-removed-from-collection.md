---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032465"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a><span data-ttu-id="71b1b-101">Autorisation : IAllowAnonymous supprimé de AuthorizationFilterContext. filters</span><span class="sxs-lookup"><span data-stu-id="71b1b-101">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>

<span data-ttu-id="71b1b-102">À partir de ASP.NET Core 3,0, MVC n’ajoute pas de [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) pour les attributs [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) qui ont été découverts sur les contrôleurs et les méthodes d’action.</span><span class="sxs-lookup"><span data-stu-id="71b1b-102">As of ASP.NET Core 3.0, MVC doesn't add [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) for [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) attributes that were discovered on controllers and action methods.</span></span> <span data-ttu-id="71b1b-103">Cette modification est traitée localement pour les dérivés de <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute> , mais il s’agit d’une modification avec rupture pour les <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implémentations et.</span><span class="sxs-lookup"><span data-stu-id="71b1b-103">This change is addressed locally for derivatives of <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, but it's a breaking change for <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> and <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementations.</span></span> <span data-ttu-id="71b1b-104">Ces implémentations encapsulées dans un attribut [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) sont un moyen [populaire](https://stackoverflow.com/a/41348219/608220) et pris en charge pour obtenir une autorisation fortement typée basée sur les attributs lorsque la configuration et l’injection de dépendances sont requises.</span><span class="sxs-lookup"><span data-stu-id="71b1b-104">Such implementations wrapped in a [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) attribute are a [popular](https://stackoverflow.com/a/41348219/608220) and supported way to achieve strongly-typed, attribute-based authorization when both configuration and dependency injection are required.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="71b1b-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="71b1b-105">Version introduced</span></span>

<span data-ttu-id="71b1b-106">3.0</span><span class="sxs-lookup"><span data-stu-id="71b1b-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="71b1b-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="71b1b-107">Old behavior</span></span>

<span data-ttu-id="71b1b-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> apparaît dans la collection [AuthorizationFilterContext. filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) .</span><span class="sxs-lookup"><span data-stu-id="71b1b-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> appeared in the [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) collection.</span></span> <span data-ttu-id="71b1b-109">Le test de la présence de l’interface était une approche valide pour remplacer ou désactiver le filtre sur des méthodes de contrôleur individuelles.</span><span class="sxs-lookup"><span data-stu-id="71b1b-109">Testing for the interface's presence was a valid approach to override or disable the filter on individual controller methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="71b1b-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="71b1b-110">New behavior</span></span>

<span data-ttu-id="71b1b-111">`IAllowAnonymous` n’apparaît plus dans la `AuthorizationFilterContext.Filters` collection.</span><span class="sxs-lookup"><span data-stu-id="71b1b-111">`IAllowAnonymous` no longer appears in the `AuthorizationFilterContext.Filters` collection.</span></span> <span data-ttu-id="71b1b-112">`IAsyncAuthorizationFilter` les implémentations qui dépendent de l’ancien comportement entraînent généralement une réponse intermittente HTTP 401 non autorisée ou HTTP 403 interdit.</span><span class="sxs-lookup"><span data-stu-id="71b1b-112">`IAsyncAuthorizationFilter` implementations that are dependent on the old behavior typically cause intermittent HTTP 401 Unauthorized or HTTP 403 Forbidden responses.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="71b1b-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="71b1b-113">Reason for change</span></span>

<span data-ttu-id="71b1b-114">Une nouvelle stratégie de routage des points de terminaison a été introduite dans ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="71b1b-114">A new endpoint routing strategy was introduced in ASP.NET Core 3.0.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="71b1b-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="71b1b-115">Recommended action</span></span>

<span data-ttu-id="71b1b-116">Recherchez dans les métadonnées de point de terminaison `IAllowAnonymous` .</span><span class="sxs-lookup"><span data-stu-id="71b1b-116">Search the endpoint metadata for `IAllowAnonymous`.</span></span> <span data-ttu-id="71b1b-117">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="71b1b-117">For example:</span></span>

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

<span data-ttu-id="71b1b-118">Un exemple de cette technique est illustré dans [cette méthode HasAllowAnonymous](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span><span class="sxs-lookup"><span data-stu-id="71b1b-118">An example of this technique is seen in [this HasAllowAnonymous method](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span></span>

#### <a name="category"></a><span data-ttu-id="71b1b-119">Category</span><span class="sxs-lookup"><span data-stu-id="71b1b-119">Category</span></span>

<span data-ttu-id="71b1b-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="71b1b-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="71b1b-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="71b1b-121">Affected APIs</span></span>

<span data-ttu-id="71b1b-122">None</span><span class="sxs-lookup"><span data-stu-id="71b1b-122">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
