---
title: Outils .NET Core
description: Comment installer, utiliser, mettre à jour et supprimer les outils .NET Core. Décrit les outils globaux, les outils de chemin d’accès d’outil et les outils locaux.
author: KathleenDollard
ms.date: 02/12/2020
ms.openlocfilehash: d8ee30df3fe063fd41a85072d145b1b5eec7d0d0
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543389"
---
# <a name="how-to-manage-net-core-tools"></a>Comment gérer les outils .NET Core

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

Un outil .NET Core est un package NuGet spécial qui contient une application console. Un outil peut être installé sur votre ordinateur de l’une des manières suivantes :

* Comme un outil Global.

  Les fichiers binaires de l’outil sont installés dans un répertoire par défaut qui est ajouté à la variable d’environnement PATH. Vous pouvez appeler l’outil à partir de n’importe quel répertoire sur l’ordinateur sans spécifier son emplacement. Une version d’un outil est utilisée pour tous les répertoires sur l’ordinateur.

* En tant qu’outil Global dans un emplacement personnalisé (également appelé outil de chemin d’accès d’outil).

  Les fichiers binaires de l’outil sont installés dans un emplacement que vous spécifiez. Vous pouvez appeler l’outil à partir du répertoire d’installation ou en fournissant le répertoire avec le nom de commande ou en ajoutant le répertoire à la variable d’environnement PATH. Une version d’un outil est utilisée pour tous les répertoires sur l’ordinateur.

* En tant qu’outil local (s’applique à kit SDK .NET Core 3,0 et versions ultérieures).

  Les fichiers binaires de l’outil sont installés dans un répertoire par défaut. Vous appelez l’outil à partir du répertoire d’installation ou de l’un de ses sous-répertoires. Différents répertoires peuvent utiliser différentes versions du même outil.
  
  L’interface CLI .NET utilise des fichiers manifeste pour suivre les outils qui sont installés en tant qu’outils locaux dans un répertoire. Lorsque le fichier manifeste est enregistré dans le répertoire racine d’un référentiel de code source, un contributeur peut cloner le référentiel et appeler une seule commande CLI .NET Core qui installe tous les outils listés dans les fichiers manifeste.

> [!IMPORTANT]
> Les outils .NET Core s’exécutent en mode confiance totale. N’installez pas d’outil .NET Core, sauf si vous faites confiance à l’auteur.

## <a name="find-a-tool"></a>Rechercher un outil

Actuellement, .NET Core ne dispose pas d’une fonctionnalité de recherche d’outils. Voici quelques méthodes pour trouver des outils :

