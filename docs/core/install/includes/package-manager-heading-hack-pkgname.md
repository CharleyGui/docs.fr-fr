---
ms.openlocfilehash: ab1006f706439bcf5129854da3d14538e5b690a2
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506861"
---

<span data-ttu-id="4edec-101">Les packages ajoutés aux flux du gestionnaire de package sont nommés dans un format pirate : `{product}-{type}-{version}` .</span><span class="sxs-lookup"><span data-stu-id="4edec-101">The packages added to package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="4edec-102">**production**</span><span class="sxs-lookup"><span data-stu-id="4edec-102">**product**</span></span>\
<span data-ttu-id="4edec-103">Type de produit .NET à installer.</span><span class="sxs-lookup"><span data-stu-id="4edec-103">The type of .NET product to install.</span></span> <span data-ttu-id="4edec-104">Les options valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="4edec-104">Valid options are:</span></span>

  - <span data-ttu-id="4edec-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="4edec-105">dotnet</span></span>
  - <span data-ttu-id="4edec-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="4edec-106">aspnetcore</span></span>

- <span data-ttu-id="4edec-107">**entrer**</span><span class="sxs-lookup"><span data-stu-id="4edec-107">**type**</span></span>\
<span data-ttu-id="4edec-108">Choisit le kit de développement logiciel (SDK) ou le Runtime.</span><span class="sxs-lookup"><span data-stu-id="4edec-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="4edec-109">Les options valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="4edec-109">Valid options are:</span></span>

  - <span data-ttu-id="4edec-110">SDK</span><span class="sxs-lookup"><span data-stu-id="4edec-110">sdk</span></span>
  - <span data-ttu-id="4edec-111">runtime</span><span class="sxs-lookup"><span data-stu-id="4edec-111">runtime</span></span>

- <span data-ttu-id="4edec-112">**Version**</span><span class="sxs-lookup"><span data-stu-id="4edec-112">**version**</span></span>\
<span data-ttu-id="4edec-113">Version du kit de développement logiciel (SDK) ou du runtime à installer.</span><span class="sxs-lookup"><span data-stu-id="4edec-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="4edec-114">Cet article fournira toujours les instructions relatives à la dernière version prise en charge.</span><span class="sxs-lookup"><span data-stu-id="4edec-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="4edec-115">Les options valides sont toutes les versions publiées, par exemple :</span><span class="sxs-lookup"><span data-stu-id="4edec-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="4edec-116">5.0</span><span class="sxs-lookup"><span data-stu-id="4edec-116">5.0</span></span>
  - <span data-ttu-id="4edec-117">3.1</span><span class="sxs-lookup"><span data-stu-id="4edec-117">3.1</span></span>
  - <span data-ttu-id="4edec-118">3.0</span><span class="sxs-lookup"><span data-stu-id="4edec-118">3.0</span></span>
  - <span data-ttu-id="4edec-119">2.1</span><span class="sxs-lookup"><span data-stu-id="4edec-119">2.1</span></span>

  <span data-ttu-id="4edec-120">Il est possible que le kit de développement logiciel (SDK)/Runtime que vous essayez de télécharger ne soit pas disponible pour votre distribution Linux.</span><span class="sxs-lookup"><span data-stu-id="4edec-120">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="4edec-121">Pour obtenir la liste des distributions prises en charge, consultez [dépendances et exigences de .net Core](../linux.md).</span><span class="sxs-lookup"><span data-stu-id="4edec-121">For a list of supported distributions, see [.NET Core dependencies and requirements](../linux.md).</span></span>

### <a name="examples"></a><span data-ttu-id="4edec-122">Exemples</span><span class="sxs-lookup"><span data-stu-id="4edec-122">Examples</span></span>

- <span data-ttu-id="4edec-123">Installez le ASP.NET Core 5,0 Runtime : `aspnetcore-runtime-5.0`</span><span class="sxs-lookup"><span data-stu-id="4edec-123">Install the ASP.NET Core 5.0 runtime: `aspnetcore-runtime-5.0`</span></span>
- <span data-ttu-id="4edec-124">Installez le Runtime .NET Core 2,1 : `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="4edec-124">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="4edec-125">Installez le kit de développement logiciel (SDK) .NET 5,0 : `dotnet-sdk-5.0`</span><span class="sxs-lookup"><span data-stu-id="4edec-125">Install the .NET 5.0 SDK: `dotnet-sdk-5.0`</span></span>
- <span data-ttu-id="4edec-126">Installez le kit de développement logiciel (SDK) .NET Core 3,1 : `dotnet-sdk-3.1`</span><span class="sxs-lookup"><span data-stu-id="4edec-126">Install the .NET Core 3.1 SDK: `dotnet-sdk-3.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="4edec-127">Package manquant</span><span class="sxs-lookup"><span data-stu-id="4edec-127">Package missing</span></span>

<span data-ttu-id="4edec-128">Si la combinaison package-version ne fonctionne pas, elle n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="4edec-128">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="4edec-129">Par exemple, il n’existe pas de kit de développement logiciel (SDK) ASP.NET Core, les composants SDK sont inclus dans le kit de développement logiciel (SDK) .NET.</span><span class="sxs-lookup"><span data-stu-id="4edec-129">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET SDK.</span></span> <span data-ttu-id="4edec-130">La valeur `aspnetcore-sdk-2.2` est incorrecte et doit être `dotnet-sdk-2.2` .</span><span class="sxs-lookup"><span data-stu-id="4edec-130">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="4edec-131">Pour obtenir la liste des distributions Linux prises en charge par .NET Core, consultez [dépendances et exigences .net](../linux.md).</span><span class="sxs-lookup"><span data-stu-id="4edec-131">For a list of Linux distributions supported by .NET Core, see [.NET dependencies and requirements](../linux.md).</span></span>
