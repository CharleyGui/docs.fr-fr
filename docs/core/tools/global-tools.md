---
title: .NET Outils de base
description: Comment installer, utiliser, mettre à jour et supprimer les outils .NET Core. Couvre les outils globaux, les outils de chemin à outils et les outils locaux.
author: KathleenDollard
ms.date: 02/12/2020
ms.openlocfilehash: 2f0101c6385c41eda49bcb2458428c1f14552617
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847783"
---
# <a name="how-to-manage-net-core-tools"></a>Comment gérer les outils de base .NET

**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures

Un outil .NET Core est un forfait NuGet spécial qui contient une application de console. Un outil peut être installé sur votre machine de la manière suivante :

* En tant qu’outil global.

  Les binaires d’outils sont installés dans un répertoire par défaut qui est ajouté à la variable d’environnement PATH. Vous pouvez invoquer l’outil à partir de n’importe quel répertoire sur la machine sans spécifier son emplacement. Une version d’un outil est utilisée pour tous les répertoires de la machine.

* En tant qu’outil global dans un emplacement personnalisé (également connu sous le nom d’outil-chemin).

  Les binaires d’outils sont installés dans un endroit que vous spécifiez. Vous pouvez invoquer l’outil à partir du répertoire d’installation ou en fournissant le répertoire avec le nom de commande ou en ajoutant l’annuaire à la variable de l’environnement PATH. Une version d’un outil est utilisée pour tous les répertoires de la machine.

* En tant qu’outil local (s’applique à .NET Core SDK 3.0 et plus tard).

  Les binaires d’outils sont installés dans un répertoire par défaut. Vous invoquez l’outil du répertoire d’installation ou de l’un de ses sous-directeurs. Différents répertoires peuvent utiliser différentes versions d’un même outil.
  
  Le CLI .NET utilise des fichiers manifestes pour garder une trace des outils qui sont installés comme locaux à un répertoire. Lorsque le fichier manifeste est enregistré dans l’annuaire root d’un référentiel de code source, un contributeur peut cloner le référentiel et invoquer une seule commande CLI de base .NET qui installe tous les outils énumérés dans les fichiers manifestes.

> [!IMPORTANT]
> .NET Outils de base fonctionnent en pleine confiance. N’installez pas un outil .NET Core sauf si vous faites confiance à l’auteur.

## <a name="find-a-tool"></a>Trouver un outil

Actuellement, .NET Core n’a pas de fonctionnalité de recherche d’outils. Voici quelques façons de trouver des outils :

