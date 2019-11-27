---
title: Installer le Runtime .NET Core sur Windows, Linux et macOS-.NET Core
description: Découvrez comment installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances requises pour exécuter des applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 395978a2e471260254caf3da8421adf2413c132c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450855"
---
# <a name="install-the-net-core-runtime"></a>Installer le Runtime .NET Core

Dans cet article, vous allez apprendre à télécharger et à installer le Runtime .NET Core. Le Runtime .NET Core est utilisé pour exécuter des applications créées avec .NET Core.

Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants :

- [Téléchargements .NET Core 3,1 Preview 3](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Téléchargements .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [Téléchargements .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [Téléchargements .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="install-with-an-installer"></a>Installer avec un programme d’installation

Windows et macOS ont tous deux des programmes d’installation autonomes qui peuvent être utilisés pour installer le Runtime .NET Core 3,0.

- UC Windows [x64](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-windows-x64-installer) | [UC x32](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-windows-x86-installer)
- [processeurs MacOS x64](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-macos-x64-installer)

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Installer avec un gestionnaire de package

Vous pouvez installer le Runtime .NET Core avec un grand nombre de gestionnaires de packages Linux courants. Pour plus d’informations, consultez [Linux Package Manager-install .net Core](linux-package-manager-rhel7.md).

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Installer avec l’automatisation PowerShell

Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime. Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).

Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 2,1. Pour installer la version actuelle de .NET Core (3,0), exécutez le script avec le commutateur suivant :

```powershell
dotnet-install.ps1 -Channel 3.0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Installer avec l’automatisation bash

Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime. Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).

Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 2,1. Pour installer la version actuelle de .NET Core (3,0), exécutez le script avec le commutateur suivant :

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="docker"></a>Docker

Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte. Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.

.NET Core peut s’exécuter dans un conteneur d’ancrage. Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/). Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.

Microsoft fournit des images adaptées à des scénarios particuliers. Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.

Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Étapes suivantes :

- [Comment vérifier si .net Core est déjà installé](how-to-detect-installed-versions.md).
