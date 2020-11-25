---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032504"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a><span data-ttu-id="047a6-101">Hébergement : AspNetCoreModule v1 supprimé du bundle d’hébergement Windows</span><span class="sxs-lookup"><span data-stu-id="047a6-101">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>

<span data-ttu-id="047a6-102">À compter de ASP.NET Core 3,0, le bundle d’hébergement Windows ne contient pas AspNetCoreModule (ANCM) v1.</span><span class="sxs-lookup"><span data-stu-id="047a6-102">Starting with ASP.NET Core 3.0, the Windows Hosting Bundle won't contain AspNetCoreModule (ANCM) V1.</span></span>

<span data-ttu-id="047a6-103">ANCM V2 offre une compatibilité descendante avec ANCM OutOfProcess et il est recommandé de l’utiliser avec les applications ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="047a6-103">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="047a6-104">Pour plus d’informations, consultez [dotnet/aspnetcore # 7095](https://github.com/dotnet/aspnetcore/issues/7095).</span><span class="sxs-lookup"><span data-stu-id="047a6-104">For discussion, see [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="047a6-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="047a6-105">Version introduced</span></span>

<span data-ttu-id="047a6-106">3.0</span><span class="sxs-lookup"><span data-stu-id="047a6-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="047a6-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="047a6-107">Old behavior</span></span>

<span data-ttu-id="047a6-108">ANCM v1 est inclus dans le bundle d’hébergement Windows.</span><span class="sxs-lookup"><span data-stu-id="047a6-108">ANCM V1 is included in the Windows Hosting Bundle.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="047a6-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="047a6-109">New behavior</span></span>

<span data-ttu-id="047a6-110">ANCM v1 n’est pas inclus dans le bundle d’hébergement Windows.</span><span class="sxs-lookup"><span data-stu-id="047a6-110">ANCM V1 isn't included in the Windows Hosting Bundle.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="047a6-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="047a6-111">Reason for change</span></span>

<span data-ttu-id="047a6-112">ANCM V2 offre une compatibilité descendante avec ANCM OutOfProcess et il est recommandé de l’utiliser avec les applications ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="047a6-112">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="047a6-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="047a6-113">Recommended action</span></span>

<span data-ttu-id="047a6-114">Utilisez ANCM v2 avec les applications ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="047a6-114">Use ANCM V2 with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="047a6-115">Si ANCM v1 est requis, il peut être installé à l’aide de l’offre groupée d’hébergement Windows ASP.NET Core 2,1 ou 2,2.</span><span class="sxs-lookup"><span data-stu-id="047a6-115">If ANCM V1 is required, it can be installed using the ASP.NET Core 2.1 or 2.2 Windows Hosting Bundle.</span></span>

<span data-ttu-id="047a6-116">Cette modification s’interrompt ASP.NET Core applications 3,0 qui :</span><span class="sxs-lookup"><span data-stu-id="047a6-116">This change will break ASP.NET Core 3.0 apps that:</span></span>

- <span data-ttu-id="047a6-117">Optez explicitement pour l’utilisation de ANCM v1 avec `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>` .</span><span class="sxs-lookup"><span data-stu-id="047a6-117">Explicitly opted into using ANCM V1 with `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span></span>
- <span data-ttu-id="047a6-118">Avoir un fichier de *web.config* personnalisé avec `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />` .</span><span class="sxs-lookup"><span data-stu-id="047a6-118">Have a custom *web.config* file with `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span></span>

#### <a name="category"></a><span data-ttu-id="047a6-119">Category</span><span class="sxs-lookup"><span data-stu-id="047a6-119">Category</span></span>

<span data-ttu-id="047a6-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="047a6-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="047a6-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="047a6-121">Affected APIs</span></span>

<span data-ttu-id="047a6-122">None</span><span class="sxs-lookup"><span data-stu-id="047a6-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