* Voir la liste des outils dans le référentiel GitHub [natemcmaster/dotnet-tools.](https://github.com/natemcmaster/dotnet-tools)
* Utilisez [ToolGet](https://www.toolget.net/) pour rechercher des outils .NET.
* Voir le code source pour les outils créés par l’équipe ASP.NET Core dans le [répertoire Tools du référentiel GitHub dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).
* En savoir plus sur les outils de diagnostic à [.NET Core dotnet outils de diagnostic](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).
* Recherchez le site [Web de NuGet.](https://www.nuget.org) Cependant, le site NuGet n’a pas encore de fonctionnalité qui vous permet de rechercher uniquement des paquets d’outils.

## <a name="check-the-author-and-statistics"></a>Vérifier l’auteur et les statistiques

Étant donné que les outils .NET Core fonctionnent en pleine confiance et que des outils globaux sont ajoutés à la variable de l’environnement PATH, ils peuvent être très puissants. Par conséquent, ne téléchargez pas d’outils provenant de personnes en qui vous n’avez pas confiance.

Si l’outil est hébergé sur NuGet, vous pouvez vérifier l’auteur et les statistiques en recherchant l’outil.

## <a name="install-a-global-tool"></a>Installer un outil global

Pour installer un outil comme outil `-g` `--global` global, utilisez l’installation ou l’option de [l’installation d’outils dotnet,](dotnet-tool-install.md)comme le montre l’exemple suivant :

```dotnetcli
dotnet tool install -g dotnetsay
```

La sortie montre la commande utilisée pour invoquer l’outil et la version installée, semblable à l’exemple suivant :

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

L’emplacement par défaut des binaires d’un outil dépend du système d’exploitation :

| Système d''exploitation          | Path                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
|  Windows     | `%USERPROFILE%\.dotnet\tools` |

Cet emplacement est ajouté au chemin de l’utilisateur lorsque le SDK est géré pour la première fois, de sorte que les outils globaux peuvent être invoqués à partir de n’importe quel répertoire sans spécifier l’emplacement de l’outil.

L’accès à l’outil est spécifique à l’utilisateur, et non à la machine mondiale. Un outil global n’est disponible que pour l’utilisateur qui a installé l’outil.

### <a name="install-a-global-tool-in-a-custom-location"></a>Installer un outil global dans un emplacement personnalisé

Pour installer un outil comme outil global dans `--tool-path` un emplacement personnalisé, utilisez l’option d’installation d’outils [dotnet,](dotnet-tool-install.md)comme le montrent les exemples suivants.

Sur Windows :

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

Sur Linux ou macOS :

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

Le SDK core .NET n’ajoute pas automatiquement cet emplacement à la variable d’environnement PATH. Pour [invoquer un outil de chemin d’outil,](#invoke-a-tool-path-tool)vous devez vous assurer que la commande est disponible en utilisant l’une des méthodes suivantes :

* Ajouter le répertoire d’installation à la variable de l’environnement PATH.
* Spécifier le chemin complet vers l’outil lorsque vous l’invoquez.
* Invoquez l’outil à partir de l’annuaire d’installation.

## <a name="install-a-local-tool"></a>Installer un outil local

**S’applique à .NET Core 3.0 SDK et plus tard.**

Pour installer un outil d’accès local uniquement (pour l’annuaire actuel et les sous-directeurs), il doit être ajouté à un fichier manifeste d’outil. Pour créer un fichier manifeste `dotnet new tool-manifest` d’outil, exécutez la commande :

```dotnetcli
dotnet new tool-manifest
```

Cette commande crée un fichier manifeste nommé *dotnet-tools.json* sous l’annuaire *.config.* Pour ajouter un outil local au fichier manifeste, utilisez l’outil `--tool-path` [dotnet installer](dotnet-tool-install.md) la commande et **omettre** les options et les `--global` options, comme le montre l’exemple suivant :

```dotnetcli
dotnet tool install dotnetsay
```

La sortie de commande indique dans quel fichier manifeste l’outil nouvellement installé est, semblable à l’exemple suivant :

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

L’exemple suivant montre un fichier manifeste avec deux outils locaux installés :

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

Vous ajoutez généralement un outil local à l’annuaire racine du référentiel. Après avoir vérifié le fichier manifeste au référentiel, les développeurs qui vérifient le code du référentiel obtiennent le dernier fichier manifeste. Pour installer tous les outils énumérés dans `dotnet tool restore` le fichier manifeste, ils exécutent la commande :

```dotnetcli
dotnet tool restore
```

La sortie indique quels outils ont été restaurés :

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a>Installer une version outil spécifique

Pour installer une version pré-version ou une version spécifique d’un outil, spécifiez le numéro de version en utilisant l’option, `--version` comme indiqué dans l’exemple suivant :

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a>Utiliser un outil

La commande que vous utilisez pour invoquer un outil peut être différente du nom du paquet que vous installez. Pour afficher tous les outils actuellement installés sur la machine pour l’utilisateur actuel, utilisez la commande [de liste d’outils dotnet](dotnet-tool-list.md) :

```dotnetcli
dotnet tool list
```

La sortie affiche la version et la commande de chaque outil, semblables à l’exemple suivant :

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

Comme le montre cet exemple, la liste montre les outils locaux. Pour voir les outils `--global` globaux, utiliser l’option et `--tool-path` voir les outils de voie d’outils, utilisez l’option.

### <a name="invoke-a-global-tool"></a>Invoquer un outil global

Pour les outils globaux, utilisez la commande d’outils par lui-même. Par exemple, si `dotnetsay` la `dotnet-doc`commande est ou , c’est ce que vous utilisez pour invoquer la commande:

```console
dotnetsay
dotnet-doc
```

Si la commande commence `dotnet-`par le préfixe, une autre `dotnet` façon d’invoquer l’outil est d’utiliser la commande et d’omettre le préfixe de commande de l’outil. Par exemple, si `dotnet-doc`la commande est, la commande suivante invoque l’outil :

```dotnetcli
dotnet doc
```

Toutefois, dans le scénario suivant, `dotnet` vous ne pouvez pas utiliser la commande pour invoquer un outil global :

* Un outil global et un outil local ont `dotnet-`la même commande préfixée par .
* Vous souhaitez invoquer l’outil global à partir d’un répertoire qui est en portée pour l’outil local.

Dans ce `dotnet doc` scénario, et `dotnet dotnet-doc` invoquer l’outil local. Pour invoquer l’outil global, utilisez la commande par lui-même :

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a>Invoquer un outil de chemin d’outil

Pour invoquer un outil global `tool-path` qui est installé en utilisant l’option, assurez-vous que la commande est disponible, comme expliqué [plus tôt dans cet article](#install-a-global-tool-in-a-custom-location).

### <a name="invoke-a-local-tool"></a>Invoquer un outil local

Pour invoquer un outil local, vous devez utiliser la `dotnet` commande à partir de l’annuaire d’installation. Vous pouvez utiliser la`dotnet tool run <COMMAND_NAME>`forme longue (`dotnet <COMMAND_NAME>`) ou la forme courte ( ), comme indiqué dans les exemples suivants:

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

Si la commande est `dotnet-`préfixée par , vous pouvez inclure ou omettre le préfixe lorsque vous invoquez l’outil. Par exemple, si `dotnet-doc`la commande est, l’un des exemples suivants invoque l’outil local :

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a>Mettre à jour un outil

La mise à jour d’un outil implique de le désinstaller et de le réinstaller avec la dernière version stable. Pour mettre à jour un outil, utilisez la commande [de mise à jour de l’outil dotnet](dotnet-tool-update.md) avec la même option que vous avez utilisée pour installer l’outil :

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

Pour un outil local, le SDK trouve le premier fichier manifeste qui contient l’ID du paquet en regardant dans l’annuaire actuel et les répertoires parent. S’il n’y a pas d’id de paquet dans un fichier manifeste, le SDK ajoute une nouvelle entrée au fichier manifeste le plus proche.

## <a name="uninstall-a-tool"></a>Désinstaller un outil

Retirez un outil en utilisant [l’outil dotnet désinstaller](dotnet-tool-uninstall.md) la commande avec la même option que vous avez utilisé pour installer l’outil:

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path<packagename>
dotnet tool uninstall <packagename>
```

Pour un outil local, le SDK trouve le premier fichier manifeste qui contient l’ID du paquet en regardant dans l’annuaire actuel et les répertoires parent.

## <a name="get-help-and-troubleshoot"></a>Obtenez de l’aide et dépannez

Pour obtenir une `dotnet tool` liste de commandes disponibles, entrez la commande suivante :

```dotnetcli
dotnet tool --help
```

Pour obtenir des instructions d’utilisation de l’outil, saisissez l’une des commandes suivantes ou consultez le site Web de l’outil :

```dotnetcli
<command> --help
dotnet <command> --help
```

Si un outil ne parvient pas à installer ou à exécuter, voir [Troubleshoot .NET Core problèmes d’utilisation de l’outil](troubleshoot-usage-issues.md).

## <a name="see-also"></a>Voir aussi

- [Tutorial: Créer un outil .NET Core en utilisant le CLI de base .NET](global-tools-how-to-create.md)
- [Tutorial: Installer et utiliser un outil mondial .NET Core en utilisant le CLI CLI .NET Core](global-tools-how-to-use.md)
- [Tutorial: Installer et utiliser un outil local .NET Core en utilisant le CLI .NET Core](local-tools-how-to-use.md)
