---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901959"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a><span data-ttu-id="1cd4d-101">Hébergement: AspNetCoreModule V1 supprimé de Windows Hosting Bundle</span><span class="sxs-lookup"><span data-stu-id="1cd4d-101">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>

<span data-ttu-id="1cd4d-102">En commençant par ASP.NET Core 3.0, le Windows Hosting Bundle ne contiendra pas aspNetCoreModule (ANCM) V1.</span><span class="sxs-lookup"><span data-stu-id="1cd4d-102">Starting with ASP.NET Core 3.0, the Windows Hosting Bundle won't contain AspNetCoreModule (ANCM) V1.</span></span>

<span data-ttu-id="1cd4d-103">ANCM V2 est compatible vers l’arrière avec ANCM OutOfProcess et est recommandé pour une utilisation avec ASP.NET applications Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="1cd4d-103">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="1cd4d-104">Pour discussion, voir [dotnet/aspnetcore 7095](https://github.com/dotnet/aspnetcore/issues/7095).</span><span class="sxs-lookup"><span data-stu-id="1cd4d-104">For discussion, see [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1cd4d-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="1cd4d-105">Version introduced</span></span>

<span data-ttu-id="1cd4d-106">3.0</span><span class="sxs-lookup"><span data-stu-id="1cd4d-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1cd4d-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="1cd4d-107">Old behavior</span></span>

<span data-ttu-id="1cd4d-108">ANCM V1 est inclus dans le Windows Hosting Bundle.</span><span class="sxs-lookup"><span data-stu-id="1cd4d-108">ANCM V1 is included in the Windows Hosting Bundle.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1cd4d-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="1cd4d-109">New behavior</span></span>

<span data-ttu-id="1cd4d-110">ANCM V1 n’est pas inclus dans le Windows Hosting Bundle.</span><span class="sxs-lookup"><span data-stu-id="1cd4d-110">ANCM V1 isn't included in the Windows Hosting Bundle.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1cd4d-111">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="1cd4d-111">Reason for change</span></span>

<span data-ttu-id="1cd4d-112">ANCM V2 est compatible vers l’arrière avec ANCM OutOfProcess et est recommandé pour une utilisation avec ASP.NET applications Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="1cd4d-112">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1cd4d-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="1cd4d-113">Recommended action</span></span>

<span data-ttu-id="1cd4d-114">Utilisez ANCM V2 avec ASP.NET applications Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="1cd4d-114">Use ANCM V2 with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="1cd4d-115">Si ANCM V1 est nécessaire, il peut être installé à l’aide du ASP.NET Core 2.1 ou 2.2 Windows Hosting Bundle.</span><span class="sxs-lookup"><span data-stu-id="1cd4d-115">If ANCM V1 is required, it can be installed using the ASP.NET Core 2.1 or 2.2 Windows Hosting Bundle.</span></span>

<span data-ttu-id="1cd4d-116">Ce changement va briser ASP.NET applications Core 3.0 qui:</span><span class="sxs-lookup"><span data-stu-id="1cd4d-116">This change will break ASP.NET Core 3.0 apps that:</span></span>

- <span data-ttu-id="1cd4d-117">Explicitement choisi d’utiliser ANCM V1 avec `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span><span class="sxs-lookup"><span data-stu-id="1cd4d-117">Explicitly opted into using ANCM V1 with `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span></span>
- <span data-ttu-id="1cd4d-118">Avoir un fichier *web.config* personnalisé avec `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span><span class="sxs-lookup"><span data-stu-id="1cd4d-118">Have a custom *web.config* file with `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span></span>

#### <a name="category"></a><span data-ttu-id="1cd4d-119">Category</span><span class="sxs-lookup"><span data-stu-id="1cd4d-119">Category</span></span>

<span data-ttu-id="1cd4d-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1cd4d-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1cd4d-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="1cd4d-121">Affected APIs</span></span>

<span data-ttu-id="1cd4d-122">None</span><span class="sxs-lookup"><span data-stu-id="1cd4d-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
