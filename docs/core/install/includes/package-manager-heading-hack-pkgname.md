---
ms.openlocfilehash: ef3e4f9f8145677732b9d2e66d416be277697f55
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920668"
---

<span data-ttu-id="6ded4-101">Les packages ajoutés aux flux du gestionnaire de package sont nommés dans un format pirate : `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="6ded4-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="6ded4-102">\ du **produit**</span><span class="sxs-lookup"><span data-stu-id="6ded4-102">**product**\</span></span>
<span data-ttu-id="6ded4-103">Type de produit .NET à installer.</span><span class="sxs-lookup"><span data-stu-id="6ded4-103">The type of .NET product to install.</span></span> <span data-ttu-id="6ded4-104">Les options admises sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6ded4-104">Valid options are:</span></span>

  - <span data-ttu-id="6ded4-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="6ded4-105">dotnet</span></span>
  - <span data-ttu-id="6ded4-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="6ded4-106">aspnetcore</span></span>

- <span data-ttu-id="6ded4-107">**type**</span><span class="sxs-lookup"><span data-stu-id="6ded4-107">**type**</span></span>\
<span data-ttu-id="6ded4-108">Choisit le kit de développement logiciel (SDK) ou le Runtime.</span><span class="sxs-lookup"><span data-stu-id="6ded4-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="6ded4-109">Les options admises sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6ded4-109">Valid options are:</span></span>

  - <span data-ttu-id="6ded4-110">sdk</span><span class="sxs-lookup"><span data-stu-id="6ded4-110">sdk</span></span>
  - <span data-ttu-id="6ded4-111">Runtime</span><span class="sxs-lookup"><span data-stu-id="6ded4-111">runtime</span></span>

- <span data-ttu-id="6ded4-112">\ de **version**</span><span class="sxs-lookup"><span data-stu-id="6ded4-112">**version**\</span></span>
<span data-ttu-id="6ded4-113">Version du kit de développement logiciel (SDK) ou du runtime à installer.</span><span class="sxs-lookup"><span data-stu-id="6ded4-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="6ded4-114">Cet article fournira toujours les instructions relatives à la dernière version prise en charge.</span><span class="sxs-lookup"><span data-stu-id="6ded4-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="6ded4-115">Les options valides sont toutes les versions publiées, par exemple :</span><span class="sxs-lookup"><span data-stu-id="6ded4-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="6ded4-116">3.0</span><span class="sxs-lookup"><span data-stu-id="6ded4-116">3.0</span></span>
  - <span data-ttu-id="6ded4-117">2.2</span><span class="sxs-lookup"><span data-stu-id="6ded4-117">2.2</span></span>
  - <span data-ttu-id="6ded4-118">2.1</span><span class="sxs-lookup"><span data-stu-id="6ded4-118">2.1</span></span>

### <a name="examples"></a><span data-ttu-id="6ded4-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="6ded4-119">Examples</span></span>

- <span data-ttu-id="6ded4-120">Installez le kit de développement logiciel (SDK) .NET Core 2,2 : `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="6ded4-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span></span>
- <span data-ttu-id="6ded4-121">Installer le ASP.NET Core 3,1 Runtime : `aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="6ded4-121">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="6ded4-122">Installer le Runtime .NET Core 2,1 : `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="6ded4-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="6ded4-123">Package manquant</span><span class="sxs-lookup"><span data-stu-id="6ded4-123">Package missing</span></span>

<span data-ttu-id="6ded4-124">Si la combinaison package-version ne fonctionne pas, elle n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="6ded4-124">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="6ded4-125">Par exemple, il n’existe pas de ASP.NET Core SDK, les composants du kit de développement logiciel (SDK) sont inclus dans le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ded4-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="6ded4-126">La valeur `aspnetcore-sdk-2.2` est incorrecte et doit être `dotnet-sdk-2.2`.</span><span class="sxs-lookup"><span data-stu-id="6ded4-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span>
