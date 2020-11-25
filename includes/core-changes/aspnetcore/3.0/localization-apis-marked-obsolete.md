---
ms.openlocfilehash: d70a8d2a3031a5b3d47ab3fb7f40193dce6e311e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032595"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a><span data-ttu-id="ef140-101">Localisation : ResourceManagerWithCultureStringLocalizer et WithCulture marqués comme obsolètes</span><span class="sxs-lookup"><span data-stu-id="ef140-101">Localization: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete</span></span>

<span data-ttu-id="ef140-102">La classe [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) et le membre d’interface [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) sont souvent des sources de confusion pour les utilisateurs de localisation, en particulier lors de la création de leur propre `IStringLocalizer` implémentation.</span><span class="sxs-lookup"><span data-stu-id="ef140-102">The [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) class and [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) interface member are often sources of confusion for users of localization, especially when creating their own `IStringLocalizer` implementation.</span></span> <span data-ttu-id="ef140-103">Ces éléments donnent à l’utilisateur l’impression qu’une `IStringLocalizer` instance est « par langue, par ressource ».</span><span class="sxs-lookup"><span data-stu-id="ef140-103">These items give the user the impression that an `IStringLocalizer` instance is "per-language, per-resource".</span></span> <span data-ttu-id="ef140-104">En réalité, les instances doivent uniquement être « par ressource ».</span><span class="sxs-lookup"><span data-stu-id="ef140-104">In reality, the instances should only be "per-resource".</span></span> <span data-ttu-id="ef140-105">La langue recherchée est déterminée par le `CultureInfo.CurrentUICulture` au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ef140-105">The language searched for is determined by the `CultureInfo.CurrentUICulture` at execution time.</span></span> <span data-ttu-id="ef140-106">Pour éliminer la source de confusion, les API ont été marquées comme obsolètes dans ASP.NET Core 3,0 Preview 3.</span><span class="sxs-lookup"><span data-stu-id="ef140-106">To eliminate the source of confusion, the APIs were marked as obsolete in ASP.NET Core 3.0 Preview 3.</span></span> <span data-ttu-id="ef140-107">Les API seront supprimées dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="ef140-107">The APIs will be removed in a future release.</span></span>

<span data-ttu-id="ef140-108">Pour le contexte, consultez [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="ef140-108">For context, see [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="ef140-109">Pour plus d’informations, consultez [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="ef140-109">For discussion, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ef140-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ef140-110">Version introduced</span></span>

<span data-ttu-id="ef140-111">3.0</span><span class="sxs-lookup"><span data-stu-id="ef140-111">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ef140-112">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="ef140-112">Old behavior</span></span>

<span data-ttu-id="ef140-113">Les méthodes n’ont pas été marquées comme `Obsolete` .</span><span class="sxs-lookup"><span data-stu-id="ef140-113">Methods weren't marked as `Obsolete`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ef140-114">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="ef140-114">New behavior</span></span>

<span data-ttu-id="ef140-115">Les méthodes sont marquées `Obsolete` .</span><span class="sxs-lookup"><span data-stu-id="ef140-115">Methods are marked `Obsolete`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ef140-116">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="ef140-116">Reason for change</span></span>

<span data-ttu-id="ef140-117">Les API représentaient un cas d’usage qui n’est pas recommandé.</span><span class="sxs-lookup"><span data-stu-id="ef140-117">The APIs represented a use case that isn't recommended.</span></span> <span data-ttu-id="ef140-118">Il y a eu une confusion concernant la conception de la localisation.</span><span class="sxs-lookup"><span data-stu-id="ef140-118">There was confusion about the design of localization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ef140-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="ef140-119">Recommended action</span></span>

<span data-ttu-id="ef140-120">Il est recommandé d’utiliser à la `ResourceManagerStringLocalizer` place.</span><span class="sxs-lookup"><span data-stu-id="ef140-120">The recommendation is to use `ResourceManagerStringLocalizer` instead.</span></span> <span data-ttu-id="ef140-121">Laissez la culture définie par `CurrentCulture` .</span><span class="sxs-lookup"><span data-stu-id="ef140-121">Let the culture be set by the `CurrentCulture`.</span></span> <span data-ttu-id="ef140-122">Si ce n’est pas une option, créez et utilisez une copie de [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span><span class="sxs-lookup"><span data-stu-id="ef140-122">If that isn't an option, create and use a copy of [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span></span>

#### <a name="category"></a><span data-ttu-id="ef140-123">Category</span><span class="sxs-lookup"><span data-stu-id="ef140-123">Category</span></span>

<span data-ttu-id="ef140-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ef140-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ef140-125">API affectées</span><span class="sxs-lookup"><span data-stu-id="ef140-125">Affected APIs</span></span>

- [<span data-ttu-id="ef140-126">ResourceManagerWithCultureStringLocalizer</span><span class="sxs-lookup"><span data-stu-id="ef140-126">ResourceManagerWithCultureStringLocalizer</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.0)
- [<span data-ttu-id="ef140-127">ResourceManagerStringLocalizer.WithCulture</span><span class="sxs-lookup"><span data-stu-id="ef140-127">ResourceManagerStringLocalizer.WithCulture</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.0)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
