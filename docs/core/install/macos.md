---
title: Installer .NET sur macOS
description: En savoir plus sur les versions de macOS sur lesquelles vous pouvez installer .NET.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 871263b820aaf4cc04e573dd4aa3022caa401857
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506303"
---
# <a name="install-net-on-macos"></a>Installer .NET sur macOS

> [!div class="op_single_selector"]
>
> - [Installer sur Windows](windows.md)
> - [Installer sur macOS](macos.md)
> - [Installer sur Linux](linux.md)

Dans cet article, vous allez apprendre à installer .NET sur macOS. .NET est constitué du runtime et du kit de développement logiciel (SDK). Le runtime est utilisé pour exécuter une application .NET et peut ou non être inclus avec l’application. Le kit de développement logiciel (SDK) est utilisé pour créer des applications et des bibliothèques .NET. Le Runtime .NET est toujours installé avec le kit de développement logiciel (SDK).

La dernière version de .NET est 5,0.

> [!div class="button"]
> [Télécharger .NET Core](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a>Versions prises en charge

Le tableau suivant répertorie les versions de .NET actuellement prises en charge et les versions de macOS sur lesquelles elles sont prises en charge. Ces versions restent prises en charge soit la version de [.net atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

- Une ✔️ indique que la version de .NET Core est toujours prise en charge.
- Une ❌ indique que la version de .net Core n’est pas prise en charge.

| Système d’exploitation          | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|---------------------------|---------------|---------------|----------------|
| macOS 11,0 « Big sur »        | ✔️ 2,1 ([notes de publication][release-notes-21]) | ✔️ 3,1 ([notes de publication][release-notes-31]) | ✔️ 5,0 ([notes de publication][release-notes-50]) |
| macOS 10.15 « Catalina »    | ✔️ 2,1 ([notes de publication][release-notes-21]) | ✔️ 3,1 ([notes de publication][release-notes-31]) | ✔️ 5,0 ([notes de publication][release-notes-50]) |
| macOS 10.14 « Mojave »      | ✔️ 2,1 ([notes de publication][release-notes-21]) | ✔️ 3,1 ([notes de publication][release-notes-31]) | ✔️ 5,0 ([notes de publication][release-notes-50]) |
| macOS 10.13 « High Sierra » | ✔️ 2,1 ([notes de publication][release-notes-21]) | ✔️ 3,1 ([notes de publication][release-notes-31]) | ✔️ 5,0 ([notes de publication][release-notes-50]) |
| macOS 10.12 "Sierra"      | ✔️ 2,1 ([notes de publication][release-notes-21]) | ❌ 3,1 ([notes de publication][release-notes-31]) | ❌ 5,0 ([notes de publication][release-notes-50]) |

## <a name="unsupported-releases"></a>Mises en production non prises en charge

Les versions suivantes de .NET ne sont ❌ plus prises en charge. Les téléchargements sont toujours publiés :

- 3,0 ([notes de publication][release-notes-30])
- 2,2 ([notes de publication][release-notes-22])
- 2,0 ([notes de publication][release-notes-20])

## <a name="runtime-information"></a>Informations d’exécution

Le runtime est utilisé pour exécuter des applications créées avec .NET. Quand un auteur d’application publie une application, il peut inclure le Runtime avec son application. Si elles n’incluent pas le runtime, c’est à l’utilisateur d’installer le Runtime.

Il existe deux runtimes différents que vous pouvez installer sur macOS :

- *Runtime ASP.NET Core*\
  Exécute ASP.NET Core applications. Comprend le Runtime .NET.

- *Runtime .NET*\
  Ce Runtime est le runtime le plus simple et n’inclut pas d’autre Runtime. Il est fortement recommandé d’installer *ASP.net Core Runtime* pour une meilleure compatibilité avec les applications .net.

> [!div class="button"]
> [Télécharger le Runtime .NET](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a>Informations sur le SDK

Le kit de développement logiciel (SDK) est utilisé pour générer et publier des applications et des bibliothèques .NET. L’installation du kit de développement logiciel (SDK) comprend les deux [runtimes](#runtime-information): ASP.net Core et .net.

## <a name="dependencies"></a>Les dépendances

.NET est pris en charge sur les versions macOS suivantes :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Version de .NET Core | macOS                 | Architectures | Informations complémentaires    |
| ----------------- | --------------------- | --------------| --- |
| 5.0               | High Sierra (10.13 +)  | x64 | [Plus d’informations](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md) |
| 3.1               | High Sierra (10.13 +)  | x64 | [Plus d’informations](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | High Sierra (10.13 +)  | x64 | [Plus d’informations](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | Sierra (10.12 +)       | x64 | [Plus d’informations](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | Sierra (10.12 +)       | x64 | [Plus d’informations](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

À partir de macOS Catalina (version 10,15), tous les logiciels générés après le 1er juin 2019, qui sont distribués avec l’ID de développeur, doivent être certifiés. Cette exigence s’applique au Runtime .NET, au kit de développement logiciel (SDK) .NET et aux logiciels créés avec .NET.

Les programmes d’installation du runtime et du SDK pour .NET 5,0 et .NET Core 3,1, 3,0 et 2,1 ont été certifiés depuis le 18 février 2020. Les versions antérieures publiées ne sont pas certifiées. Si vous exécutez une application non authentifiée, une erreur semblable à l’image suivante s’affiche :

![alerte de notaire Catalina macOS](media/dependencies/macos-notarized-pkg-warning.png)

Pour plus d’informations sur la façon dont l’application de la notaire affecte .NET (et vos applications .NET), consultez [utilisation de la méthode de notaire Catalina MacOS](macos-notarization-issues.md).

## <a name="libgdiplus"></a>libgdiplus

Les applications .NET qui utilisent l’assembly *System. Drawing. Common* nécessitent l’installation de libgdiplus.

Pour obtenir facilement des libgdiplus, vous pouvez utiliser le gestionnaire de package [Homebrew (« Brass »)](https://brew.sh/) pour MacOS. Après l’installation de la commande *infuse*, installez libgdiplus en exécutant les commandes suivantes à une invite de commandes :

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a>Installer avec un programme d’installation

macOS possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le kit de développement logiciel (SDK) .NET 5,0 :

- [Processeurs x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/5.0)

## <a name="download-and-manually-install"></a>Télécharger et installer manuellement

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

Comme alternative aux programmes d’installation macOS pour .NET, vous pouvez télécharger et installer manuellement le kit de développement logiciel (SDK) et le Runtime. L’installation manuelle est généralement effectuée dans le cadre du test d’intégration continue. Pour un développeur ou un utilisateur, il est généralement préférable d’utiliser un [programme d’installation](https://dotnet.microsoft.com/download/dotnet-core).

Si vous installez le kit de développement logiciel (SDK) .NET, vous n’avez pas besoin d’installer le runtime correspondant. Tout d’abord, téléchargez une version **binaire** pour le kit de développement logiciel (SDK) ou le runtime à partir de l’un des sites suivants :

- [téléchargements .net 5,0](https://dotnet.microsoft.com/download/dotnet/5.0) ✔️
- ✔️ [téléchargements .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [téléchargements .net Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [Tous les téléchargements .NET Core](https://dotnet.microsoft.com/download/dotnet-core)

Ensuite, extrayez le fichier téléchargé et utilisez la `export` commande pour définir les variables utilisées par .net, puis vérifiez que .net est dans le chemin d’accès.

Pour extraire le runtime et rendre les commandes de l’interface de commande .NET CLI disponibles sur le terminal, commencez par télécharger une version binaire .NET. Ensuite, ouvrez un terminal et exécutez les commandes suivantes à partir du répertoire dans lequel le fichier a été enregistré. Le nom du fichier d’archive peut être différent en fonction de ce que vous avez téléchargé.

**Utilisez les commandes suivantes pour extraire le runtime ou le kit de développement logiciel (SDK) que vous avez téléchargé.** N’oubliez pas de remplacer la `DOTNET_FILE` valeur par votre nom de fichier :

```bash
DOTNET_FILE=dotnet-sdk-5.0.102-linux-x64.tar.gz
export DOTNET_ROOT=$HOME/dotnet

mkdir -p "$DOTNET_ROOT" && tar zxf "$DOTNET_FILE" -C "$DOTNET_ROOT"

export PATH=$PATH:$DOTNET_ROOT
```

> [!TIP]
> Les `export` commandes précédentes rendent uniquement les commandes de l’interface de commande .net CLI disponibles pour la session Terminal dans laquelle elle a été exécutée.
>
> Vous pouvez modifier votre profil de Shell pour ajouter définitivement les commandes. Un certain nombre de shells différents sont disponibles pour Linux et chacun d’eux a un profil différent. Par exemple :
>
> - **Interpréteur** de commandes bash : *~/.bash_profile*, *~ fichier/.bashrc*
> - **Shell Korn**: *~/.kshrc* ou *. Profile*
> - **Z Shell**: *~/.zshrc* ou *. zprofile*
>
> Modifiez le fichier source approprié pour votre shell et ajoutez `:$HOME/dotnet` à la fin de l' `PATH` instruction existante. Si aucune `PATH` instruction n’est incluse, ajoutez une nouvelle ligne avec `export PATH=$PATH:$HOME/dotnet` .
>
> Ajoutez également `export DOTNET_ROOT=$HOME/dotnet` à la fin du fichier.

Cette approche vous permet d’installer différentes versions dans des emplacements distincts et de choisir explicitement celle qui doit être utilisée par l’application.

## <a name="install-with-visual-studio-for-mac"></a>Installer avec Visual Studio pour Mac

Visual Studio pour Mac installe le kit de développement logiciel (SDK) .NET lorsque la charge de travail **.net** est sélectionnée. Pour commencer à utiliser le développement .NET sur macOS, consultez [installer Visual Studio 2019 pour Mac](/visualstudio/mac/installation).

| Version du Kit de développement logiciel (SDK) .NET      | Version de Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 5.0                   | Visual Studio 2019 pour Mac version 8,8 ou ultérieure. |
| 3.1                   | Visual Studio 2019 pour Mac version 8,4 ou ultérieure. |
| 2.1                   | Visual Studio 2019 pour Mac version 8,0 ou ultérieure. |

[![fonctionnalité de charge de travail de macOS Visual Studio 2019 pour Mac avec .NET](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

## <a name="install-alongside-visual-studio-code"></a>Installer en même temps que Visual Studio Code

Visual Studio Code est un éditeur de code source puissant et léger qui s’exécute sur votre bureau. Visual Studio Code est disponible pour Windows, macOS et Linux.

Même si Visual Studio Code n’est pas fourni avec un programme d’installation automatisé de .NET, comme Visual Studio, l’ajout de la prise en charge de .NET est simple.

01. [Téléchargez et installez Visual Studio code](https://code.visualstudio.com/Download).
01. [Téléchargez et installez le kit de développement logiciel (SDK) .net](https://dotnet.microsoft.com/download/dotnet-core).
01. [Installez l’extension C# à partir de la place de marché Visual Studio code](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).

## <a name="install-with-bash-automation"></a>Installer avec l’automatisation bash

Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime. Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).

Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1. Vous pouvez choisir une version spécifique en spécifiant le `current` commutateur. Incluez le `runtime` commutateur pour installer un Runtime. Dans le cas contraire, le script installe le [Kit de développement logiciel (SDK)](./windows.md).

```bash
./dotnet-install.sh --channel 5.0 --runtime aspnetcore
```

> [!NOTE]
> La commande précédente installe le runtime ASP.NET Core pour une compatibilité maximale. Le runtime ASP.NET Core comprend également le Runtime .NET standard.

## <a name="docker"></a>Docker

Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte. Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.

.NET peut s’exécuter dans un conteneur d’ancrage. Les images officielles de la station d’accueil .NET sont publiées dans le Container Registry Microsoft et sont détectables dans le [référentiel du hub d’ancrage Microsoft .net Core](https://hub.docker.com/_/microsoft-dotnet/). Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.

Microsoft fournit des images adaptées à des scénarios particuliers. Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-aspnet) sont conçues pour exécuter des applications ASP.NET Core en production.

Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Étapes suivantes

- [Comment vérifier si .net Core est déjà installé](how-to-detect-installed-versions.md?pivots=os-macos).
- [Utilisation de la notaire Catalina MacOS](macos-notarization-issues.md).
- [Didacticiel : prise en main de MacOS](../tutorials/with-visual-studio-mac.md).
- [Didacticiel : créer une application avec Visual Studio code](../tutorials/with-visual-studio-code.md).
- [Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
