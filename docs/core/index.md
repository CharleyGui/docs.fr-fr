---
title: Guide .NET Core
description: .NET Core est une implémentation modulaire et haute performance de .NET pour créer des applications Windows, Linux et macOS. Découvrez .NET Core pour démarrer.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 3db98d21a7cdc80d8a98b23782a81ffa37520937
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75740747"
---
# <a name="net-core-guide"></a><span data-ttu-id="33e76-104">Guide .NET Core</span><span class="sxs-lookup"><span data-stu-id="33e76-104">.NET Core guide</span></span>

<span data-ttu-id="33e76-105">[.NET Core](about.md) est une plateforme de développement généraliste [open source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT) qui est tenue à jour par Microsoft et la communauté .NET sur [GitHub](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="33e76-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="33e76-106">Cette multiplateforme prend en charge Windows, macOS et Linux. Elle permet de générer des applications destinées à des appareils, au cloud et à l’Internet des objets.</span><span class="sxs-lookup"><span data-stu-id="33e76-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="33e76-107">Consultez [À propos de .NET Core](about.md) pour en savoir plus sur .NET Core, notamment ses caractéristiques, les langues et frameworks pris en charge et les API clés.</span><span class="sxs-lookup"><span data-stu-id="33e76-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="33e76-108">Consultez les [Tutoriels .NET Core](tutorials/index.md) pour apprendre à créer une application .NET Core simple.</span><span class="sxs-lookup"><span data-stu-id="33e76-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="33e76-109">Il suffit de quelques minutes pour créer votre première application et la rendre opérationnelle.</span><span class="sxs-lookup"><span data-stu-id="33e76-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="33e76-110">Si vous souhaitez tester .NET Core dans votre navigateur, consultez le tutoriel en ligne [Nombres en C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml).</span><span class="sxs-lookup"><span data-stu-id="33e76-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="33e76-111">Télécharger .NET Core</span><span class="sxs-lookup"><span data-stu-id="33e76-111">Download .NET Core</span></span>

<span data-ttu-id="33e76-112">Téléchargez le [.NET Core SDK](https://www.microsoft.com/net/download) pour essayer .NET Core sur votre Windows, macOS ou Linux machine.</span><span class="sxs-lookup"><span data-stu-id="33e76-112">Download the [.NET Core SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="33e76-113">Et si vous préférez utiliser des conteneurs Docker, visitez le [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="33e76-113">And if you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

<span data-ttu-id="33e76-114">Toutes les versions de .NET Core sont disponibles sur [Téléchargements de .NET Core](https://dotnet.microsoft.com/download/dotnet-core) si vous recherchez une autre version de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="33e76-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-31"></a><span data-ttu-id="33e76-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="33e76-115">.NET Core 3.1</span></span>

<span data-ttu-id="33e76-116">La dernière version est .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="33e76-116">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="33e76-117">3.1 comprend des améliorations mineures au-dessus de .NET Core 3.0, cependant, .NET Core 3.1 est une [version soutenue à long terme](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="33e76-117">3.1 includes minor improvements over .NET Core 3.0, however, .NET Core 3.1 is a [long-term supported release](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span> <span data-ttu-id="33e76-118">Pour plus d’informations sur la version .NET Core 3.1, voir [Ce qui est nouveau dans .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span><span class="sxs-lookup"><span data-stu-id="33e76-118">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="33e76-119">Créer votre première application</span><span class="sxs-lookup"><span data-stu-id="33e76-119">Create your first application</span></span>

<span data-ttu-id="33e76-120">Après avoir installé le SDK .NET Core, ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="33e76-120">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="33e76-121">Entrez `dotnet` les commandes suivantes pour créer et exécuter une application CMD :</span><span class="sxs-lookup"><span data-stu-id="33e76-121">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="33e76-122">Vous devez normalement voir la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="33e76-122">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="33e76-123">Support</span><span class="sxs-lookup"><span data-stu-id="33e76-123">Support</span></span>

<span data-ttu-id="33e76-124">.NET Core est [pris en charge par Microsoft](https://dotnet.microsoft.com/platform/support/policy), sur Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="33e76-124">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS, and Linux.</span></span> <span data-ttu-id="33e76-125">La sécurité et la qualité sont mises à jour plusieurs fois par an, en général, tous les mois.</span><span class="sxs-lookup"><span data-stu-id="33e76-125">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="33e76-126">Les distributions binaires .NET Core sont générées et testées sur des serveurs managés par Microsoft dans Azure et elles sont prises en charge comme tous les produits Microsoft.</span><span class="sxs-lookup"><span data-stu-id="33e76-126">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="33e76-127">[Red Hat prend en charge .NET Core](http://redhatloves.net/) sur Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="33e76-127">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="33e76-128">Red Hat génère .NET Core à partir de la source et le rend disponible dans les [collections logicielles Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="33e76-128">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="33e76-129">Red Hat et Microsoft collaborent pour s’assurer que .NET Core fonctionne correctement sur RHEL.</span><span class="sxs-lookup"><span data-stu-id="33e76-129">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
