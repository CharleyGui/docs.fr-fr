---
ms.openlocfilehash: c4e7864262a11aafa4b7f1f4bdf632fbf084c560
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507078"
---
### <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a><span data-ttu-id="fdf18-101">HTTP : Kestrel et les types de BadHttpRequestException IIS marqués comme obsolètes et remplacés</span><span class="sxs-lookup"><span data-stu-id="fdf18-101">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>

<span data-ttu-id="fdf18-102">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`et `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` ont été marqués comme obsolètes et ont été modifiés pour dériver de `Microsoft.AspNetCore.Http.BadHttpRequestException` .</span><span class="sxs-lookup"><span data-stu-id="fdf18-102">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` have been marked obsolete and changed to derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span> <span data-ttu-id="fdf18-103">Les serveurs Kestrel et IIS lèvent toujours leurs anciens types d’exception à des fins de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="fdf18-103">The Kestrel and IIS servers still throw their old exception types for backwards compatibility.</span></span> <span data-ttu-id="fdf18-104">Les types obsolètes seront supprimés dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="fdf18-104">The obsolete types will be removed in a future release.</span></span>

<span data-ttu-id="fdf18-105">Pour plus d’informations, consultez [dotnet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614).</span><span class="sxs-lookup"><span data-stu-id="fdf18-105">For discussion, see [dotnet/aspnetcore#20614](https://github.com/dotnet/aspnetcore/issues/20614).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fdf18-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="fdf18-106">Version introduced</span></span>

<span data-ttu-id="fdf18-107">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="fdf18-107">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="fdf18-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="fdf18-108">Old behavior</span></span>

<span data-ttu-id="fdf18-109">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`et `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` dérivées de <xref:System.IO.IOException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fdf18-109">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` derived from <xref:System.IO.IOException?displayProperty=nameWithType>.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="fdf18-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="fdf18-110">New behavior</span></span>

<span data-ttu-id="fdf18-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`et `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` sont obsolètes.</span><span class="sxs-lookup"><span data-stu-id="fdf18-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` are obsolete.</span></span> <span data-ttu-id="fdf18-112">Les types dérivent également de `Microsoft.AspNetCore.Http.BadHttpRequestException` , qui dérive de `System.IO.IOException` .</span><span class="sxs-lookup"><span data-stu-id="fdf18-112">The types also derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`, which derives from `System.IO.IOException`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fdf18-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="fdf18-113">Reason for change</span></span>

<span data-ttu-id="fdf18-114">La modification a été apportée à :</span><span class="sxs-lookup"><span data-stu-id="fdf18-114">The change was made to:</span></span>

* <span data-ttu-id="fdf18-115">Consolidez les types dupliqués.</span><span class="sxs-lookup"><span data-stu-id="fdf18-115">Consolidate duplicate types.</span></span>
* <span data-ttu-id="fdf18-116">Unifiez le comportement entre les implémentations de serveur.</span><span class="sxs-lookup"><span data-stu-id="fdf18-116">Unify behavior across server implementations.</span></span>

<span data-ttu-id="fdf18-117">Une application peut maintenant intercepter l’exception de base `Microsoft.AspNetCore.Http.BadHttpRequestException` lors de l’utilisation de Kestrel ou IIS.</span><span class="sxs-lookup"><span data-stu-id="fdf18-117">An app can now catch the base exception `Microsoft.AspNetCore.Http.BadHttpRequestException` when using either Kestrel or IIS.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fdf18-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="fdf18-118">Recommended action</span></span>

<span data-ttu-id="fdf18-119">Remplacer les utilisations de `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` et de `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` par `Microsoft.AspNetCore.Http.BadHttpRequestException` .</span><span class="sxs-lookup"><span data-stu-id="fdf18-119">Replace usages of `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` with `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span>

#### <a name="category"></a><span data-ttu-id="fdf18-120">Category</span><span class="sxs-lookup"><span data-stu-id="fdf18-120">Category</span></span>

<span data-ttu-id="fdf18-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fdf18-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fdf18-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="fdf18-122">Affected APIs</span></span>

- [<span data-ttu-id="fdf18-123">Microsoft. AspNetCore. Server. IIS. BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="fdf18-123">Microsoft.AspNetCore.Server.IIS.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [<span data-ttu-id="fdf18-124">Microsoft. AspNetCore. Server. Kestrel. BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="fdf18-124">Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
