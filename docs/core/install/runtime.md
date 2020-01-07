---
title: Installer le Runtime .NET Core sur Windows, Linux et macOS-.NET Core
description: Découvrez comment installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances requises pour exécuter des applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a45cb570ccf572a699359598319fd3867fb5e5dd
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340958"
---
# <a name="install-the-net-core-runtime"></a>Installer le Runtime .NET Core

Dans cet article, vous allez apprendre à télécharger et à installer le Runtime .NET Core. Le Runtime .NET Core est utilisé pour exécuter des applications créées avec .NET Core.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Installer avec un programme d’installation

Windows possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le Runtime .NET Core 3,1 :

- [Processeurs x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Processeurs x86 (32 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Installer avec un programme d’installation

macOS possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le Runtime .NET Core 3,1 :

- [Processeurs x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Installer avec un gestionnaire de package

Vous pouvez installer le Runtime .NET Core avec un grand nombre de gestionnaires de packages Linux courants. Pour plus d’informations, consultez [Linux Package Manager-install .net Core](linux-package-managers.md).

Son installation avec un gestionnaire de package est uniquement prise en charge sur l’architecture x64. Si vous installez le Runtime .NET Core avec une architecture différente, par exemple ARM, suivez les instructions de la section [téléchargement et installation manuelle](#download-and-manually-install) . Pour plus d’informations sur les architectures prises en charge, consultez [.net Core Dependencies and Requirements](dependencies.md).

## <a name="download-and-manually-install"></a>Télécharger et installer manuellement

Pour extraire le runtime et rendre les commandes CLI .NET Core disponibles sur le terminal, commencez par [Télécharger](#all-net-core-downloads) une version binaire .net core. Ensuite, ouvrez un terminal et exécutez les commandes suivantes.

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Les commandes `export` précédentes rendent uniquement les commandes CLI .NET Core disponibles pour la session Terminal dans laquelle elles ont été exécutées.
>
> Vous pouvez modifier votre profil de Shell pour ajouter définitivement les commandes. Un certain nombre de shells différents sont disponibles pour Linux et chacun d’eux a un profil différent. Par exemple :
>
> - **Interpréteur**de commandes bash : *~/. bash_profile*, *~ fichier/.bashrc*
> - **Shell Korn**: *~/.kshrc* ou *. Profile*
> - **Z Shell**: *~/.zshrc* ou *. zprofile*
> 
> Modifiez le fichier source approprié pour votre shell et ajoutez `:$HOME/dotnet` à la fin de l’instruction `PATH` existante. Si aucune instruction `PATH` n’est incluse, ajoutez une nouvelle ligne avec `export PATH=$PATH:$HOME/dotnet`.
>
> En outre, ajoutez `export DOTNET_ROOT=$HOME/dotnet` à la fin du fichier.

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Installer avec l’automatisation PowerShell

Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime. Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).

Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1. Vous pouvez choisir une version spécifique en spécifiant le commutateur `Channel`. Incluez le commutateur `Runtime` pour installer un Runtime. Dans le cas contraire, le script installe le [Kit de développement logiciel (SDK)](sdk.md).

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> La commande ci-dessus installe le runtime ASP.NET Core pour une compatibilité maximale. Le runtime ASP.NET Core comprend également le Runtime .NET Core standard.

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Installer avec l’automatisation bash

Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime. Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).

Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1. Vous pouvez choisir une version spécifique en spécifiant le commutateur `current`. Incluez le commutateur `runtime` pour installer un Runtime. Dans le cas contraire, le script installe le [Kit de développement logiciel (SDK)](sdk.md).

```bash
./dotnet-install.sh --current 3.1 --runtime aspnetcore
```

> [!NOTE]
> La commande ci-dessus installe le runtime ASP.NET Core pour une compatibilité maximale. Le runtime ASP.NET Core comprend également le Runtime .NET Core standard.

::: zone-end

## <a name="all-net-core-downloads"></a>Tous les téléchargements .NET Core

Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants :

- [Téléchargements .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Téléchargements .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [Téléchargements .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [Téléchargements .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte. Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.

.NET Core peut s’exécuter dans un conteneur d’ancrage. Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/). Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.

Microsoft fournit des images adaptées à des scénarios particuliers. Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.

Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Étapes suivantes :

- [Comment vérifier si .net Core est déjà installé](how-to-detect-installed-versions.md).
