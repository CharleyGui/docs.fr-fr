---
ms.openlocfilehash: 41e80a9dbcfa2a857e0b52674ef0724a542458a0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539469"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a><span data-ttu-id="5a85e-101">Localisation : classe ResourceManagerWithCultureStringLocalizer et membre d’interface WithCulture supprimé</span><span class="sxs-lookup"><span data-stu-id="5a85e-101">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>

<span data-ttu-id="5a85e-102">La classe [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) et la méthode [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) ont été supprimées dans .net 5,0 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="5a85e-102">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were removed in .NET 5.0 Preview 1.</span></span>

<span data-ttu-id="5a85e-103">Pour le contexte, consultez [ASPNET/announcements # 346](https://github.com/aspnet/Announcements/issues/346) et [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="5a85e-103">For context, see [aspnet/Announcements#346](https://github.com/aspnet/Announcements/issues/346) and [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="5a85e-104">Pour plus d’informations sur cette modification, consultez [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="5a85e-104">For discussion on this change, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5a85e-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="5a85e-105">Version introduced</span></span>

<span data-ttu-id="5a85e-106">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="5a85e-106">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5a85e-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="5a85e-107">Old behavior</span></span>

<span data-ttu-id="5a85e-108">La `ResourceManagerWithCultureStringLocalizer` classe et la `ResourceManagerStringLocalizer.WithCulture` méthode sont [obsolètes dans .net Core 3,0 Preview 3 et versions ultérieures](../../../../docs/core/compatibility/2.2-3.0.md#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span><span class="sxs-lookup"><span data-stu-id="5a85e-108">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method are [obsolete in .NET Core 3.0 Preview 3 and later](../../../../docs/core/compatibility/2.2-3.0.md#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5a85e-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="5a85e-109">New behavior</span></span>

<span data-ttu-id="5a85e-110">La `ResourceManagerWithCultureStringLocalizer` classe et la `ResourceManagerStringLocalizer.WithCulture` méthode ont été supprimées dans .net 5,0 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="5a85e-110">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method have been removed in .NET 5.0 Preview 1.</span></span> <span data-ttu-id="5a85e-111">Pour obtenir un inventaire des modifications apportées, consultez la demande de tirage (pull request) à l’adresse [dotnet/extensions # 2562](https://github.com/dotnet/extensions/pull/2562/files).</span><span class="sxs-lookup"><span data-stu-id="5a85e-111">For an inventory of the changes made, see the pull request at [dotnet/extensions#2562](https://github.com/dotnet/extensions/pull/2562/files).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5a85e-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="5a85e-112">Reason for change</span></span>

<span data-ttu-id="5a85e-113">La classe [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) et la méthode [ResourceManagerStringLocalizer. WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) étaient souvent des sources de confusion pour les utilisateurs de la localisation.</span><span class="sxs-lookup"><span data-stu-id="5a85e-113">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were often sources of confusion for users of localization.</span></span> <span data-ttu-id="5a85e-114">La confusion était particulièrement élevée lors de la création d’une <xref:Microsoft.Extensions.Localization.IStringLocalizer> implémentation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="5a85e-114">The confusion was especially high when creating a custom <xref:Microsoft.Extensions.Localization.IStringLocalizer> implementation.</span></span> <span data-ttu-id="5a85e-115">Cette classe et cette méthode donnent aux consommateurs l’impression qu’une `IStringLocalizer` instance est supposée être « par langue, par ressource ».</span><span class="sxs-lookup"><span data-stu-id="5a85e-115">This class and method give consumers the impression that an `IStringLocalizer` instance is expected to be "per-language, per-resource".</span></span> <span data-ttu-id="5a85e-116">En réalité, l’instance doit uniquement être « par ressource ».</span><span class="sxs-lookup"><span data-stu-id="5a85e-116">In reality, the instance should only be "per-resource".</span></span> <span data-ttu-id="5a85e-117">Au moment de l’exécution, la <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> propriété détermine la langue à utiliser.</span><span class="sxs-lookup"><span data-stu-id="5a85e-117">At run time, the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> property determines the language to be used.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5a85e-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="5a85e-118">Recommended action</span></span>

<span data-ttu-id="5a85e-119">Arrêtez l’utilisation de la `ResourceManagerWithCultureStringLocalizer` classe et de la `ResourceManagerStringLocalizer.WithCulture` méthode.</span><span class="sxs-lookup"><span data-stu-id="5a85e-119">Stop using the `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method.</span></span>

#### <a name="category"></a><span data-ttu-id="5a85e-120">Category</span><span class="sxs-lookup"><span data-stu-id="5a85e-120">Category</span></span>

<span data-ttu-id="5a85e-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5a85e-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5a85e-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="5a85e-122">Affected APIs</span></span>

- [<span data-ttu-id="5a85e-123">ResourceManagerWithCultureStringLocalizer</span><span class="sxs-lookup"><span data-stu-id="5a85e-123">ResourceManagerWithCultureStringLocalizer</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [<span data-ttu-id="5a85e-124">ResourceManagerStringLocalizer.WithCulture</span><span class="sxs-lookup"><span data-stu-id="5a85e-124">ResourceManagerStringLocalizer.WithCulture</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