* Consultez la liste des outils dans le référentiel GitHub [natemcmaster/dotnet-Tools](https://github.com/natemcmaster/dotnet-tools) .
* Utilisez [ToolGet](https://www.toolget.net/) pour rechercher des outils .net.
* Consultez le code source des outils créés par l’équipe ASP.NET Core dans le [répertoire Tools du référentiel GitHub dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).
* Découvrez les outils de diagnostics dans les [outils de diagnostic dotnet .net Core](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).
* Recherchez le site Web [NuGet](https://www.nuget.org) . Toutefois, le site NuGet ne dispose pas encore d’une fonctionnalité qui vous permet de rechercher uniquement les packages d’outils.

## <a name="check-the-author-and-statistics"></a>Vérifier l’auteur et les statistiques

Étant donné que les outils .NET Core s’exécutent en mode de confiance totale et que les outils globaux sont ajoutés à la variable d’environnement PATH, ils peuvent être très puissants. Par conséquent, ne téléchargez pas d’outils provenant de personnes en qui vous n’avez pas confiance.

Si l’outil est hébergé sur NuGet, vous pouvez vérifier l’auteur et les statistiques en recherchant l’outil.

## <a name="install-a-global-tool"></a>Installer un outil Global

Pour installer un outil comme un outil Global, utilisez l’option `-g` ou `--global` de l’installation de l' [outil dotnet](dotnet-tool-install.md), comme indiqué dans l’exemple suivant :

```dotnetcli
dotnet tool install -g dotnetsay
```

La sortie affiche la commande utilisée pour appeler l’outil et la version installée, similaire à l’exemple suivant :

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

L’emplacement par défaut des binaires d’un outil dépend du système d’exploitation :

| Système d''exploitation          | Path                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Cet emplacement est ajouté au chemin d’accès de l’utilisateur lors de la première exécution du kit de développement logiciel (SDK), de sorte que les outils globaux peuvent être appelés à partir de n’importe quel répertoire sans spécifier l’emplacement de l’outil.

L’accès aux outils est spécifique à l’utilisateur, et non à l’ordinateur global. Un outil Global est uniquement disponible pour l’utilisateur qui a installé l’outil.

### <a name="install-a-global-tool-in-a-custom-location"></a>Installer un outil Global dans un emplacement personnalisé

Pour installer un outil comme un outil Global dans un emplacement personnalisé, utilisez l’option `--tool-path` de l’installation de l' [outil dotnet](dotnet-tool-install.md), comme indiqué dans les exemples suivants.

Sur Windows :

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

Sur Linux ou macOS :

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

La kit SDK .NET Core n’ajoute pas cet emplacement automatiquement à la variable d’environnement PATH. Pour [appeler un outil de chemin d’accès d’outil](#invoke-a-tool-path-tool), vous devez vous assurer que la commande est disponible à l’aide de l’une des méthodes suivantes :

* Ajoutez le répertoire d’installation à la variable d’environnement PATH.
* Spécifiez le chemin d’accès complet à l’outil lorsque vous l’appelez.
* Appelez l’outil à partir du répertoire d’installation.

## <a name="install-a-local-tool"></a>Installer un outil local

**S’applique au kit de développement logiciel (SDK) .NET Core 3,0 et versions ultérieures.**

Pour installer un outil pour un accès local uniquement (pour le répertoire et les sous-répertoires actifs), il doit être ajouté à un fichier manifeste de l’outil. Pour créer un fichier de manifeste d’outil, exécutez la commande `dotnet new tool-manifest` :

```dotnetcli
dotnet new tool-manifest
```

Cette commande crée un fichier manifeste nommé *dotnet-Tools. JSON* dans le répertoire *. config* . Pour ajouter un outil local au fichier manifeste, utilisez la commande d’installation de l' [outil dotnet](dotnet-tool-install.md) et **omettez** les options `--global` et `--tool-path`, comme indiqué dans l’exemple suivant :

```dotnetcli
dotnet tool install dotnetsay
```

La sortie de la commande indique le fichier manifeste dans lequel se trouve l’outil qui vient d’être installé, comme dans l’exemple suivant :

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

L’exemple suivant montre un fichier manifeste avec deux outils locaux installés :

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    },
    "dotnetsay": {
      "version": "2.1.3",
      "commands": [
        "dotnetsay"
      ]
    }
  }
}
```

En général, vous ajoutez un outil local au répertoire racine du référentiel. Après avoir vérifié le fichier manifeste dans le référentiel, les développeurs qui récupèrent le code à partir du référentiel obtiennent le dernier fichier manifeste. Pour installer tous les outils listés dans le fichier manifeste, ils exécutent la commande `dotnet tool restore` :

```dotnetcli
dotnet tool restore
```

La sortie indique les outils qui ont été restaurés :

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a>Installer une version d’outil spécifique

Pour installer une version préliminaire ou une version spécifique d’un outil, spécifiez le numéro de version à l’aide de l’option `--version`, comme indiqué dans l’exemple suivant :

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a>Utiliser un outil

La commande que vous utilisez pour appeler un outil peut être différente du nom du package que vous installez. Pour afficher tous les outils actuellement installés sur l’ordinateur pour l’utilisateur actuel, utilisez la commande de [liste d’outils dotnet](dotnet-tool-list.md) :

```dotnetcli
dotnet tool list
```

La sortie affiche la version et la commande de chaque outil, comme dans l’exemple suivant :

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

Comme indiqué dans cet exemple, la liste affiche les outils locaux. Pour afficher les outils globaux, utilisez l’option `--global` et pour consulter les outils de chemin d’accès d’outil, utilisez l’option `--tool-path`.

### <a name="invoke-a-global-tool"></a>Appeler un outil Global

Pour les outils globaux, utilisez la commande d’outil seule. Par exemple, si la commande est `dotnetsay` ou `dotnet-doc`, c’est ce que vous utilisez pour appeler la commande :

```console
dotnetsay
dotnet-doc
```

Si la commande commence par le préfixe `dotnet-`, une autre façon d’appeler l’outil consiste à utiliser la commande `dotnet` et à omettre le préfixe de commande d’outil. Par exemple, si la commande est `dotnet-doc`, la commande suivante appelle l’outil :

```dotnetcli
dotnet doc
```

Toutefois, dans le scénario suivant, vous ne pouvez pas utiliser la commande `dotnet` pour appeler un outil Global :

* Un outil Global et un outil local ont la même commande préfixée par `dotnet-`.
* Vous souhaitez appeler l’outil Global à partir d’un répertoire qui se trouve dans l’étendue de l’outil local.

Dans ce scénario, `dotnet doc` et `dotnet dotnet-doc` appeler l’outil local. Pour appeler l’outil Global, utilisez la commande seule :

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a>Appeler un outil de chemin d’accès d’outil

Pour appeler un outil global qui est installé à l’aide de l’option `tool-path`, assurez-vous que la commande est disponible, comme expliqué [plus haut dans cet article](#install-a-global-tool-in-a-custom-location).

### <a name="invoke-a-local-tool"></a>Appeler un outil local

Pour appeler un outil local, vous devez utiliser la commande `dotnet` à partir du répertoire d’installation. Vous pouvez utiliser la forme longue (`dotnet tool run <COMMAND_NAME>`) ou la forme abrégée (`dotnet <COMMAND_NAME>`), comme indiqué dans les exemples suivants :

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

Si la commande est préfixée par `dotnet-`, vous pouvez inclure ou omettre le préfixe lorsque vous appelez l’outil. Par exemple, si la commande est `dotnet-doc`, l’un des exemples suivants appelle l’outil local :

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a>Mettre à jour un outil

La mise à jour d’un outil implique sa désinstallation et sa réinstallation avec la dernière version stable. Pour mettre à jour un outil, utilisez la commande de [mise à jour de l’outil dotnet](dotnet-tool-update.md) avec la même option que celle utilisée pour installer l’outil :

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

Pour un outil local, le kit de développement logiciel (SDK) recherche le premier fichier manifeste qui contient l’ID de package en examinant le répertoire actif et les répertoires parents. S’il n’existe aucun ID de package de ce type dans un fichier manifeste, le kit de développement logiciel (SDK) ajoute une nouvelle entrée au fichier manifeste le plus proche.

## <a name="uninstall-a-tool"></a>Désinstaller un outil

Supprimez un outil à l’aide de la commande de [désinstallation de l’outil dotnet](dotnet-tool-uninstall.md) avec la même option que celle utilisée pour installer l’outil :

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path<packagename>
dotnet tool uninstall <packagename>
```

Pour un outil local, le kit de développement logiciel (SDK) recherche le premier fichier manifeste qui contient l’ID de package en examinant le répertoire actif et les répertoires parents.

## <a name="get-help-and-troubleshoot"></a>Obtenir de l’aide et résoudre les problèmes

Pour obtenir la liste des commandes `dotnet tool` disponibles, entrez la commande suivante :

```dotnetcli
dotnet tool --help
```

Pour obtenir des instructions sur l’utilisation de l’outil, entrez l’une des commandes suivantes ou consultez le site Web de l’outil :

```dotnetcli
<command> --help
dotnet <command> --help
```

En cas d’échec de l’installation ou de l’exécution d’un outil, consultez [résoudre les problèmes d’utilisation de l’outil .net Core](troubleshoot-usage-issues.md).
