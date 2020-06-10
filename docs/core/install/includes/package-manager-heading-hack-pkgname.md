---
ms.openlocfilehash: 7723892a33bf7dd8e475b2f696db5d9ab287e182
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602991"
---

<span data-ttu-id="20231-101">Les packages ajoutés aux flux du gestionnaire de package sont nommés dans un format pirate : `{product}-{type}-{version}` .</span><span class="sxs-lookup"><span data-stu-id="20231-101">The packages added to package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="20231-102">**production**</span><span class="sxs-lookup"><span data-stu-id="20231-102">**product**</span></span>\
<span data-ttu-id="20231-103">Type de produit .NET à installer.</span><span class="sxs-lookup"><span data-stu-id="20231-103">The type of .NET product to install.</span></span> <span data-ttu-id="20231-104">Les options valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="20231-104">Valid options are:</span></span>

  - <span data-ttu-id="20231-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="20231-105">dotnet</span></span>
  - <span data-ttu-id="20231-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="20231-106">aspnetcore</span></span>

- <span data-ttu-id="20231-107">**entrer**</span><span class="sxs-lookup"><span data-stu-id="20231-107">**type**</span></span>\
<span data-ttu-id="20231-108">Choisit le kit de développement logiciel (SDK) ou le Runtime.</span><span class="sxs-lookup"><span data-stu-id="20231-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="20231-109">Les options valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="20231-109">Valid options are:</span></span>

  - <span data-ttu-id="20231-110">SDK</span><span class="sxs-lookup"><span data-stu-id="20231-110">sdk</span></span>
  - <span data-ttu-id="20231-111">runtime</span><span class="sxs-lookup"><span data-stu-id="20231-111">runtime</span></span>

- <span data-ttu-id="20231-112">**Version**</span><span class="sxs-lookup"><span data-stu-id="20231-112">**version**</span></span>\
<span data-ttu-id="20231-113">Version du kit de développement logiciel (SDK) ou du runtime à installer.</span><span class="sxs-lookup"><span data-stu-id="20231-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="20231-114">Cet article fournira toujours les instructions relatives à la dernière version prise en charge.</span><span class="sxs-lookup"><span data-stu-id="20231-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="20231-115">Les options valides sont toutes les versions publiées, par exemple :</span><span class="sxs-lookup"><span data-stu-id="20231-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="20231-116">3.1</span><span class="sxs-lookup"><span data-stu-id="20231-116">3.1</span></span>
  - <span data-ttu-id="20231-117">3.0</span><span class="sxs-lookup"><span data-stu-id="20231-117">3.0</span></span>
  - <span data-ttu-id="20231-118">2.1</span><span class="sxs-lookup"><span data-stu-id="20231-118">2.1</span></span>

  <span data-ttu-id="20231-119">Il est possible que le kit de développement logiciel (SDK)/Runtime que vous essayez de télécharger ne soit pas disponible pour votre distribution Linux.</span><span class="sxs-lookup"><span data-stu-id="20231-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="20231-120">Pour obtenir la liste des distributions prises en charge, consultez [dépendances et exigences de .net Core](../linux.md).</span><span class="sxs-lookup"><span data-stu-id="20231-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../linux.md).</span></span>

### <a name="examples"></a><span data-ttu-id="20231-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="20231-121">Examples</span></span>

- <span data-ttu-id="20231-122">Installez le ASP.NET Core 3,1 Runtime :`aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="20231-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="20231-123">Installez le Runtime .NET Core 2,1 :`dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="20231-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="20231-124">Installez le kit de développement logiciel (SDK) .NET Core 3,1 :`dotnet-sdk-3.1`</span><span class="sxs-lookup"><span data-stu-id="20231-124">Install the .NET Core 3.1 SDK: `dotnet-sdk-3.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="20231-125">Package manquant</span><span class="sxs-lookup"><span data-stu-id="20231-125">Package missing</span></span>

<span data-ttu-id="20231-126">Si la combinaison package-version ne fonctionne pas, elle n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="20231-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="20231-127">Par exemple, il n’existe pas de ASP.NET Core SDK, les composants du kit de développement logiciel (SDK) sont inclus dans le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="20231-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="20231-128">La valeur `aspnetcore-sdk-2.2` est incorrecte et doit être `dotnet-sdk-2.2` .</span><span class="sxs-lookup"><span data-stu-id="20231-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="20231-129">Pour obtenir la liste des distributions Linux prises en charge par .NET Core, consultez [dépendances et exigences de .net Core](../linux.md).</span><span class="sxs-lookup"><span data-stu-id="20231-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../linux.md).</span></span>
