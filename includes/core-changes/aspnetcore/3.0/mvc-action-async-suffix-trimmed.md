---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901803"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="56f84-101">MVC : suffixe Async tronqué à partir des noms d’action du contrôleur</span><span class="sxs-lookup"><span data-stu-id="56f84-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="56f84-102">Dans le cadre de l’adressage [dotnet/aspnetcore # 4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.net Core MVC supprime le `Async` suffixe des noms d’action par défaut.</span><span class="sxs-lookup"><span data-stu-id="56f84-102">As part of addressing [dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="56f84-103">À compter de ASP.NET Core 3,0, cette modification affecte à la fois le routage et la génération de liens.</span><span class="sxs-lookup"><span data-stu-id="56f84-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="56f84-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="56f84-104">Version introduced</span></span>

<span data-ttu-id="56f84-105">3.0</span><span class="sxs-lookup"><span data-stu-id="56f84-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="56f84-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="56f84-106">Old behavior</span></span>

<span data-ttu-id="56f84-107">Considérez les ASP.NET Core contrôleur MVC suivants :</span><span class="sxs-lookup"><span data-stu-id="56f84-107">Consider the following ASP.NET Core MVC controller:</span></span>

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

<span data-ttu-id="56f84-108">L’action peut être routable `Product/ListAsync`via.</span><span class="sxs-lookup"><span data-stu-id="56f84-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="56f84-109">La génération de liens requiert `Async` la spécification du suffixe.</span><span class="sxs-lookup"><span data-stu-id="56f84-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="56f84-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="56f84-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="56f84-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="56f84-111">New behavior</span></span>

<span data-ttu-id="56f84-112">Dans ASP.NET Core 3,0, l’action est routable via `Product/List`.</span><span class="sxs-lookup"><span data-stu-id="56f84-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="56f84-113">Le code de génération de lien `Async` doit omettre le suffixe.</span><span class="sxs-lookup"><span data-stu-id="56f84-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="56f84-114">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="56f84-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="56f84-115">Cette modification n’affecte pas les noms spécifiés à l’aide de l' `[ActionName]` attribut.</span><span class="sxs-lookup"><span data-stu-id="56f84-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="56f84-116">Le nouveau comportement peut être désactivé en affectant `false` à `Startup.ConfigureServices`la valeur `MvcOptions.SuppressAsyncSuffixInActionNames` dans :</span><span class="sxs-lookup"><span data-stu-id="56f84-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="56f84-117">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="56f84-117">Reason for change</span></span>

<span data-ttu-id="56f84-118">Par Convention, les méthodes .NET asynchrones sont suivies d' `Async`un suffixe.</span><span class="sxs-lookup"><span data-stu-id="56f84-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="56f84-119">Toutefois, lorsqu’une méthode définit une action MVC, il n’est pas souhaitable d’utiliser `Async` le suffixe.</span><span class="sxs-lookup"><span data-stu-id="56f84-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="56f84-120">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="56f84-120">Recommended action</span></span>

<span data-ttu-id="56f84-121">Si votre application dépend d’actions MVC qui conservent le `Async` suffixe du nom, choisissez l’une des solutions de contournement suivantes :</span><span class="sxs-lookup"><span data-stu-id="56f84-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="56f84-122">Utilisez l' `[ActionName]` attribut pour conserver le nom d’origine.</span><span class="sxs-lookup"><span data-stu-id="56f84-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="56f84-123">Désactivez entièrement le changement de `MvcOptions.SuppressAsyncSuffixInActionNames` nom `false` en `Startup.ConfigureServices`définissant sur dans :</span><span class="sxs-lookup"><span data-stu-id="56f84-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a><span data-ttu-id="56f84-124">Category</span><span class="sxs-lookup"><span data-stu-id="56f84-124">Category</span></span>

<span data-ttu-id="56f84-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="56f84-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="56f84-126">API affectées</span><span class="sxs-lookup"><span data-stu-id="56f84-126">Affected APIs</span></span>

<span data-ttu-id="56f84-127">Aucun</span><span class="sxs-lookup"><span data-stu-id="56f84-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
