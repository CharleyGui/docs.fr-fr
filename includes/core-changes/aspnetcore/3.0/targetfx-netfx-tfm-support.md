---
ms.openlocfilehash: ec6724ab378dd614c55a024ede18d997d27be3a3
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79549606"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="3bbb8-101">Cadre cible : le soutien cadre net supprimé</span><span class="sxs-lookup"><span data-stu-id="3bbb8-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="3bbb8-102">À partir de ASP.NET Core 3.0, le cadre NET est un cadre cible non pris en soutien.</span><span class="sxs-lookup"><span data-stu-id="3bbb8-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3bbb8-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="3bbb8-103">Change description</span></span>

<span data-ttu-id="3bbb8-104">.NET Framework 4.8 est la dernière version majeure du cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="3bbb8-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="3bbb8-105">Les nouvelles applications ASP.NET Core devraient être construites sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3bbb8-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="3bbb8-106">En commençant par la version .NET Core 3.0, vous pouvez penser à ASP.NET Core 3.0 comme faisant partie de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3bbb8-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="3bbb8-107">Les clients utilisant ASP.NET Core avec .NET Framework peuvent continuer d’une manière entièrement pris en charge en utilisant la [version 2.1 LTS](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="3bbb8-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span> <span data-ttu-id="3bbb8-108">Le soutien et l’entretien de 2,1 se poursuivent au moins jusqu’au 21 août 2021.</span><span class="sxs-lookup"><span data-stu-id="3bbb8-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="3bbb8-109">Cette date est de trois ans après la déclaration de la version LTS par la [politique de soutien .NET](https://dotnet.microsoft.com/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="3bbb8-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://dotnet.microsoft.com/platform/support-policy).</span></span> <span data-ttu-id="3bbb8-110">Le soutien aux paquets ASP.NET Core 2.1 **sur le cadre .NET** s’étendra indéfiniment, semblable à la [politique de service pour d’autres cadres ASP.NET fondés sur des paquets](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span><span class="sxs-lookup"><span data-stu-id="3bbb8-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="3bbb8-111">Pour plus d’informations sur le portage de .NET Framework à .NET Core, voir [Porting à .NET Core](~/docs/core/porting/index.md).</span><span class="sxs-lookup"><span data-stu-id="3bbb8-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="3bbb8-112">`Microsoft.Extensions`(tels que l’exploitation forestière, l’injection de dépendance et la configuration) et le cadre d’entité n’est pas affecté.</span><span class="sxs-lookup"><span data-stu-id="3bbb8-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="3bbb8-113">Ils continueront à soutenir .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3bbb8-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="3bbb8-114">Pour plus d’informations sur la motivation de ce changement, voir [le blog original](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="3bbb8-114">For more information on the motivation for this change, see [the original blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3bbb8-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3bbb8-115">Version introduced</span></span>

<span data-ttu-id="3bbb8-116">3.0</span><span class="sxs-lookup"><span data-stu-id="3bbb8-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3bbb8-117">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="3bbb8-117">Old behavior</span></span>

<span data-ttu-id="3bbb8-118">ASP.NET applications de base pourraient s’exécuter sur .NET Core ou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3bbb8-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3bbb8-119">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="3bbb8-119">New behavior</span></span>

<span data-ttu-id="3bbb8-120">ASP.NET les applications Core ne peuvent être exécutées que sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3bbb8-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3bbb8-121">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="3bbb8-121">Recommended action</span></span>

<span data-ttu-id="3bbb8-122">Effectuez l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3bbb8-122">Take one of the following actions:</span></span>

- <span data-ttu-id="3bbb8-123">Gardez votre application sur ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="3bbb8-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="3bbb8-124">Migrez votre application et dépendances à .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3bbb8-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="3bbb8-125">Category</span><span class="sxs-lookup"><span data-stu-id="3bbb8-125">Category</span></span>

<span data-ttu-id="3bbb8-126">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3bbb8-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3bbb8-127">API affectées</span><span class="sxs-lookup"><span data-stu-id="3bbb8-127">Affected APIs</span></span>

<span data-ttu-id="3bbb8-128">None</span><span class="sxs-lookup"><span data-stu-id="3bbb8-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
