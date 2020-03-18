---
title: Installer .NET Core runtime sur Windows, Linux et macOS - .NET Core
description: Apprenez à installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances requises pour exécuter des applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca55b8fab4aa9ca9f7e308cce57181e2c7e89f4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399013"
---
# <a name="install-the-net-core-runtime"></a>Installer le .NET Core Runtime

Dans cet article, vous apprendrez à télécharger et installer le temps d’exécution .NET Core. Le temps d’exécution .NET Core est utilisé pour exécuter des applications créées avec .NET Core.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Installer avec un installateur

Windows a des installateurs autonomes qui peuvent être utilisés pour installer le point d’exécution .NET Core 3.1:

- [x64 (64 bits) DPC](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [x86 (32 bits) CPU](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Installer avec un installateur

macOS a des installateurs autonomes qui peuvent être utilisés pour installer le temps d’exécution .NET Core 3.1 :

- [x64 (64 bits) DPC](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>Télécharger et installer manuellement

Comme alternative aux installateurs macOS pour .NET Core, vous pouvez télécharger et installer manuellement l’heure d’exécution.

Pour installer l’heure d’exécution et activer les commandes CLI .NET Core disponibles au terminal, [téléchargez](#all-net-core-downloads) d’abord une version binaire .NET Core. Ensuite, ouvrez un terminal et exécutez les commandes suivantes. On suppose que le temps d’exécution est téléchargé sur le `~/Downloads/dotnet-runtime.pkg` fichier.

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Installer avec un gestionnaire de paquets

Vous pouvez installer le .NET Core Runtime avec de nombreux gestionnaires de paquets Linux communs. Pour plus d’informations, voir [Linux Package Manager - Install .NET Core](linux-package-managers.md).

L’installer avec un gestionnaire de paquets n’est pris en charge que sur l’architecture x64. Si vous installez le .NET Core Runtime avec une architecture différente, comme ARM, suivez les instructions sur la section [Télécharger et installer manuellement.](#download-and-manually-install) Pour plus d’informations sur les architectures qui sont prises en charge, voir [.NET Core dépendances et les exigences](dependencies.md).

## <a name="download-and-manually-install"></a>Télécharger et installer manuellement

Pour extraire l’heure d’exécution et rendre disponibles les commandes CLI de base .NET au terminal, [téléchargez](#all-net-core-downloads) d’abord une version binaire .NET Core. Ensuite, ouvrez un terminal et exécutez les commandes suivantes.

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Les `export` commandes précédentes ne rendent disponibles que les commandes CLI de base .NET pour la session terminale au cours de laquelle il a été exécuté.
>
> Vous pouvez modifier votre profil shell pour ajouter définitivement les commandes. Il ya un certain nombre de coquilles différentes disponibles pour Linux et chacun a un profil différent. Par exemple :
>
> - **Bash Shell**: *'/.bash_profile*, *'/.bashrc'*
> - **Korn Shell**: *'/.kshrc* ou *.profil*
> - **Z Shell**: *'/.zshrc* ou *.zprofile*
>
> Modifiez le fichier source approprié `:$HOME/dotnet` pour votre coque `PATH` et ajoutez à la fin de l’instruction existante. Si `PATH` aucune déclaration n’est incluse, ajoutez une nouvelle ligne avec `export PATH=$PATH:$HOME/dotnet`.
>
> En outre, ajouter `export DOTNET_ROOT=$HOME/dotnet` à la fin du fichier.

Cette approche vous permet d’installer différentes versions dans des endroits distincts et de choisir explicitement celle à utiliser par quelle application.

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Installer avec l’automatisation PowerShell

Les [scripts d’installation de dotnet](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non admin de l’heure d’exécution. Vous pouvez télécharger le script à partir de la page de [référence de script dotnet-install](../tools/dotnet-install-script.md).

Le script par défaut à l’installation de la dernière [version de support à long terme (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) qui est .NET Core 3.1. Vous pouvez choisir une version `Channel` spécifique en spécifiant le commutateur. Inclure `Runtime` le commutateur pour installer un temps d’exécution. Sinon, le script installe le [SDK](sdk.md).

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> La commande ci-dessus installe le temps de course ASP.NET Core pour une compatibilité maximale. Le temps d’exécution ASP.NET Core comprend également le temps d’exécution standard .NET Core.

## <a name="download-and-manually-install"></a>Télécharger et installer manuellement

Pour extraire l’heure d’exécution et rendre disponibles les commandes CLI de base .NET au terminal, [téléchargez](#all-net-core-downloads) d’abord une version binaire .NET Core. Ensuite, créez un répertoire à installer, par exemple. `%USERPROFILE%\dotnet` Enfin, extraire le fichier zip téléchargé dans ce répertoire.

Par défaut, les commandes et les applications CLI de base .NET n’utiliseront pas le noyau .NET installé de cette façon. Vous devez choisir explicitement de l’utiliser. Pour ce faire, modifiez les variables de l’environnement avec lesquelles une application est lancée :

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

Cette approche vous permet d’installer plusieurs versions dans des endroits distincts, puis de choisir explicitement l’emplacement d’installation qu’une application doit utiliser en exécutant l’application avec des variables d’environnement pointant vers cet endroit.

Même lorsque ces variables d’environnement sont définies, .NET Core tient toujours compte de l’emplacement d’installation global par défaut lors de la sélection du meilleur cadre pour l’exécution de l’application. La valeur `C:\Program Files\dotnet`par défaut est généralement, que les installateurs utilisent. Vous pouvez demander à l’heure d’exécution d’utiliser uniquement l’emplacement d’installation personnalisé en définissant cette variable d’environnement ainsi:

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Installer avec l’automatisation bash

Les [scripts d’installation de dotnet](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non admin de l’heure d’exécution. Vous pouvez télécharger le script à partir de la page de [référence de script dotnet-install](../tools/dotnet-install-script.md).

Le script par défaut à l’installation de la dernière [version de support à long terme (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) qui est .NET Core 3.1. Vous pouvez choisir une version `current` spécifique en spécifiant le commutateur. Inclure `runtime` le commutateur pour installer un temps d’exécution. Sinon, le script installe le [SDK](sdk.md).

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> La commande ci-dessus installe le temps de course ASP.NET Core pour une compatibilité maximale. Le temps d’exécution ASP.NET Core comprend également le temps d’exécution standard .NET Core.

::: zone-end

## <a name="all-net-core-downloads"></a>Tous les téléchargements .NET Core

Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants:

- [.NET Core 3.1 téléchargements](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [.NET Core 2.1 téléchargements](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Les conteneurs fournissent un moyen léger d’isoler votre application du reste du système hôte. Les conteneurs de la même machine ne partagent que le noyau et utilisent les ressources données à votre application.

.NET Core peut fonctionner dans un conteneur Docker. Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/). Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.

Microsoft fournit des images adaptées à des scénarios particuliers. Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.

Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur Docker, voir [Introduction à .NET et Docker](../docker/introduction.md) et [Échantillons](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Étapes suivantes

- [Comment vérifier si .NET Core est déjà installé](how-to-detect-installed-versions.md).
