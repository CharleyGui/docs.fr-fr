---
title: .NET Core intro et aperçu
description: .NET Core est une implémentation modulaire et haute performance de .NET pour créer des applications Windows, Linux et macOS. Découvrez .NET Core pour démarrer.
author: richlander
ms.date: 03/25/2020
ms.custom: updateeachrelease
ms.openlocfilehash: edd3864d3c3c5c0e9fd8c26ee806ffc9e100423d
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80351700"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="dafec-104">Introduction à .NET Core</span><span class="sxs-lookup"><span data-stu-id="dafec-104">Introduction to .NET Core</span></span>

<span data-ttu-id="dafec-105">[.NET Core](about.md) est une plateforme de développement généraliste [open source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT) qui est tenue à jour par Microsoft et la communauté .NET sur [GitHub](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="dafec-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="dafec-106">Cette multiplateforme prend en charge Windows, macOS et Linux. Elle permet de générer des applications destinées à des appareils, au cloud et à l’Internet des objets.</span><span class="sxs-lookup"><span data-stu-id="dafec-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="dafec-107">Télécharger .NET Core</span><span class="sxs-lookup"><span data-stu-id="dafec-107">Download .NET Core</span></span>

<span data-ttu-id="dafec-108">Téléchargez le [.NET Core SDK](https://dotnet.microsoft.com/download) pour essayer .NET Core sur votre Windows, macOS ou Linux machine.</span><span class="sxs-lookup"><span data-stu-id="dafec-108">Download the [.NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="dafec-109">Si vous préférez utiliser des conteneurs Docker, visitez le [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="dafec-109">If you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

## <a name="net-core-31"></a><span data-ttu-id="dafec-110">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="dafec-110">.NET Core 3.1</span></span>

<span data-ttu-id="dafec-111">La dernière version est .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="dafec-111">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="dafec-112">3.1 comprend des améliorations mineures au-dessus de .NET Core 3.0, cependant, .NET Core 3.1 est une [version soutenue à long terme](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="dafec-112">3.1 includes minor improvements over .NET Core 3.0, however, .NET Core 3.1 is a [long-term supported release](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span> <span data-ttu-id="dafec-113">Pour plus d’informations sur la version .NET Core 3.1, voir [Ce qui est nouveau dans .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span><span class="sxs-lookup"><span data-stu-id="dafec-113">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

<span data-ttu-id="dafec-114">Si vous êtes à la recherche d’une autre version de .NET Core, toutes les versions sont disponibles à [.NET Core téléchargements](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="dafec-114">If you're looking for another version of .NET Core, all the versions are available at [.NET Core downloads](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="dafec-115">Créer votre première application</span><span class="sxs-lookup"><span data-stu-id="dafec-115">Create your first application</span></span>

<span data-ttu-id="dafec-116">Après avoir installé le SDK .NET Core, ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="dafec-116">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="dafec-117">Entrez `dotnet` les commandes suivantes pour créer et exécuter une application CMD :</span><span class="sxs-lookup"><span data-stu-id="dafec-117">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="dafec-118">Vous devez normalement voir la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="dafec-118">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="dafec-119">Support</span><span class="sxs-lookup"><span data-stu-id="dafec-119">Support</span></span>

<span data-ttu-id="dafec-120">.NET Core est [pris en charge par Microsoft](https://dotnet.microsoft.com/platform/support/policy) sur Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="dafec-120">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy) on Windows, macOS, and Linux.</span></span> <span data-ttu-id="dafec-121">La sécurité et la qualité sont mises à jour plusieurs fois par an, en général, tous les mois.</span><span class="sxs-lookup"><span data-stu-id="dafec-121">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="dafec-122">Les distributions binaires .NET Core sont générées et testées sur des serveurs managés par Microsoft dans Azure et elles sont prises en charge comme tous les produits Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dafec-122">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="dafec-123">[Red Hat prend en charge .NET Core](http://redhatloves.net/) sur Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="dafec-123">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="dafec-124">Red Hat génère .NET Core à partir de la source et le rend disponible dans les [collections logicielles Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="dafec-124">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="dafec-125">Red Hat et Microsoft collaborent pour s’assurer que .NET Core fonctionne correctement sur RHEL.</span><span class="sxs-lookup"><span data-stu-id="dafec-125">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dafec-126">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="dafec-126">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dafec-127">tutoriels .NET Core</span><span class="sxs-lookup"><span data-stu-id="dafec-127">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="dafec-128">Essayez .NET Core dans votre navigateur</span><span class="sxs-lookup"><span data-stu-id="dafec-128">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
