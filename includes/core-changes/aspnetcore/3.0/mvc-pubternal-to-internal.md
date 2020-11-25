---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032615"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a><span data-ttu-id="efa49-101">MVC : les types « Pubternal » sont devenus internes</span><span class="sxs-lookup"><span data-stu-id="efa49-101">MVC: "Pubternal" types changed to internal</span></span>

<span data-ttu-id="efa49-102">Dans ASP.NET Core 3,0, tous les types « pubternal » dans MVC ont été mis à jour pour se trouver `public` dans un espace de noms pris en charge ou `internal` selon le cas.</span><span class="sxs-lookup"><span data-stu-id="efa49-102">In ASP.NET Core 3.0, all "pubternal" types in MVC were updated to either be `public` in a supported namespace or `internal` as appropriate.</span></span>

#### <a name="change-description"></a><span data-ttu-id="efa49-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="efa49-103">Change description</span></span>

<span data-ttu-id="efa49-104">Dans ASP.NET Core, les types « pubternal » sont déclarés comme, `public` mais résident dans un `.Internal` espace de noms avec suffixe.</span><span class="sxs-lookup"><span data-stu-id="efa49-104">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a `.Internal`-suffixed namespace.</span></span> <span data-ttu-id="efa49-105">Bien que ces types soient `public` , ils n’ont aucune stratégie de prise en charge et sont soumis à des modifications avec rupture.</span><span class="sxs-lookup"><span data-stu-id="efa49-105">While these types are `public`, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="efa49-106">Malheureusement, l’utilisation accidentelle de ces types est courante, entraînant des modifications avec rupture de ces projets et limitant la capacité à gérer l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="efa49-106">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="efa49-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="efa49-107">Version introduced</span></span>

<span data-ttu-id="efa49-108">3.0</span><span class="sxs-lookup"><span data-stu-id="efa49-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="efa49-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="efa49-109">Old behavior</span></span>

<span data-ttu-id="efa49-110">Certains types dans MVC étaient `public` , mais dans un `.Internal` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="efa49-110">Some types in MVC were `public` but in a `.Internal` namespace.</span></span> <span data-ttu-id="efa49-111">Ces types n’ont pas de stratégie de prise en charge et ont fait l’objet de modifications avec rupture.</span><span class="sxs-lookup"><span data-stu-id="efa49-111">These types had no support policy and were subject to breaking changes.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="efa49-112">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="efa49-112">New behavior</span></span>

<span data-ttu-id="efa49-113">Tous ces types sont mis à jour pour se trouver `public` dans un espace de noms pris en charge ou être marqués comme `internal` .</span><span class="sxs-lookup"><span data-stu-id="efa49-113">All such types are updated either to be `public` in a supported namespace or marked as `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="efa49-114">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="efa49-114">Reason for change</span></span>

<span data-ttu-id="efa49-115">L’utilisation accidentelle des types « pubternal » a été courante, entraînant des modifications avec rupture de ces projets et limitant la capacité à gérer l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="efa49-115">Accidental use of the "pubternal" types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="efa49-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="efa49-116">Recommended action</span></span>

<span data-ttu-id="efa49-117">Si vous utilisez des types qui ont été réellement `public` et qui ont été déplacés dans un nouvel espace de noms pris en charge, mettez à jour vos références pour qu’elles correspondent aux nouveaux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="efa49-117">If you're using types that have become truly `public` and have been moved into a new, supported namespace, update your references to match the new namespaces.</span></span>

<span data-ttu-id="efa49-118">Si vous utilisez des types qui ont été marqués comme `internal` , vous devez trouver une alternative.</span><span class="sxs-lookup"><span data-stu-id="efa49-118">If you're using types that have become marked as `internal`, you'll need to find an alternative.</span></span> <span data-ttu-id="efa49-119">Les types « pubternal » précédemment n’étaient jamais pris en charge pour une utilisation publique.</span><span class="sxs-lookup"><span data-stu-id="efa49-119">The previously "pubternal" types were never supported for public use.</span></span> <span data-ttu-id="efa49-120">S’il existe des types spécifiques dans ces espaces de noms qui sont essentiels à vos applications, émettez un problème dans [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="efa49-120">If there are specific types in these namespaces that are critical to your apps, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span> <span data-ttu-id="efa49-121">Des considérations peuvent être prises pour effectuer les types demandés `public` .</span><span class="sxs-lookup"><span data-stu-id="efa49-121">Considerations may be made for making the requested types `public`.</span></span>

#### <a name="category"></a><span data-ttu-id="efa49-122">Category</span><span class="sxs-lookup"><span data-stu-id="efa49-122">Category</span></span>

<span data-ttu-id="efa49-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="efa49-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="efa49-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="efa49-124">Affected APIs</span></span>

<span data-ttu-id="efa49-125">Cette modification comprend des types dans les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="efa49-125">This change includes types in the following namespaces:</span></span>

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
