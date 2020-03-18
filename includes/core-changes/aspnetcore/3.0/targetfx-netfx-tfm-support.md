---
ms.openlocfilehash: b60f74947a537c602c7bd1a89587b76bd847c82a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937284"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="d2759-101">Cadre cible : le soutien cadre net supprimé</span><span class="sxs-lookup"><span data-stu-id="d2759-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="d2759-102">À partir de ASP.NET Core 3.0, le cadre NET est un cadre cible non pris en soutien.</span><span class="sxs-lookup"><span data-stu-id="d2759-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d2759-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="d2759-103">Change description</span></span>

<span data-ttu-id="d2759-104">.NET Framework 4.8 est la dernière version majeure du cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="d2759-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="d2759-105">Les nouvelles applications ASP.NET Core devraient être construites sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d2759-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="d2759-106">En commençant par la version .NET Core 3.0, vous pouvez penser à ASP.NET Core 3.0 comme faisant partie de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d2759-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="d2759-107">Les clients utilisant ASP.NET Core avec .NET Framework peuvent continuer d’une manière entièrement pris en charge en utilisant la [version 2.1 LTS](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="d2759-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span> <span data-ttu-id="d2759-108">Le soutien et l’entretien de 2,1 se poursuivent au moins jusqu’au 21 août 2021.</span><span class="sxs-lookup"><span data-stu-id="d2759-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="d2759-109">Cette date est de trois ans après la déclaration de la version LTS par la [politique de soutien .NET](https://www.microsoft.com/net/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="d2759-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy).</span></span> <span data-ttu-id="d2759-110">Le soutien aux paquets ASP.NET Core 2.1 **sur le cadre .NET** s’étendra indéfiniment, semblable à la [politique de service pour d’autres cadres ASP.NET fondés sur des paquets](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span><span class="sxs-lookup"><span data-stu-id="d2759-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="d2759-111">Pour plus d’informations sur le portage de .NET Framework à .NET Core, voir [Porting à .NET Core](~/docs/core/porting/index.md).</span><span class="sxs-lookup"><span data-stu-id="d2759-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="d2759-112">`Microsoft.Extensions`(tels que l’exploitation forestière, l’injection de dépendance et la configuration) et le cadre d’entité n’est pas affecté.</span><span class="sxs-lookup"><span data-stu-id="d2759-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="d2759-113">Ils continueront à soutenir .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d2759-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="d2759-114">Pour plus d’informations sur la motivation de ce changement, voir [le blog original](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="d2759-114">For more information on the motivation for this change, see [the original blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d2759-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d2759-115">Version introduced</span></span>

<span data-ttu-id="d2759-116">3.0</span><span class="sxs-lookup"><span data-stu-id="d2759-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d2759-117">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="d2759-117">Old behavior</span></span>

<span data-ttu-id="d2759-118">ASP.NET applications de base pourraient s’exécuter sur .NET Core ou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d2759-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d2759-119">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="d2759-119">New behavior</span></span>

<span data-ttu-id="d2759-120">ASP.NET les applications Core ne peuvent être exécutées que sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d2759-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d2759-121">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d2759-121">Recommended action</span></span>

<span data-ttu-id="d2759-122">Effectuez l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="d2759-122">Take one of the following actions:</span></span>

- <span data-ttu-id="d2759-123">Gardez votre application sur ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="d2759-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="d2759-124">Migrez votre application et dépendances à .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d2759-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="d2759-125">Category</span><span class="sxs-lookup"><span data-stu-id="d2759-125">Category</span></span>

<span data-ttu-id="d2759-126">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d2759-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d2759-127">API affectées</span><span class="sxs-lookup"><span data-stu-id="d2759-127">Affected APIs</span></span>

<span data-ttu-id="d2759-128">None</span><span class="sxs-lookup"><span data-stu-id="d2759-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
