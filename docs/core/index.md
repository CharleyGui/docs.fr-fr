---
title: Guide .NET Core
description: .NET Core est une implémentation modulaire à hautes performances de .NET pour la création d’applications Windows, Linux et Mac. Découvrez .NET Core pour démarrer.
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 0007c1c6a9939c46f123535f9053ac1d4ced7266
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848948"
---
# <a name="net-core-guide"></a><span data-ttu-id="5b8ce-104">Guide .NET Core</span><span class="sxs-lookup"><span data-stu-id="5b8ce-104">.NET Core Guide</span></span>

<span data-ttu-id="5b8ce-105">[.NET Core](about.md) est une plateforme de développement généraliste [open source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) qui est tenue à jour par Microsoft et la communauté .NET sur [GitHub](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="5b8ce-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="5b8ce-106">Cette multiplateforme prend en charge Windows, macOS et Linux. Elle permet de générer des applications destinées à des appareils, au cloud et à l’Internet des objets.</span><span class="sxs-lookup"><span data-stu-id="5b8ce-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="5b8ce-107">Consultez [À propos de .NET Core](about.md) pour en savoir plus sur .NET Core, notamment ses caractéristiques, les langues et frameworks pris en charge et les API clés.</span><span class="sxs-lookup"><span data-stu-id="5b8ce-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="5b8ce-108">Consultez les [Tutoriels .NET Core](tutorials/index.md) pour apprendre à créer une application .NET Core simple.</span><span class="sxs-lookup"><span data-stu-id="5b8ce-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="5b8ce-109">Il suffit de quelques minutes pour créer votre première application et la rendre opérationnelle.</span><span class="sxs-lookup"><span data-stu-id="5b8ce-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="5b8ce-110">Si vous souhaitez tester .NET Core dans votre navigateur, consultez le tutoriel en ligne [Nombres en C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml).</span><span class="sxs-lookup"><span data-stu-id="5b8ce-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core-22"></a><span data-ttu-id="5b8ce-111">Télécharger .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5b8ce-111">Download .NET Core 2.2</span></span>

<span data-ttu-id="5b8ce-112">Téléchargez le kit [SDK .NET Core 2.2](https://dotnet.microsoft.com/download) pour tester .NET Core sur votre ordinateur Windows, macOS ou Linux.</span><span class="sxs-lookup"><span data-stu-id="5b8ce-112">Download the [.NET Core  2.2 SDK](https://dotnet.microsoft.com/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="5b8ce-113">Visitez [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) si vous préférez utiliser des conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="5b8ce-113">Visit [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) if you prefer to use Docker containers.</span></span>

<span data-ttu-id="5b8ce-114">Toutes les versions de .NET Core sont disponibles sur [Téléchargements de .NET Core](https://dotnet.microsoft.com/download/dotnet-core) si vous recherchez une autre version de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5b8ce-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-22"></a><span data-ttu-id="5b8ce-115">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5b8ce-115">.NET Core 2.2</span></span>

<span data-ttu-id="5b8ce-116">La dernière version est [.NET Core 2.2](whats-new/dotnet-core-2-2.md).</span><span class="sxs-lookup"><span data-stu-id="5b8ce-116">The latest version is [.NET Core 2.2](whats-new/dotnet-core-2-2.md).</span></span> <span data-ttu-id="5b8ce-117">Nouvelles fonctionnalités : déploiements dépendants du framework, hooks de démarrage, authentification AAD avec Azure SQL et prise en charge de Windows ARM32.</span><span class="sxs-lookup"><span data-stu-id="5b8ce-117">New features include: framework-dependent deployments, startup hooks, AAD authentication with Azure SQL, and support for Windows ARM32.</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="5b8ce-118">Créer votre première application</span><span class="sxs-lookup"><span data-stu-id="5b8ce-118">Create your first application</span></span>

<span data-ttu-id="5b8ce-119">Après avoir installé le SDK .NET Core, ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="5b8ce-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="5b8ce-120">Tapez les commandes `dotnet` suivantes pour créer et exécuter une application C#.</span><span class="sxs-lookup"><span data-stu-id="5b8ce-120">Type the following `dotnet` commands to create and run a C# application.</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="5b8ce-121">Vous devez voir la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="5b8ce-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="5b8ce-122">Assistance</span><span class="sxs-lookup"><span data-stu-id="5b8ce-122">Support</span></span>

<span data-ttu-id="5b8ce-123">.NET Core est [pris en charge par Microsoft](https://dotnet.microsoft.com/platform/support/policy) sur Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="5b8ce-123">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS and Linux.</span></span> <span data-ttu-id="5b8ce-124">La sécurité et la qualité sont mises à jour plusieurs fois par an, en général, tous les mois.</span><span class="sxs-lookup"><span data-stu-id="5b8ce-124">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="5b8ce-125">Les distributions binaires .NET Core sont générées et testées sur des serveurs managés par Microsoft dans Azure et elles sont prises en charge comme tous les produits Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5b8ce-125">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="5b8ce-126">[Red Hat prend en charge .NET Core](http://redhatloves.net/) sur Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="5b8ce-126">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="5b8ce-127">Red Hat génère .NET Core à partir de la source et le rend disponible dans les [collections logicielles Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="5b8ce-127">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="5b8ce-128">Red Hat et Microsoft collaborent pour s’assurer que .NET Core fonctionne correctement sur RHEL.</span><span class="sxs-lookup"><span data-stu-id="5b8ce-128">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
