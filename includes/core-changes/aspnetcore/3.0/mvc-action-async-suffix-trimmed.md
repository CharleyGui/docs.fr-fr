---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901803"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="d3e56-101">MVC: Suffixe Async coupé à partir de noms d’action contrôleur</span><span class="sxs-lookup"><span data-stu-id="d3e56-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="d3e56-102">Dans le cadre de l’adresse [dotnet/aspnetcore 4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core `Async` MVC coupe le suffixe des noms d’action par défaut.</span><span class="sxs-lookup"><span data-stu-id="d3e56-102">As part of addressing [dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="d3e56-103">En commençant par ASP.NET Core 3.0, ce changement affecte à la fois le routage et la génération de liaisons.</span><span class="sxs-lookup"><span data-stu-id="d3e56-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d3e56-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d3e56-104">Version introduced</span></span>

<span data-ttu-id="d3e56-105">3.0</span><span class="sxs-lookup"><span data-stu-id="d3e56-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d3e56-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="d3e56-106">Old behavior</span></span>

<span data-ttu-id="d3e56-107">Considérez le contrôleur ASP.NET Core MVC suivant :</span><span class="sxs-lookup"><span data-stu-id="d3e56-107">Consider the following ASP.NET Core MVC controller:</span></span>

```csharp
public class ProductController : Controller
{
    public async IActionResult ListAsync()
    {
        var model = await DbContext.Products.ToListAsync();
        return View(model);
    }
}
```

<span data-ttu-id="d3e56-108">L’action est `Product/ListAsync`routable via .</span><span class="sxs-lookup"><span data-stu-id="d3e56-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="d3e56-109">La génération de `Async` liens nécessite de spécifier le suffixe.</span><span class="sxs-lookup"><span data-stu-id="d3e56-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="d3e56-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d3e56-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="d3e56-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="d3e56-111">New behavior</span></span>

<span data-ttu-id="d3e56-112">Dans ASP.NET Core 3.0, l’action est `Product/List`routable via .</span><span class="sxs-lookup"><span data-stu-id="d3e56-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="d3e56-113">Le code de génération `Async` de lien doit omettre le suffixe.</span><span class="sxs-lookup"><span data-stu-id="d3e56-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="d3e56-114">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d3e56-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="d3e56-115">Cette modification n’affecte pas `[ActionName]` les noms spécifiés à l’aide de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="d3e56-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="d3e56-116">Le nouveau comportement peut `MvcOptions.SuppressAsyncSuffixInActionNames` être `false` `Startup.ConfigureServices`désactivé en définissant dans :</span><span class="sxs-lookup"><span data-stu-id="d3e56-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="d3e56-117">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="d3e56-117">Reason for change</span></span>

<span data-ttu-id="d3e56-118">Par convention, asynchrone .NET méthodes sont `Async`suffixes avec .</span><span class="sxs-lookup"><span data-stu-id="d3e56-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="d3e56-119">Cependant, lorsqu’une méthode définit une action MVC, il n’est pas souhaitable d’utiliser le `Async` suffixe.</span><span class="sxs-lookup"><span data-stu-id="d3e56-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d3e56-120">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d3e56-120">Recommended action</span></span>

<span data-ttu-id="d3e56-121">Si votre application dépend des actions MVC `Async` préservant le suffixe du nom, choisissez l’une des mesures d’atténuation suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3e56-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="d3e56-122">Utilisez `[ActionName]` l’attribut pour préserver le nom d’origine.</span><span class="sxs-lookup"><span data-stu-id="d3e56-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="d3e56-123">Désactiver entièrement le changement de `MvcOptions.SuppressAsyncSuffixInActionNames` `false` nom `Startup.ConfigureServices`en mettant en place :</span><span class="sxs-lookup"><span data-stu-id="d3e56-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a><span data-ttu-id="d3e56-124">Category</span><span class="sxs-lookup"><span data-stu-id="d3e56-124">Category</span></span>

<span data-ttu-id="d3e56-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d3e56-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d3e56-126">API affectées</span><span class="sxs-lookup"><span data-stu-id="d3e56-126">Affected APIs</span></span>

<span data-ttu-id="d3e56-127">None</span><span class="sxs-lookup"><span data-stu-id="d3e56-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
