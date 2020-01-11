---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901703"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a><span data-ttu-id="dab59-101">Localisation : ResourceManagerWithCultureStringLocalizer et WithCulture marqués comme obsolètes</span><span class="sxs-lookup"><span data-stu-id="dab59-101">Localization: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete</span></span>

<span data-ttu-id="dab59-102">La classe [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) et le membre d’interface [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) sont souvent des sources de confusion pour les utilisateurs de localisation, en particulier lors de la création de leur propre implémentation de `IStringLocalizer`.</span><span class="sxs-lookup"><span data-stu-id="dab59-102">The [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) class and [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) interface member are often sources of confusion for users of localization, especially when creating their own `IStringLocalizer` implementation.</span></span> <span data-ttu-id="dab59-103">Ces éléments donnent à l’utilisateur l’impression qu’une `IStringLocalizer` instance est « par langue, par ressource ».</span><span class="sxs-lookup"><span data-stu-id="dab59-103">These items give the user the impression that an `IStringLocalizer` instance is "per-language, per-resource".</span></span> <span data-ttu-id="dab59-104">En réalité, les instances doivent uniquement être « par ressource ».</span><span class="sxs-lookup"><span data-stu-id="dab59-104">In reality, the instances should only be "per-resource".</span></span> <span data-ttu-id="dab59-105">La langue recherchée est déterminée par la `CultureInfo.CurrentUICulture` au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="dab59-105">The language searched for is determined by the `CultureInfo.CurrentUICulture` at execution time.</span></span> <span data-ttu-id="dab59-106">Pour éliminer la source de confusion, les API ont été marquées comme obsolètes dans ASP.NET Core 3,0 Preview 3.</span><span class="sxs-lookup"><span data-stu-id="dab59-106">To eliminate the source of confusion, the APIs were marked as obsolete in ASP.NET Core 3.0 Preview 3.</span></span> <span data-ttu-id="dab59-107">Les API seront supprimées dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="dab59-107">The APIs will be removed in a future release.</span></span>

<span data-ttu-id="dab59-108">Pour le contexte, consultez [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="dab59-108">For context, see [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="dab59-109">Pour plus d’informations, consultez [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="dab59-109">For discussion, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dab59-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="dab59-110">Version introduced</span></span>

<span data-ttu-id="dab59-111">3.0</span><span class="sxs-lookup"><span data-stu-id="dab59-111">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="dab59-112">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="dab59-112">Old behavior</span></span>

<span data-ttu-id="dab59-113">Les méthodes n’ont pas été marquées comme `Obsolete`.</span><span class="sxs-lookup"><span data-stu-id="dab59-113">Methods weren't marked as `Obsolete`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="dab59-114">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="dab59-114">New behavior</span></span>

<span data-ttu-id="dab59-115">Les méthodes sont marquées `Obsolete`.</span><span class="sxs-lookup"><span data-stu-id="dab59-115">Methods are marked `Obsolete`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="dab59-116">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="dab59-116">Reason for change</span></span>

<span data-ttu-id="dab59-117">Les API représentaient un cas d’usage qui n’est pas recommandé.</span><span class="sxs-lookup"><span data-stu-id="dab59-117">The APIs represented a use case that isn't recommended.</span></span> <span data-ttu-id="dab59-118">Il y a eu une confusion concernant la conception de la localisation.</span><span class="sxs-lookup"><span data-stu-id="dab59-118">There was confusion about the design of localization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dab59-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="dab59-119">Recommended action</span></span>

<span data-ttu-id="dab59-120">La recommandation consiste à utiliser `ResourceManagerStringLocalizer` à la place.</span><span class="sxs-lookup"><span data-stu-id="dab59-120">The recommendation is to use `ResourceManagerStringLocalizer` instead.</span></span> <span data-ttu-id="dab59-121">Laissez la culture définie par l' `CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="dab59-121">Let the culture be set by the `CurrentCulture`.</span></span> <span data-ttu-id="dab59-122">Si ce n’est pas une option, créez et utilisez une copie de [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span><span class="sxs-lookup"><span data-stu-id="dab59-122">If that isn't an option, create and use a copy of [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span></span>

#### <a name="category"></a><span data-ttu-id="dab59-123">Catégorie</span><span class="sxs-lookup"><span data-stu-id="dab59-123">Category</span></span>

<span data-ttu-id="dab59-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dab59-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dab59-125">API affectées</span><span class="sxs-lookup"><span data-stu-id="dab59-125">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
