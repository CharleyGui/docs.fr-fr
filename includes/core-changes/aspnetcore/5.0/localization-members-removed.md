---
ms.openlocfilehash: 6deeb7debce9b731f3871b7de0ad8df8a8cdafea
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728285"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a><span data-ttu-id="31c52-101">Localisation : classe ResourceManagerWithCultureStringLocalizer et membre d’interface WithCulture supprimé</span><span class="sxs-lookup"><span data-stu-id="31c52-101">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>

<span data-ttu-id="31c52-102">La classe [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) et la méthode [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) ont été supprimées dans .net 5,0 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="31c52-102">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were removed in .NET 5.0 Preview 1.</span></span>

<span data-ttu-id="31c52-103">Pour le contexte, consultez [ASPNET/announcements # 346](https://github.com/aspnet/Announcements/issues/346) et [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="31c52-103">For context, see [aspnet/Announcements#346](https://github.com/aspnet/Announcements/issues/346) and [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="31c52-104">Pour plus d’informations sur cette modification, consultez [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="31c52-104">For discussion on this change, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="31c52-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="31c52-105">Version introduced</span></span>

<span data-ttu-id="31c52-106">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="31c52-106">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="31c52-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="31c52-107">Old behavior</span></span>

<span data-ttu-id="31c52-108">La `ResourceManagerWithCultureStringLocalizer` classe et la `ResourceManagerStringLocalizer.WithCulture` méthode sont [obsolètes dans .net Core 3,0 Preview 3 et versions ultérieures](/dotnet/core/compatibility/2.2-3.0#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span><span class="sxs-lookup"><span data-stu-id="31c52-108">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method are [obsolete in .NET Core 3.0 Preview 3 and later](/dotnet/core/compatibility/2.2-3.0#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="31c52-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="31c52-109">New behavior</span></span>

<span data-ttu-id="31c52-110">La `ResourceManagerWithCultureStringLocalizer` classe et la `ResourceManagerStringLocalizer.WithCulture` méthode ont été supprimées dans .net 5,0 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="31c52-110">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method have been removed in .NET 5.0 Preview 1.</span></span> <span data-ttu-id="31c52-111">Pour obtenir un inventaire des modifications apportées, consultez la demande de tirage (pull request) à l’adresse [dotnet/extensions # 2562](https://github.com/dotnet/extensions/pull/2562/files).</span><span class="sxs-lookup"><span data-stu-id="31c52-111">For an inventory of the changes made, see the pull request at [dotnet/extensions#2562](https://github.com/dotnet/extensions/pull/2562/files).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="31c52-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="31c52-112">Reason for change</span></span>

<span data-ttu-id="31c52-113">La classe [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) et la méthode [ResourceManagerStringLocalizer. WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) étaient souvent des sources de confusion pour les utilisateurs de la localisation.</span><span class="sxs-lookup"><span data-stu-id="31c52-113">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were often sources of confusion for users of localization.</span></span> <span data-ttu-id="31c52-114">La confusion était particulièrement élevée lors de la création d’une <xref:Microsoft.Extensions.Localization.IStringLocalizer> implémentation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="31c52-114">The confusion was especially high when creating a custom <xref:Microsoft.Extensions.Localization.IStringLocalizer> implementation.</span></span> <span data-ttu-id="31c52-115">Cette classe et cette méthode donnent aux consommateurs l’impression qu’une `IStringLocalizer` instance est supposée être « par langue, par ressource ».</span><span class="sxs-lookup"><span data-stu-id="31c52-115">This class and method give consumers the impression that an `IStringLocalizer` instance is expected to be "per-language, per-resource".</span></span> <span data-ttu-id="31c52-116">En réalité, l’instance doit uniquement être « par ressource ».</span><span class="sxs-lookup"><span data-stu-id="31c52-116">In reality, the instance should only be "per-resource".</span></span> <span data-ttu-id="31c52-117">Au moment de l’exécution, la <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> propriété détermine la langue à utiliser.</span><span class="sxs-lookup"><span data-stu-id="31c52-117">At run time, the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> property determines the language to be used.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="31c52-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="31c52-118">Recommended action</span></span>

<span data-ttu-id="31c52-119">Arrêtez l’utilisation de la `ResourceManagerWithCultureStringLocalizer` classe et de la `ResourceManagerStringLocalizer.WithCulture` méthode.</span><span class="sxs-lookup"><span data-stu-id="31c52-119">Stop using the `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method.</span></span>

#### <a name="category"></a><span data-ttu-id="31c52-120">Category</span><span class="sxs-lookup"><span data-stu-id="31c52-120">Category</span></span>

<span data-ttu-id="31c52-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="31c52-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="31c52-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="31c52-122">Affected APIs</span></span>

- [<span data-ttu-id="31c52-123">ResourceManagerWithCultureStringLocalizer</span><span class="sxs-lookup"><span data-stu-id="31c52-123">ResourceManagerWithCultureStringLocalizer</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [<span data-ttu-id="31c52-124">ResourceManagerStringLocalizer.WithCulture</span><span class="sxs-lookup"><span data-stu-id="31c52-124">ResourceManagerStringLocalizer.WithCulture</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
