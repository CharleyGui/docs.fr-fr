---
title: Configuration requise pour .NET Core sur Mac
description: Versions macOS et dépendances .NET Core prises en charge pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs macOS.
author: thraka
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 10/11/2019
ms.openlocfilehash: 2d4fc0b37be08988440325db8b507124c36bf053
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318317"
---
# <a name="prerequisites-for-net-core-on-macos"></a>Configuration requise pour .NET Core sur macOS

Cet article vous présente les versions macOS et les dépendances .NET Core prises en charge nécessaires pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs macOS. Les versions de système d’exploitation et dépendances prises en charge suivantes s’appliquent aux trois méthodes de développement des applications .NET Core sur un Mac : via la [ligne de commande de votre éditeur favori](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/) et [Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).

## <a name="downloads-and-dependencies"></a>Téléchargements et dépendances

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3,0 est pris en charge sur **MacOS High Sierra (version 10,13)** et versions ultérieures. Une architecture d’UC **x64** est requise.

Téléchargez et installez le kit SDK .NET Core à partir de la page de [téléchargement de .net Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0) . [.Net core 3,0 les versions de système d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) pour la liste complète des systèmes d’exploitation, distributions et versions pris en charge par .net Core 3,0, les versions de système d’exploitation et les liens de stratégie de cycle de vie.

Pour obtenir la liste des problèmes connus, consultez [problèmes connus liés à .net Core](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-known-issues.md).

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

.NET Core 2,2 est pris en charge sur **MacOS Sierra (version 10,12)** et versions ultérieures. Une architecture d’UC **x64** est requise.

Téléchargez et installez le kit SDK .NET Core à partir de la page de [téléchargement de .net Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) . [.Net core 2,2 les versions de système d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) pour la liste complète des systèmes d’exploitation, distributions et versions pris en charge par .net Core 2,2, les versions de système d’exploitation et les liens de stratégie de cycle de vie.

Pour obtenir la liste des problèmes connus, consultez [problèmes connus liés à .net Core](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-known-issues.md).

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2,1 est pris en charge sur **MacOS Sierra (version 10,12)** et versions ultérieures. Une architecture d’UC **x64** est requise.

Téléchargez et installez le kit SDK .NET Core à partir de la page de [téléchargement de .net Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1) . [.Net core 2,1 les versions de système d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) pour la liste complète des systèmes d’exploitation, distributions et versions pris en charge par .net Core 2,1, les versions de système d’exploitation et les liens de stratégie de cycle de vie.

Pour obtenir la liste des problèmes connus, consultez [problèmes connus liés à .net Core](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-known-issues.md).

---

## <a name="libgdiplus"></a>libgdiplus

Les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* nécessitent l’installation de libgdiplus.

Pour obtenir facilement des libgdiplus, vous pouvez utiliser le gestionnaire de package [Homebrew (« Brass »)](https://brew.sh/) pour MacOS. Après l’installation de la commande *infuse*, installez libgdiplus en exécutant les commandes suivantes à une invite de commandes :

```console
brew update
brew install libgdiplus
```

## <a name="visual-studio-for-mac"></a>Visual Studio pour Mac

Vous pouvez utiliser l’éditeur de votre choix pour développer des applications .NET Core à l’aide du Kit SDK .NET Core. Toutefois, si vous voulez développer des applications .NET Core sous Mac dans un environnement de développement intégré, vous pouvez utiliser [Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).
