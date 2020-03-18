---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901591"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a><span data-ttu-id="9fc35-101">MVC: "Pubternal" types changés à interne</span><span class="sxs-lookup"><span data-stu-id="9fc35-101">MVC: "Pubternal" types changed to internal</span></span>

<span data-ttu-id="9fc35-102">Dans ASP.NET Core 3.0, tous les types de « pubternal `public` » dans MVC `internal` ont été mis à jour pour être soit dans un espace de nom pris en charge ou, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="9fc35-102">In ASP.NET Core 3.0, all "pubternal" types in MVC were updated to either be `public` in a supported namespace or `internal` as appropriate.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9fc35-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="9fc35-103">Change description</span></span>

<span data-ttu-id="9fc35-104">Dans ASP.NET Core, les types "pubternal" `public` sont déclarés comme étant sauf dans un `.Internal`espace noméxé.</span><span class="sxs-lookup"><span data-stu-id="9fc35-104">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a `.Internal`-suffixed namespace.</span></span> <span data-ttu-id="9fc35-105">Bien que `public`ces types sont , ils n’ont pas de politique de soutien et sont sujets à des changements de rupture.</span><span class="sxs-lookup"><span data-stu-id="9fc35-105">While these types are `public`, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="9fc35-106">Malheureusement, l’utilisation accidentelle de ces types a été courante, ce qui a entraîné la rupture des changements à ces projets et la limitation de la capacité de maintenir le cadre.</span><span class="sxs-lookup"><span data-stu-id="9fc35-106">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9fc35-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="9fc35-107">Version introduced</span></span>

<span data-ttu-id="9fc35-108">3.0</span><span class="sxs-lookup"><span data-stu-id="9fc35-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9fc35-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="9fc35-109">Old behavior</span></span>

<span data-ttu-id="9fc35-110">Certains types dans `public` MVC `.Internal` étaient, mais dans un namespace.</span><span class="sxs-lookup"><span data-stu-id="9fc35-110">Some types in MVC were `public` but in a `.Internal` namespace.</span></span> <span data-ttu-id="9fc35-111">Ces types n’avaient pas de politique de soutien et étaient susceptibles de modifier en cassant.</span><span class="sxs-lookup"><span data-stu-id="9fc35-111">These types had no support policy and were subject to breaking changes.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9fc35-112">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="9fc35-112">New behavior</span></span>

<span data-ttu-id="9fc35-113">Tous ces types sont `public` mis à jour soit `internal`pour être dans un namespace pris en charge ou marqué comme .</span><span class="sxs-lookup"><span data-stu-id="9fc35-113">All such types are updated either to be `public` in a supported namespace or marked as `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9fc35-114">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="9fc35-114">Reason for change</span></span>

<span data-ttu-id="9fc35-115">L’utilisation accidentelle des types « pubtérinaux » a été courante, ce qui a entraîné la rupture des changements à ces projets et la limitation de la capacité de maintenir le cadre.</span><span class="sxs-lookup"><span data-stu-id="9fc35-115">Accidental use of the "pubternal" types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9fc35-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="9fc35-116">Recommended action</span></span>

<span data-ttu-id="9fc35-117">Si vous utilisez des types `public` qui sont devenus vraiment et ont été déplacés dans un nouvel espace de nom pris en charge, mettez à jour vos références pour correspondre aux nouveaux espaces de nom.</span><span class="sxs-lookup"><span data-stu-id="9fc35-117">If you're using types that have become truly `public` and have been moved into a new, supported namespace, update your references to match the new namespaces.</span></span>

<span data-ttu-id="9fc35-118">Si vous utilisez des types qui `internal`sont devenus marqués comme , vous aurez besoin de trouver une alternative.</span><span class="sxs-lookup"><span data-stu-id="9fc35-118">If you're using types that have become marked as `internal`, you'll need to find an alternative.</span></span> <span data-ttu-id="9fc35-119">Les types auparavant «pubternal» n’ont jamais été pris en charge pour un usage public.</span><span class="sxs-lookup"><span data-stu-id="9fc35-119">The previously "pubternal" types were never supported for public use.</span></span> <span data-ttu-id="9fc35-120">S’il existe des types spécifiques dans ces espaces nominaux qui sont essentiels à vos applications, déposez un problème à [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="9fc35-120">If there are specific types in these namespaces that are critical to your apps, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span> <span data-ttu-id="9fc35-121">Des considérations peuvent être prises `public`pour faire les types demandés .</span><span class="sxs-lookup"><span data-stu-id="9fc35-121">Considerations may be made for making the requested types `public`.</span></span>

#### <a name="category"></a><span data-ttu-id="9fc35-122">Category</span><span class="sxs-lookup"><span data-stu-id="9fc35-122">Category</span></span>

<span data-ttu-id="9fc35-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9fc35-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9fc35-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="9fc35-124">Affected APIs</span></span>

<span data-ttu-id="9fc35-125">Ce changement inclut les types dans les espaces nominaux suivants :</span><span class="sxs-lookup"><span data-stu-id="9fc35-125">This change includes types in the following namespaces:</span></span>

- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

-->
