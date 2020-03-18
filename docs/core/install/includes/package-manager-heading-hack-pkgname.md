---
ms.openlocfilehash: 51b3c1b3e3d61b23a0511ca807afef0269ac9ee4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77466081"
---

<span data-ttu-id="65389-101">Les paquets ajoutés aux flux de gestionnaire de `{product}-{type}-{version}`paquets sont nommés dans un format hackable: .</span><span class="sxs-lookup"><span data-stu-id="65389-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="65389-102">**Produit**</span><span class="sxs-lookup"><span data-stu-id="65389-102">**product**</span></span>\
<span data-ttu-id="65389-103">Le type de produit .NET à installer.</span><span class="sxs-lookup"><span data-stu-id="65389-103">The type of .NET product to install.</span></span> <span data-ttu-id="65389-104">Les options valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="65389-104">Valid options are:</span></span>

  - <span data-ttu-id="65389-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="65389-105">dotnet</span></span>
  - <span data-ttu-id="65389-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="65389-106">aspnetcore</span></span>

- <span data-ttu-id="65389-107">**Type**</span><span class="sxs-lookup"><span data-stu-id="65389-107">**type**</span></span>\
<span data-ttu-id="65389-108">Choisit le SDK ou l’heure d’exécution.</span><span class="sxs-lookup"><span data-stu-id="65389-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="65389-109">Les options valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="65389-109">Valid options are:</span></span>

  - <span data-ttu-id="65389-110">SDK</span><span class="sxs-lookup"><span data-stu-id="65389-110">sdk</span></span>
  - <span data-ttu-id="65389-111">runtime</span><span class="sxs-lookup"><span data-stu-id="65389-111">runtime</span></span>

- <span data-ttu-id="65389-112">**Version**</span><span class="sxs-lookup"><span data-stu-id="65389-112">**version**</span></span>\
<span data-ttu-id="65389-113">La version du SDK ou l’heure d’exécution à installer.</span><span class="sxs-lookup"><span data-stu-id="65389-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="65389-114">Cet article donnera toujours les instructions pour la dernière version prise en charge.</span><span class="sxs-lookup"><span data-stu-id="65389-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="65389-115">Les options valides sont n’importe quelle version libérée, telles que :</span><span class="sxs-lookup"><span data-stu-id="65389-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="65389-116">3.1</span><span class="sxs-lookup"><span data-stu-id="65389-116">3.1</span></span>
  - <span data-ttu-id="65389-117">3.0</span><span class="sxs-lookup"><span data-stu-id="65389-117">3.0</span></span>
  - <span data-ttu-id="65389-118">2.1</span><span class="sxs-lookup"><span data-stu-id="65389-118">2.1</span></span>

  <span data-ttu-id="65389-119">Il est possible que le SDK/runtime que vous essayez de télécharger n’est pas disponible pour votre distribution Linux.</span><span class="sxs-lookup"><span data-stu-id="65389-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="65389-120">Pour une liste de distributions prises en charge, voir [.NET Core dépendances et exigences](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="65389-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>

### <a name="examples"></a><span data-ttu-id="65389-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="65389-121">Examples</span></span>

- <span data-ttu-id="65389-122">Installer le ASP.NET cœur 3.1 temps d’exécution:`aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="65389-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="65389-123">Installer le temps d’exécution .NET Core 2.1 :`dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="65389-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="65389-124">Installer le .NET Core 3.0 SDK:`dotnet-sdk-3.0`</span><span class="sxs-lookup"><span data-stu-id="65389-124">Install the .NET Core 3.0 SDK: `dotnet-sdk-3.0`</span></span>

### <a name="package-missing"></a><span data-ttu-id="65389-125">Paquet manquant</span><span class="sxs-lookup"><span data-stu-id="65389-125">Package missing</span></span>

<span data-ttu-id="65389-126">Si la combinaison de versions de paquet ne fonctionne pas, elle n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="65389-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="65389-127">Par exemple, il n’y a pas de ASP.NET Core SDK, les composants SDK sont inclus avec le SDK core .NET.</span><span class="sxs-lookup"><span data-stu-id="65389-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="65389-128">La `aspnetcore-sdk-2.2` valeur est incorrecte et doit être `dotnet-sdk-2.2`.</span><span class="sxs-lookup"><span data-stu-id="65389-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="65389-129">Pour une liste de distributions Linux prises en charge par .NET Core, voir [.NET Core dépendances et exigences](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="65389-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>
