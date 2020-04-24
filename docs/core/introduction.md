---
title: .NET Core intro et aperçu
description: .NET Core est une implémentation modulaire et haute performance de .NET pour créer des applications Windows, Linux et macOS. Découvrez .NET Core pour démarrer.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: f99b446bbd38b2b814c13afa13ab34cd5c9aa086
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645524"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="bd6db-104">Introduction à .NET Core</span><span class="sxs-lookup"><span data-stu-id="bd6db-104">Introduction to .NET Core</span></span>

<span data-ttu-id="bd6db-105">[.NET Core](about.md) est une plate-forme de développement [open-source,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)polyvalente.</span><span class="sxs-lookup"><span data-stu-id="bd6db-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform.</span></span> <span data-ttu-id="bd6db-106">Vous pouvez créer des applications .NET Core pour Windows, macOS et Linux pour les processeurs x64, x86, ARM32 et ARM64 à l’aide de plusieurs langages de programmation.</span><span class="sxs-lookup"><span data-stu-id="bd6db-106">You can create .NET Core apps for Windows, macOS, and Linux for x64, x86, ARM32, and ARM64 processors using multiple programming languages.</span></span> <span data-ttu-id="bd6db-107">Cadres et API sont fournis pour [le cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [l’interface utilisateur client](../desktop-wpf/overview/index.md), et [l’apprentissage automatique](/dotnet/machine-learning/).</span><span class="sxs-lookup"><span data-stu-id="bd6db-107">Frameworks and APIs are provided for [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [client UI](../desktop-wpf/overview/index.md), and [machine learning](/dotnet/machine-learning/).</span></span>

<span data-ttu-id="bd6db-108">[Téléchargez le .NET Core SDK](https://dotnet.microsoft.com/download) pour essayer .NET Core sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="bd6db-108">[Download the .NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your machine.</span></span> <span data-ttu-id="bd6db-109">La dernière version est [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="bd6db-109">The latest version is [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

## <a name="download-net-core"></a><span data-ttu-id="bd6db-110">Télécharger .NET Core</span><span class="sxs-lookup"><span data-stu-id="bd6db-110">Download .NET Core</span></span>

<span data-ttu-id="bd6db-111">Vous pouvez obtenir .NET Core de la manière suivante:</span><span class="sxs-lookup"><span data-stu-id="bd6db-111">You can get .NET Core in the following ways:</span></span>

* [<span data-ttu-id="bd6db-112">Installateurs pour Windows et macOS</span><span class="sxs-lookup"><span data-stu-id="bd6db-112">Installers for Windows and macOS</span></span>](https://dotnet.microsoft.com/download)
* [<span data-ttu-id="bd6db-113">Packages Linux</span><span class="sxs-lookup"><span data-stu-id="bd6db-113">Linux packages</span></span>](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [<span data-ttu-id="bd6db-114">Conteneurs Docker</span><span class="sxs-lookup"><span data-stu-id="bd6db-114">Docker containers</span></span>](https://hub.docker.com/_/microsoft-dotnet-core/)
* [<span data-ttu-id="bd6db-115">Zips et boules de goudron</span><span class="sxs-lookup"><span data-stu-id="bd6db-115">Zips and tar balls</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [<span data-ttu-id="bd6db-116">Installer des scripts</span><span class="sxs-lookup"><span data-stu-id="bd6db-116">Install scripts</span></span>](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [<span data-ttu-id="bd6db-117">Notes de publication</span><span class="sxs-lookup"><span data-stu-id="bd6db-117">Release notes</span></span>](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a><span data-ttu-id="bd6db-118">Créer votre première application</span><span class="sxs-lookup"><span data-stu-id="bd6db-118">Create your first application</span></span>

<span data-ttu-id="bd6db-119">Après avoir installé le SDK .NET Core, ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="bd6db-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="bd6db-120">Utilisez les commandes suivantes pour créer et exécuter une application :</span><span class="sxs-lookup"><span data-stu-id="bd6db-120">Use the following commands to create and run an application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="bd6db-121">Vous devez normalement voir la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="bd6db-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="contribute"></a><span data-ttu-id="bd6db-122">Collaboration</span><span class="sxs-lookup"><span data-stu-id="bd6db-122">Contribute</span></span>

<span data-ttu-id="bd6db-123">.NET Core est une plate-forme ouverte.</span><span class="sxs-lookup"><span data-stu-id="bd6db-123">.NET Core is an open platform.</span></span> <span data-ttu-id="bd6db-124">Tout le monde est le bienvenu pour participer.</span><span class="sxs-lookup"><span data-stu-id="bd6db-124">Everyone is welcome to participate.</span></span>

* <span data-ttu-id="bd6db-125">Déposer des questions et des questions sur les produits à [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span><span class="sxs-lookup"><span data-stu-id="bd6db-125">File product issues and questions at [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span></span>
* <span data-ttu-id="bd6db-126">Les contributions de produits doivent être effectuées sur l’un des dépôts de projet, tels que [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), ou [aspnetcore](https://github.com/dotnet/aspnetcore).</span><span class="sxs-lookup"><span data-stu-id="bd6db-126">Product contributions should be made on one of the project repositories, such as [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), or [aspnetcore](https://github.com/dotnet/aspnetcore).</span></span> <span data-ttu-id="bd6db-127">Pour plus d’informations, voir [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span><span class="sxs-lookup"><span data-stu-id="bd6db-127">For more information, see [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="bd6db-128">Support</span><span class="sxs-lookup"><span data-stu-id="bd6db-128">Support</span></span>

<span data-ttu-id="bd6db-129">.NET Core est pris en charge par Microsoft sur Windows, macOS, et Linux et par Red Hat sur Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="bd6db-129">.NET Core is supported by Microsoft on Windows, macOS, and Linux and by Red Hat on Red Hat Enterprise Linux.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bd6db-130">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="bd6db-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd6db-131">tutoriels .NET Core</span><span class="sxs-lookup"><span data-stu-id="bd6db-131">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd6db-132">Essayez .NET Core dans votre navigateur</span><span class="sxs-lookup"><span data-stu-id="bd6db-132">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
