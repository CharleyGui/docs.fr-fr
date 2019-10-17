---
ms.openlocfilehash: dc9f37ae0cd6eef2c67e62421571290bba1c2233
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394016"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="47487-101">MVC : suffixe Async tronqué à partir des noms d’action du contrôleur</span><span class="sxs-lookup"><span data-stu-id="47487-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="47487-102">Dans le cadre de l’adressage [ASPNET/AspNetCore # 4849](https://github.com/aspnet/AspNetCore/issues/4849), ASP.net Core MVC supprime le suffixe `Async` des noms d’action par défaut.</span><span class="sxs-lookup"><span data-stu-id="47487-102">As part of addressing [aspnet/AspNetCore#4849](https://github.com/aspnet/AspNetCore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="47487-103">À compter de ASP.NET Core 3,0, cette modification affecte à la fois le routage et la génération de liens.</span><span class="sxs-lookup"><span data-stu-id="47487-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="47487-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="47487-104">Version introduced</span></span>

<span data-ttu-id="47487-105">3,0</span><span class="sxs-lookup"><span data-stu-id="47487-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="47487-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="47487-106">Old behavior</span></span>

<span data-ttu-id="47487-107">Considérez les ASP.NET Core contrôleur MVC suivants :</span><span class="sxs-lookup"><span data-stu-id="47487-107">Consider the following ASP.NET Core MVC controller:</span></span>

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

<span data-ttu-id="47487-108">L’action est routable via `Product/ListAsync`.</span><span class="sxs-lookup"><span data-stu-id="47487-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="47487-109">La génération de liens requiert la spécification du suffixe `Async`.</span><span class="sxs-lookup"><span data-stu-id="47487-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="47487-110">Exemple :</span><span class="sxs-lookup"><span data-stu-id="47487-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="47487-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="47487-111">New behavior</span></span>

<span data-ttu-id="47487-112">Dans ASP.NET Core 3,0, l’action est routable via `Product/List`.</span><span class="sxs-lookup"><span data-stu-id="47487-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="47487-113">Le code de génération de lien doit omettre le suffixe `Async`.</span><span class="sxs-lookup"><span data-stu-id="47487-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="47487-114">Exemple :</span><span class="sxs-lookup"><span data-stu-id="47487-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="47487-115">Cette modification n’affecte pas les noms spécifiés à l’aide de l’attribut `[ActionName]`.</span><span class="sxs-lookup"><span data-stu-id="47487-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="47487-116">Le nouveau comportement peut être désactivé en définissant `MvcOptions.SuppressAsyncSuffixInActionNames` sur `false` dans `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="47487-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false; 
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="47487-117">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="47487-117">Reason for change</span></span>

<span data-ttu-id="47487-118">Par Convention, les méthodes .NET asynchrones sont suivies d’un suffixe `Async`.</span><span class="sxs-lookup"><span data-stu-id="47487-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="47487-119">Toutefois, lorsqu’une méthode définit une action MVC, il n’est pas souhaitable d’utiliser le suffixe `Async`.</span><span class="sxs-lookup"><span data-stu-id="47487-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="47487-120">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="47487-120">Recommended action</span></span>

<span data-ttu-id="47487-121">Si votre application dépend d’actions MVC conservant le suffixe `Async` du nom, choisissez l’une des solutions suivantes :</span><span class="sxs-lookup"><span data-stu-id="47487-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="47487-122">Utilisez l’attribut `[ActionName]` pour conserver le nom d’origine.</span><span class="sxs-lookup"><span data-stu-id="47487-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="47487-123">Désactivez entièrement l’attribution d’un nouveau nom en définissant `MvcOptions.SuppressAsyncSuffixInActionNames` sur `false` dans `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="47487-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false; 
});
```

#### <a name="category"></a><span data-ttu-id="47487-124">Category</span><span class="sxs-lookup"><span data-stu-id="47487-124">Category</span></span>

<span data-ttu-id="47487-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="47487-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="47487-126">API affectées</span><span class="sxs-lookup"><span data-stu-id="47487-126">Affected APIs</span></span>

<span data-ttu-id="47487-127">aucune.</span><span class="sxs-lookup"><span data-stu-id="47487-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
