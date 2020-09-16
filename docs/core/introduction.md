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
# <a name="introduction-to-net-core"></a>Introduction à .NET Core

[.Net Core](about.md) est une plateforme de développement [Open source à](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)usage général. Vous pouvez créer des applications .NET Core pour Windows, macOS et Linux pour les processeurs x64, x86, ARM32 et ARM64 à l’aide de plusieurs langages de programmation. Les frameworks et les API sont fournis pour le [Cloud](/aspnet/core/), l' [IOT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [l’interface utilisateur du client](../desktop-wpf/overview/index.md)et les [machine learning](../machine-learning/index.yml).

[Téléchargez le kit SDK .net Core](https://dotnet.microsoft.com/download) pour essayer .net Core sur votre ordinateur. La dernière version est [.net Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

## <a name="download-net-core"></a>Télécharger .NET Core

Vous pouvez vous procurer .NET Core des manières suivantes :

* [Programmes d’installation pour Windows et macOS](https://dotnet.microsoft.com/download)
* [Packages Linux](./install/linux.md)
* [Conteneurs Docker](https://hub.docker.com/_/microsoft-dotnet-core/)
* [Compresse et tarballs](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [Installer les scripts](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [Notes de publication](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a>Créer votre première application

Après avoir installé le SDK .NET Core, ouvrez une invite de commandes. Utilisez les commandes suivantes pour créer et exécuter une application :

```dotnetcli
dotnet new console
dotnet run
```

Vous devez normalement voir la sortie suivante :

```output
Hello World!
```

## <a name="contribute"></a>Collaboration

.NET Core est une plateforme ouverte. Tout le monde est invité à participer.

* Problèmes liés aux produits de fichiers et questions de la [communauté des développeurs](https://developercommunity.visualstudio.com/spaces/61/index.html).
* Les contributions de produits doivent être effectuées sur l’un des référentiels de projet, tels que [dotnet/Runtime](https://github.com/dotnet/runtime), [dotnet/SDK](https://github.com/dotnet/sdk), [dotnet/Rosyln](https://github.com/dotnet/roslyn)ou [aspnetcore](https://github.com/dotnet/aspnetcore). Pour plus d’informations, consultez les dépôts [.net Core](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).

## <a name="support"></a>Support

.NET Core est pris en charge par Microsoft sur Windows, macOS et Linux et Red Hat sur Red Hat Enterprise Linux.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Didacticiels .NET Core](tutorials/index.md)

> [!div class="nextstepaction"]
> [Essayez .NET Core dans votre navigateur](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
