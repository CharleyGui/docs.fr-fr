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
# <a name="introduction-to-net-core"></a>Introduction à .NET Core

[.NET Core](about.md) est une plate-forme de développement [open-source,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)polyvalente. Vous pouvez créer des applications .NET Core pour Windows, macOS et Linux pour les processeurs x64, x86, ARM32 et ARM64 à l’aide de plusieurs langages de programmation. Cadres et API sont fournis pour [le cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [l’interface utilisateur client](../desktop-wpf/overview/index.md), et [l’apprentissage automatique](/dotnet/machine-learning/).

[Téléchargez le .NET Core SDK](https://dotnet.microsoft.com/download) pour essayer .NET Core sur votre machine. La dernière version est [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

## <a name="download-net-core"></a>Télécharger .NET Core

Vous pouvez obtenir .NET Core de la manière suivante:

* [Installateurs pour Windows et macOS](https://dotnet.microsoft.com/download)
* [Packages Linux](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [Conteneurs Docker](https://hub.docker.com/_/microsoft-dotnet-core/)
* [Zips et boules de goudron](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [Installer des scripts](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [Notes de publication](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a>Créer votre première application

Après avoir installé le SDK .NET Core, ouvrez une invite de commandes. Utilisez les commandes suivantes pour créer et exécuter une application :

```dotnetcli
dotnet new console
dotnet run
```

Vous devez normalement voir la sortie suivante.

```output
Hello World!
```

## <a name="contribute"></a>Collaboration

.NET Core est une plate-forme ouverte. Tout le monde est le bienvenu pour participer.

* Déposer des questions et des questions sur les produits à [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).
* Les contributions de produits doivent être effectuées sur l’un des dépôts de projet, tels que [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), ou [aspnetcore](https://github.com/dotnet/aspnetcore). Pour plus d’informations, voir [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).

## <a name="support"></a>Support

.NET Core est pris en charge par Microsoft sur Windows, macOS, et Linux et par Red Hat sur Red Hat Enterprise Linux.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [tutoriels .NET Core](tutorials/index.md)

> [!div class="nextstepaction"]
> [Essayez .NET Core dans votre navigateur](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
