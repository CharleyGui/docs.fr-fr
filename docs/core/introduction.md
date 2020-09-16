---
title: Présentation et présentation de .NET Core
description: .NET Core est une implémentation modulaire et hautement performante de .NET pour la création d’applications Windows, Linux et macOS. Découvrez .NET Core pour démarrer.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 350fd50bee3403a05d1c19c9a692535613b17498
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538274"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="671aa-104">Introduction à .NET Core</span><span class="sxs-lookup"><span data-stu-id="671aa-104">Introduction to .NET Core</span></span>

<span data-ttu-id="671aa-105">[.Net Core](about.md) est une plateforme de développement [Open source à](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)usage général.</span><span class="sxs-lookup"><span data-stu-id="671aa-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform.</span></span> <span data-ttu-id="671aa-106">Vous pouvez créer des applications .NET Core pour Windows, macOS et Linux pour les processeurs x64, x86, ARM32 et ARM64 à l’aide de plusieurs langages de programmation.</span><span class="sxs-lookup"><span data-stu-id="671aa-106">You can create .NET Core apps for Windows, macOS, and Linux for x64, x86, ARM32, and ARM64 processors using multiple programming languages.</span></span> <span data-ttu-id="671aa-107">Les frameworks et les API sont fournis pour le [Cloud](/aspnet/core/), l' [IOT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [l’interface utilisateur du client](../desktop-wpf/overview/index.md)et les [machine learning](../machine-learning/index.yml).</span><span class="sxs-lookup"><span data-stu-id="671aa-107">Frameworks and APIs are provided for [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [client UI](../desktop-wpf/overview/index.md), and [machine learning](../machine-learning/index.yml).</span></span>

<span data-ttu-id="671aa-108">[Téléchargez le kit SDK .net Core](https://dotnet.microsoft.com/download) pour essayer .net Core sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="671aa-108">[Download the .NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your machine.</span></span> <span data-ttu-id="671aa-109">La dernière version est [.net Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="671aa-109">The latest version is [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

## <a name="download-net-core"></a><span data-ttu-id="671aa-110">Télécharger .NET Core</span><span class="sxs-lookup"><span data-stu-id="671aa-110">Download .NET Core</span></span>

<span data-ttu-id="671aa-111">Vous pouvez vous procurer .NET Core des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="671aa-111">You can get .NET Core in the following ways:</span></span>

* [<span data-ttu-id="671aa-112">Programmes d’installation pour Windows et macOS</span><span class="sxs-lookup"><span data-stu-id="671aa-112">Installers for Windows and macOS</span></span>](https://dotnet.microsoft.com/download)
* [<span data-ttu-id="671aa-113">Packages Linux</span><span class="sxs-lookup"><span data-stu-id="671aa-113">Linux packages</span></span>](./install/linux.md)
* [<span data-ttu-id="671aa-114">Conteneurs Docker</span><span class="sxs-lookup"><span data-stu-id="671aa-114">Docker containers</span></span>](https://hub.docker.com/_/microsoft-dotnet-core/)
* [<span data-ttu-id="671aa-115">Compresse et tarballs</span><span class="sxs-lookup"><span data-stu-id="671aa-115">Zips and tarballs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [<span data-ttu-id="671aa-116">Installer les scripts</span><span class="sxs-lookup"><span data-stu-id="671aa-116">Install scripts</span></span>](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [<span data-ttu-id="671aa-117">Notes de publication</span><span class="sxs-lookup"><span data-stu-id="671aa-117">Release notes</span></span>](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a><span data-ttu-id="671aa-118">Créer votre première application</span><span class="sxs-lookup"><span data-stu-id="671aa-118">Create your first application</span></span>

<span data-ttu-id="671aa-119">Après avoir installé le SDK .NET Core, ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="671aa-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="671aa-120">Utilisez les commandes suivantes pour créer et exécuter une application :</span><span class="sxs-lookup"><span data-stu-id="671aa-120">Use the following commands to create and run an application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="671aa-121">Vous devez normalement voir la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="671aa-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="contribute"></a><span data-ttu-id="671aa-122">Collaboration</span><span class="sxs-lookup"><span data-stu-id="671aa-122">Contribute</span></span>

<span data-ttu-id="671aa-123">.NET Core est une plateforme ouverte.</span><span class="sxs-lookup"><span data-stu-id="671aa-123">.NET Core is an open platform.</span></span> <span data-ttu-id="671aa-124">Tout le monde est invité à participer.</span><span class="sxs-lookup"><span data-stu-id="671aa-124">Everyone is welcome to participate.</span></span>

* <span data-ttu-id="671aa-125">Problèmes liés aux produits de fichiers et questions de la [communauté des développeurs](https://developercommunity.visualstudio.com/spaces/61/index.html).</span><span class="sxs-lookup"><span data-stu-id="671aa-125">File product issues and questions at [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span></span>
* <span data-ttu-id="671aa-126">Les contributions de produits doivent être effectuées sur l’un des référentiels de projet, tels que [dotnet/Runtime](https://github.com/dotnet/runtime), [dotnet/SDK](https://github.com/dotnet/sdk), [dotnet/Rosyln](https://github.com/dotnet/roslyn)ou [aspnetcore](https://github.com/dotnet/aspnetcore).</span><span class="sxs-lookup"><span data-stu-id="671aa-126">Product contributions should be made on one of the project repositories, such as [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), or [aspnetcore](https://github.com/dotnet/aspnetcore).</span></span> <span data-ttu-id="671aa-127">Pour plus d’informations, consultez les dépôts [.net Core](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span><span class="sxs-lookup"><span data-stu-id="671aa-127">For more information, see [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="671aa-128">Support</span><span class="sxs-lookup"><span data-stu-id="671aa-128">Support</span></span>

<span data-ttu-id="671aa-129">.NET Core est pris en charge par Microsoft sur Windows, macOS et Linux et Red Hat sur Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="671aa-129">.NET Core is supported by Microsoft on Windows, macOS, and Linux and by Red Hat on Red Hat Enterprise Linux.</span></span>

## <a name="next-steps"></a><span data-ttu-id="671aa-130">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="671aa-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="671aa-131">Didacticiels .NET Core</span><span class="sxs-lookup"><span data-stu-id="671aa-131">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="671aa-132">Essayez .NET Core dans votre navigateur</span><span class="sxs-lookup"><span data-stu-id="671aa-132">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
