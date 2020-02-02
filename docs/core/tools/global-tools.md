---
title: Outils globaux .NET Core
description: Vue d’ensemble des outils globaux .NET Core et des commandes CLI .NET Core disponibles pour eux.
author: KathleenDollard
ms.date: 05/29/2018
ms.openlocfilehash: 1531df48b7ca9c816b897d06e725ec375f6cae31
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920489"
---
# <a name="net-core-global-tools-overview"></a>Vue d’ensemble des outils globaux .NET Core

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

Un outil global .NET Core est un package NuGet spécial qui contient une application console. Vous pouvez installer un outil global sur votre machine à un emplacement par défaut inclus dans la variable d’environnement PATH ou à un emplacement personnalisé.

Pour utiliser un outil global .NET Core :

* Recherchez des informations sur l’outil (généralement un site web ou une page GitHub).
* Vérifiez l’auteur et les statistiques dans la page d’accueil du flux (généralement NuGet.org).
* Installez l’outil.
* Appelez l’outil.
* Mettez à jour l’outil.
* Désinstallez l’outil.

> [!IMPORTANT]
> Les outils globaux .NET Core apparaissent dans votre chemin et s’exécutent en mode de confiance totale. N’installez pas les outils globaux .NET Core si vous ne faites pas confiance à l’auteur.

## <a name="find-a-net-core-global-tool"></a>Rechercher un outil global .NET Core

Actuellement, il n’existe pas de fonctionnalité de recherche d’outils globale dans le CLI .NET Core. Voici quelques recommandations sur la façon de trouver des outils :

* Vous trouverez des outils globaux .NET Core sur [NuGet](https://www.nuget.org). Toutefois, NuGet ne vous permet pas encore de rechercher spécifiquement des outils globaux .NET Core.
* Vous pouvez trouver des recommandations d’outils dans les billets de blog ou dans le référentiel GitHub [natemcmaster/dotnet-Tools](https://github.com/natemcmaster/dotnet-tools) .
* Vous pouvez voir le code source des outils globaux créés par l’équipe ASP.NET dans le référentiel GitHub [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools) .
* Pour en savoir plus sur les outils de diagnostic, consultez [Outils globaux de diagnostic dotnet .net Core](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).

## <a name="check-the-author-and-statistics"></a>Vérifier l’auteur et les statistiques

Étant donné que les outils globaux .NET Core s’exécutent en mode de confiance totale et qu’ils sont généralement installés dans votre chemin, ils peuvent être très puissants. Par conséquent, ne téléchargez pas d’outils provenant de personnes en qui vous n’avez pas confiance.

Si l’outil est hébergé sur NuGet, vous pouvez vérifier l’auteur et les statistiques en recherchant l’outil.

## <a name="install-a-global-tool"></a>Installer un outil global

Pour installer un outil global, utilisez la commande CLI .NET Core [dotnet tool install](dotnet-tool-install.md). L’exemple suivant montre comment installer un outil global à l’emplacement par défaut :

```dotnetcli
dotnet tool install -g dotnetsay
```

Si l’outil ne peut pas être installé, des messages d’erreur s’affichent. Assurez-vous que les flux attendus sont vérifiés.

Si vous essayez d’installer une préversion ou une version spécifique de l’outil, vous pouvez spécifier le numéro de version au format suivant :

```dotnetcli
dotnet tool install -g <package-name> --version <version-number>
```

Si l’installation réussit, un message s’affiche indiquant la commande utilisée pour appeler l’outil et la version installée, comme dans l’exemple suivant :

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

Il est possible d’installer des outils globaux dans le répertoire par défaut ou à un emplacement spécifique. Les répertoires par défaut sont :

| Système d’exploitation          | Path                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Portail     | `%USERPROFILE%\.dotnet\tools` |

Ces emplacements sont ajoutés au chemin de l’utilisateur lors de la première exécution du SDK, si bien que les outils globaux qui y sont installés peuvent être appelées directement.

Notez que les outils globaux sont propres à l’utilisateur, et non globaux pour la machine. Le fait d’être propre à l’utilisateur signifie que vous ne pouvez pas installer un outil global disponible pour tous les utilisateurs de la machine. L’outil est uniquement disponible pour chaque profil utilisateur dans lequel l’outil a été installé.

Les outils globaux peuvent également être installés dans un répertoire spécifique. Lors d’une installation dans un répertoire spécifique, l’utilisateur doit vérifier que la commande est disponible, en incluant ce répertoire dans le chemin, en appelant la commande avec le répertoire spécifié, ou en appelant l’outil à partir du répertoire spécifié.
Dans ce cas, CLI .NET Core n’ajoute pas automatiquement cet emplacement à la variable d’environnement PATH.

## <a name="use-the-tool"></a>Utiliser l’outil

Une fois que l’outil est installé, vous pouvez l’appeler à l’aide de sa commande. Notez que la commande peut ne pas être identique au nom du package.

Si la commande est `dotnetsay`, vous l’appelez avec :

```console
dotnetsay
```

Si l’auteur de l’outil voulait que l’outil apparaisse dans le contexte de l’invite `dotnet`, il peut l’avoir écrit de façon à ce que vous l’appeliez en utilisant `dotnet <command>`, par exemple :

```dotnetcli
dotnet doc
```

Vous pouvez déterminer quels outils sont inclus dans un package d’outils globaux installé en répertoriant les packages installés à l’aide de la commande [dotnet tool list](dotnet-tool-list.md).

Vous pouvez également rechercher des instructions d’utilisation sur le site web de l’outil ou en tapant l’une des commandes suivantes :

```console
<command> --help
dotnet <command> --help
```

## <a name="other-cli-commands"></a>Autres commandes CLI

Le SDK .NET Core contient d’autres commandes qui prennent en charge des outils globaux .NET Core. Utilisez l’une des commandes `dotnet tool` avec l’une des options suivantes :

* `--global` ou `-g` spécifient que la commande s’applique aux outils globaux à l’échelle de l’utilisateur.
* `--tool-path` spécifie un emplacement personnalisé pour les outils globaux.

Pour déterminer les commandes disponibles pour les outils globaux :

```dotnetcli
dotnet tool --help
```

La mise à jour d’un outil global implique de le désinstaller puis de le réinstaller avec la dernière version stable. Pour mettre à jour un outil global, utilisez la commande [dotnet tool update](dotnet-tool-update.md) :

```dotnetcli
dotnet tool update -g <packagename>
```

Supprimez un outil global avec [dotnet tool uninstall](dotnet-tool-uninstall.md) :

```dotnetcli
dotnet tool uninstall -g <packagename>
```

Pour afficher tous les outils globaux actuellement installés sur la machine, ainsi que leur version et leurs commandes, utilisez la commande [dotnet tool list](dotnet-tool-list.md) :

```dotnetcli
dotnet tool list -g
```

## <a name="see-also"></a>Voir aussi

* [Résoudre les problèmes d’utilisation de l’outil .NET Core](troubleshoot-usage-issues.md)
