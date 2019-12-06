---
title: Guide .NET Core
description: .NET Core est une implémentation modulaire à hautes performances de .NET pour la création d’applications Windows, Linux et Mac. Découvrez .NET Core pour démarrer.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: b2622dba53d64c9dcf58e852d57de117fe79eb2e
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837010"
---
# <a name="net-core-guide"></a><span data-ttu-id="9e701-104">Guide .NET Core</span><span class="sxs-lookup"><span data-stu-id="9e701-104">.NET Core Guide</span></span>

<span data-ttu-id="9e701-105">[.NET Core](about.md) est une plateforme de développement généraliste [open source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) qui est tenue à jour par Microsoft et la communauté .NET sur [GitHub](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="9e701-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="9e701-106">Cette multiplateforme prend en charge Windows, macOS et Linux. Elle permet de générer des applications destinées à des appareils, au cloud et à l’Internet des objets.</span><span class="sxs-lookup"><span data-stu-id="9e701-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="9e701-107">Consultez [À propos de .NET Core](about.md) pour en savoir plus sur .NET Core, notamment ses caractéristiques, les langues et frameworks pris en charge et les API clés.</span><span class="sxs-lookup"><span data-stu-id="9e701-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="9e701-108">Consultez les [Tutoriels .NET Core](tutorials/index.md) pour apprendre à créer une application .NET Core simple.</span><span class="sxs-lookup"><span data-stu-id="9e701-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="9e701-109">Il suffit de quelques minutes pour créer votre première application et la rendre opérationnelle.</span><span class="sxs-lookup"><span data-stu-id="9e701-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="9e701-110">Si vous souhaitez tester .NET Core dans votre navigateur, consultez le tutoriel en ligne [Nombres en C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml).</span><span class="sxs-lookup"><span data-stu-id="9e701-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="9e701-111">Télécharger .NET Core</span><span class="sxs-lookup"><span data-stu-id="9e701-111">Download .NET Core</span></span>

<span data-ttu-id="9e701-112">Téléchargez le [Kit SDK .net Core](https://www.microsoft.com/net/download) pour essayer .net Core sur votre ordinateur Windows, MacOS ou Linux.</span><span class="sxs-lookup"><span data-stu-id="9e701-112">Download the [.NET Core SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="9e701-113">Et si vous préférez utiliser les conteneurs de l’ancrage, visitez le hub de l' [ancreur .net Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="9e701-113">And if you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

<span data-ttu-id="9e701-114">Toutes les versions de .NET Core sont disponibles sur [Téléchargements de .NET Core](https://dotnet.microsoft.com/download/dotnet-core) si vous recherchez une autre version de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9e701-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-31"></a><span data-ttu-id="9e701-115">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="9e701-115">.NET Core 3.1</span></span>

<span data-ttu-id="9e701-116">La dernière version est .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="9e701-116">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="9e701-117">Ce qui comprend des améliorations mineures par rapport à .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="9e701-117">Which includes minor improvements over .NET Core 3.0.</span></span> <span data-ttu-id="9e701-118">Toutefois, .NET Core 3,1 est une version prise en charge à long terme.</span><span class="sxs-lookup"><span data-stu-id="9e701-118">However, .NET Core 3.1 is a long-term supported release.</span></span> <span data-ttu-id="9e701-119">Pour plus d’informations sur la version 3,1 de .NET Core, consultez [what’s New in .net core 3,1](./whats-new/dotnet-core-3-1.md).</span><span class="sxs-lookup"><span data-stu-id="9e701-119">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="9e701-120">Créer votre première application</span><span class="sxs-lookup"><span data-stu-id="9e701-120">Create your first application</span></span>

<span data-ttu-id="9e701-121">Après avoir installé le SDK .NET Core, ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="9e701-121">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="9e701-122">Tapez les commandes de `dotnet` suivantes pour créer et exécuter C# une application :</span><span class="sxs-lookup"><span data-stu-id="9e701-122">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="9e701-123">Vous devez voir la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="9e701-123">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="9e701-124">Prise en charge de</span><span class="sxs-lookup"><span data-stu-id="9e701-124">Support</span></span>

<span data-ttu-id="9e701-125">.NET Core est [pris en charge par Microsoft](https://dotnet.microsoft.com/platform/support/policy), sur Windows, MacOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="9e701-125">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS, and Linux.</span></span> <span data-ttu-id="9e701-126">La sécurité et la qualité sont mises à jour plusieurs fois par an, en général, tous les mois.</span><span class="sxs-lookup"><span data-stu-id="9e701-126">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="9e701-127">Les distributions binaires .NET Core sont générées et testées sur des serveurs managés par Microsoft dans Azure et elles sont prises en charge comme tous les produits Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9e701-127">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="9e701-128">[Red Hat prend en charge .NET Core](http://redhatloves.net/) sur Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="9e701-128">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="9e701-129">Red Hat génère .NET Core à partir de la source et le rend disponible dans les [collections logicielles Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="9e701-129">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="9e701-130">Red Hat et Microsoft collaborent pour s’assurer que .NET Core fonctionne correctement sur RHEL.</span><span class="sxs-lookup"><span data-stu-id="9e701-130">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
