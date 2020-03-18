---
title: Installer .NET Core SDK sur Windows, Linux et macOS - .NET Core
description: Apprenez à installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances nécessaires au développement d’applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 13600ea01e18ad47e6295653ba3b79ce53ff3257
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399006"
---
# <a name="install-the-net-core-sdk"></a>Installer le kit de développement logiciel (SDK) .NET Core

Dans cet article, vous apprendrez à installer le .NET Core SDK. Le .NET Core SDK est utilisé pour créer des applications et des bibliothèques .NET Core. Le temps d’exécution .NET Core est toujours installé avec le SDK.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Installer avec un installateur

Windows a des installateurs autonomes qui peuvent être utilisés pour installer le .NET Core 3.1 SDK:

- [x64 (64 bits) DPC](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [x86 (32 bits) CPU](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Installer avec un installateur

macOS a des installateurs autonomes qui peuvent être utilisés pour installer le .NET Core 3.1 SDK:

- [x64 (64 bits) DPC](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>Télécharger et installer manuellement

Comme alternative aux installateurs macOS pour .NET Core, vous pouvez télécharger et installer manuellement le SDK.

Pour extraire le SDK et rendre disponibles les commandes CLI .NET Core au terminal, [téléchargez](#all-net-core-downloads) d’abord une version binaire .NET Core. Ensuite, ouvrez un terminal et exécutez les commandes suivantes. On suppose que le temps d’exécution est téléchargé sur le `~/Downloads/dotnet-sdk.pkg` fichier.

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Installer avec un gestionnaire de paquets

Vous pouvez installer le .NET Core SDK avec de nombreux gestionnaires de paquets Linux communs. Pour plus d’informations, voir [Linux Package Manager - Install .NET Core](linux-package-managers.md).

L’installation avec un gestionnaire de paquets n’est pris en charge que sur l’architecture x64. Si vous installez le .NET Core SDK avec une architecture différente, comme ARM, suivez le [Télécharger et installer manuellement](#download-and-manually-install) des instructions ci-dessous. Pour plus d’informations sur les architectures qui sont prises en charge, voir [.NET Core dépendances et les exigences](dependencies.md).

## <a name="download-and-manually-install"></a>Télécharger et installer manuellement

Pour extraire le SDK et rendre disponibles les commandes CLI .NET Core au terminal, [téléchargez](#all-net-core-downloads) d’abord une version binaire .NET Core. Ensuite, ouvrez un terminal et exécutez les commandes suivantes.

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
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

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a>Installer avec Visual Studio

Si vous utilisez Visual Studio pour développer des applications .NET Core, le tableau suivant décrit la version minimale requise de Visual Studio en fonction de la version SDK target .NET Core.

| version SDK Core .NET | Version de Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 3.1                   | Visual Studio 2019 version 16.4 ou plus. |
| 3.0                   | Visual Studio 2019 version 16.3 ou plus. |
| 2.2                   | Visual Studio 2017 version 15.9 ou plus. |
| 2.1                   | Visual Studio 2017 version 15.7 ou plus. |

Si vous avez déjà Visual Studio installé, vous pouvez vérifier votre version avec les étapes suivantes.

01. Ouvrez Visual Studio.
01. Sélectionnez > **l’aide sur Microsoft Visual Studio**. **Help**
01. Lisez le numéro de version du **Dialogue About.**

Visual Studio peut installer le dernier .NET Core SDK et l’heure d’exécution.

- [Télécharger Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).

### <a name="select-a-workload"></a>Sélectionnez une charge de travail

Lors de l’installation ou de la modification de Visual Studio, sélectionnez une ou plusieurs des charges de travail suivantes, selon le type d’application que vous construisez :

- La charge de travail **de développement multiplateforme .NET Core** dans la section Autres **outils.**
- La charge de travail **de développement ASP.NET et Web** dans la section Web & **Cloud.**
- La charge de travail **de développement Azure** dans la section **Web & Cloud.**
- La charge de travail **de développement de bureau .NET** dans la section Desktop & **Mobile.**

[![Windows Visual Studio 2019 avec .NET Core charge de travail](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

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

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a>Installer avec Visual Studio pour Mac

Visual Studio pour Mac installe le .NET Core SDK lorsque la charge de travail **.NET Core** est sélectionnée. Pour commencer avec .NET Core développement sur macOS, voir [Installer Visual Studio 2019 pour Mac](/visualstudio/mac/installation). Pour la dernière version, .NET Core 3.1, vous devez utiliser le Visual Studio pour Mac 8.4 Aperçu.

[![macOS Visual Studio 2019 pour Mac avec une fonction de charge de travail .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

::: zone-end

## <a name="install-alongside-visual-studio-code"></a>Installer aux côtés de Visual Studio Code

Visual Studio Code est un éditeur de code source puissant et léger qui s’exécute sur votre bureau. Visual Studio Code est disponible pour Windows, macOS et Linux.

Bien que Visual Studio Code ne soit pas livré avec un installateur .NET Core automatisé comme Visual Studio, l’ajout de support .NET Core est simple.

01. [Téléchargez et installez Visual Studio Code](https://code.visualstudio.com/Download).
01. [Téléchargez et installez le .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).
01. [Installez l’extension Cmd à partir du marché du code de studio visuel.](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Installer avec l’automatisation PowerShell

Les [scripts d’installation de dotnet](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non admin du SDK. Vous pouvez télécharger le script à partir de la page de [référence de script dotnet-install](../tools/dotnet-install-script.md).

Le script par défaut à l’installation de la dernière [version de support à long terme (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) qui est .NET Core 3.1. Pour installer la version actuelle de .NET Core, exécutez le script avec le commutateur suivant.

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Installer avec l’automatisation bash

Les [scripts d’installation de dotnet](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non admin du SDK. Vous pouvez télécharger le script à partir de la page de [référence de script dotnet-install](../tools/dotnet-install-script.md).

Le script par défaut à l’installation de la dernière [version de support à long terme (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) qui est .NET Core 3.1. Pour installer la version actuelle de .NET Core, exécutez le script avec le commutateur suivant.

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a>Tous les téléchargements .NET Core

Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants:

- [.NET Core 3.1 téléchargements](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [.NET Core 3.0 téléchargements](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [.NET Core 2.2 téléchargements](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [.NET Core 2.1 téléchargements](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Les conteneurs fournissent un moyen léger d’isoler votre application du reste du système hôte. Les conteneurs de la même machine ne partagent que le noyau et utilisent les ressources données à votre application.

.NET Core peut fonctionner dans un conteneur Docker. Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/). Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.

Microsoft fournit des images adaptées à des scénarios particuliers. Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.

Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur Docker, voir [Introduction à .NET et Docker](../docker/introduction.md) et [Échantillons](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Étapes suivantes

::: zone pivot="os-windows"

- [Tutorial: Bonjour World tutoriel](../tutorials/with-visual-studio.md).
- [Tutorial: Créer une nouvelle application avec Visual Studio Code](../tutorials/with-visual-studio-code.md).
- [Tutorial: Containerize a .NET Core app](../docker/build-container.md).

::: zone-end

::: zone pivot="os-macos"

- [Travailler avec macOS Catalina notarisation](macos-notarization-issues.md).
- [Tutorial: Démarrer sur macOS](../tutorials/using-on-mac-vs.md).
- [Tutorial: Créer une nouvelle application avec Visual Studio Code](../tutorials/with-visual-studio-code.md).
- [Tutorial: Containerize a .NET Core app](../docker/build-container.md).

::: zone-end

::: zone pivot="os-linux"

- [Tutorial: Créer une nouvelle application avec Visual Studio Code](../tutorials/with-visual-studio-code.md).
- [Tutorial: Containerize a .NET Core app](../docker/build-container.md).

::: zone-end
