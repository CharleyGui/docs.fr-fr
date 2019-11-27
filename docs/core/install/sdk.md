---
title: Installer kit SDK .NET Core sur Windows, Linux et macOS-.NET Core
description: Découvrez comment installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances requises pour développer des applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 2f65e9dc39a4cd1076af1a70dfedfa671f20b42d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450876"
---
# <a name="install-the-net-core-sdk"></a>Installer le kit SDK .NET Core

Dans cet article, vous allez apprendre à installer le kit SDK .NET Core. Le kit SDK .NET Core est utilisé pour créer des applications et des bibliothèques .NET Core. Le Runtime .NET Core est toujours installé avec le kit de développement logiciel (SDK).

Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants :

- [Téléchargements .NET Core 3,1 Preview 3](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Téléchargements .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [Téléchargements .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [Téléchargements .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

Vous pouvez également installer .NET Core dans le cadre d’un environnement de développement intégré (IDE), détaillé dans les sections ci-dessous.

## <a name="install-with-an-installer"></a>Installer avec un programme d’installation

Windows et macOS ont tous deux des programmes d’installation autonomes qui peuvent être utilisés pour installer le kit de développement logiciel (SDK) .NET Core 3,0.

- UC Windows [x64](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x64-installer) | [UC x32](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x86-installer)
- [processeurs MacOS x64](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-macos-x64-installer)

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Installer avec un gestionnaire de package

Vous pouvez installer les kit SDK .NET Core avec un grand nombre de gestionnaires de packages Linux courants. Pour plus d’informations, consultez [Linux Package Manager-install .net Core](linux-package-manager-rhel7.md).

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a>Installer avec Visual Studio

Si vous utilisez Visual Studio pour développer des applications .NET Core, le tableau suivant décrit la version minimale requise de Visual Studio en fonction de la version de kit SDK .NET Core cible.

| Version de kit SDK .NET Core | Version de Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 3,0                   | Visual Studio 2019 version 16,3 ou ultérieure. |
| 2.2                   | Visual Studio 2017 version 15,9 ou ultérieure. |
| 2.1                   | Visual Studio 2017 version 15,7 ou ultérieure. |

Si vous avez déjà installé Visual Studio, vous pouvez vérifier votre version en procédant comme suit.

01. Ouvrez Visual Studio.
01. Sélectionnez **aide** > **à propos de Microsoft Visual Studio**.
01. Lisez le numéro de version dans la boîte de dialogue **à propos** de.

Visual Studio peut installer les kit SDK .NET Core et Runtime les plus récents.

- [Téléchargez Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).

### <a name="select-a-workload"></a>Sélectionner une charge de travail

Lors de l’installation ou de la modification de Visual Studio, sélectionnez l’une des charges de travail suivantes, selon le type d’application que vous créez :

- La charge de travail **développement multiplateforme .net Core** dans la section **autres ensembles d’outils** .
- La charge de travail **ASP.net et développement Web** dans la section **Web & Cloud** .
- La charge de travail **développement Azure** dans la section **Web & Cloud** .
- La charge de travail **développement .net Desktop** dans la section **Desktop & mobile** .

[![Windows Visual Studio 2019 avec charge de travail .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a>Installer avec Visual Studio pour Mac

Visual Studio pour Mac installe le kit SDK .NET Core lorsque la charge de travail **.net Core** est sélectionnée. Pour commencer à utiliser le développement .NET Core sur macOS, consultez [installer Visual Studio 2019 pour Mac](/visualstudio/mac/installation).

[![la fonctionnalité de charge de travail de Visual Studio 2019 pour Mac macOS avec .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

::: zone-end

## <a name="install-from-visual-studio-code"></a>Installer à partir de Visual Studio Code

Visual Studio Code est un éditeur de code source puissant et léger qui s’exécute sur votre bureau. Visual Studio Code est disponible pour Windows, macOS et Linux.

Même si Visual Studio Code n’est pas fourni avec la prise en charge de .NET Core, l’ajout de la prise en charge de .NET Core est simple.

01. [Téléchargez et installez Visual Studio code](https://code.visualstudio.com/Download).
01. [Téléchargez et installez le kit SDK .net Core](https://dotnet.microsoft.com/download/dotnet-core/3.0).
01. [Installez l' C# extension à partir de la place de marché Visual Studio code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Installer avec l’automatisation PowerShell

Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du kit de développement logiciel (SDK). Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).

Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 2,1. Pour installer la version actuelle de .NET Core, exécutez le script avec le commutateur suivant.

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Installer avec l’automatisation bash

Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du kit de développement logiciel (SDK). Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).

Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 2,1. Pour installer la version actuelle de .NET Core, exécutez le script avec le commutateur suivant.

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

::: zone pivot="os-windows"

- [Didacticiel : C# Hello World didacticiel](../tutorials/with-visual-studio.md).
- [Didacticiel : Visual Basic Hello World didacticiel](../tutorials/vb-with-visual-studio.md).
- [Didacticiel : créer une application avec Visual Studio code](https://code.visualstudio.com/docs/languages/dotnet).
- [Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).

::: zone-end

::: zone pivot="os-macos"

- [Didacticiel : prise en main de MacOS](../tutorials/using-on-mac-vs.md).
- [Didacticiel : créer une application avec Visual Studio code](https://code.visualstudio.com/docs/languages/dotnet).
- [Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).

::: zone-end
