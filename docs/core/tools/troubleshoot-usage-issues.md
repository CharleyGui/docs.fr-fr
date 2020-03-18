---
title: Problème .NET Problèmes d’utilisation d’outils de base
description: Découvrez les problèmes communs lors de l’exécution des outils .NET Core et des solutions possibles.
author: kdollard
ms.date: 02/14/2020
ms.openlocfilehash: ed6243f802c4d3ce56a742916a1a28676e3cd876
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146448"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a>Problème .NET Problèmes d’utilisation d’outils de base

Vous pourriez rencontrer des problèmes lorsque vous essayez d’installer ou d’exécuter un outil .NET Core, qui peut être un outil global ou un outil local. Cet article décrit les causes profondes communes et certaines solutions possibles.

## <a name="installed-net-core-tool-fails-to-run"></a>L’outil de base .NET installé ne fonctionne pas

Lorsqu’un outil .NET Core ne fonctionne pas, il est fort probable que vous ayez rencontré l’un des problèmes suivants :

* Le fichier exécutable pour l’outil n’a pas été trouvé.
* La version correcte du temps d’exécution .NET Core n’a pas été trouvée.

### <a name="executable-file-not-found"></a>Fichier exécutable non trouvé

Si le fichier exécutable n’est pas trouvé, vous verrez un message similaire à ce qui suit :

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

Le nom de l’exécutable détermine comment vous invoquez l’outil. Le tableau suivant décrit le format :

| Format de nom exécutable  | Format d’invocation   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* Outils globaux

  Des outils globaux peuvent être installés dans l’annuaire par défaut ou dans un endroit spécifique. Les répertoires par défaut sont :

  | Système d''exploitation          | Path                          |
  |-------------|-------------------------------|
  | Linux/macOS | `$HOME/.dotnet/tools`         |
  |  Windows     | `%USERPROFILE%\.dotnet\tools` |

  Si vous essayez d’exécuter un outil `PATH` global, vérifiez que la variable d’environnement sur votre machine contient le chemin où vous avez installé l’outil global et que l’exécutable est dans ce sens.

  Le CLI core .NET essaie d’ajouter l’emplacement par défaut à la variable d’environnement PATH sur sa première utilisation. Cependant, il existe certains scénarios où l’emplacement pourrait ne pas être ajouté à PATH automatiquement:

  * Si vous utilisez Linux et que vous avez installé le .NET Core SDK à l’aide de fichiers *.tar.gz* et non pas apt-get ou rpm.
  * Si vous utilisez macOS 10.15 "Catalina" ou des versions ultérieures.
  * Si vous utilisez macOS 10.14 "Mojave" ou des versions antérieures, et vous avez installé le .NET Core SDK en utilisant des fichiers *.tar.gz* et non *.pkg*.
  * Si vous avez installé le .NET Core 3.0 SDK et que vous avez défini la variable de l’environnement `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` à `false`.
  * Si vous avez installé .NET Core 2.2 SDK ou des `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` versions `true`antérieures, et que vous avez défini la variable de l’environnement à .

  Dans ces scénarios ou si `--tool-path` vous `PATH` avez spécifié l’option, la variable d’environnement sur votre machine ne contient pas automatiquement le chemin où vous avez installé l’outil global. Dans ce cas, appendicez l’emplacement de l’outil (par exemple) `$HOME/.dotnet/tools`à la variable d’environnement `PATH` en utilisant n’importe quelle méthode que votre coquille fournit pour mettre à jour les variables de l’environnement. Pour plus d’informations, voir [.NET Core tools](global-tools.md).

* Outils locaux

  Si vous essayez d’exécuter un outil local, vérifiez qu’il existe un fichier manifeste appelé *dotnet-tools.json* dans l’annuaire actuel ou l’un de ses répertoires parent. Ce fichier peut également vivre sous un dossier nommé *.config* n’importe où dans la hiérarchie du dossier de projet, au lieu du dossier de racine. Si *dotnet-tools.json* existe, ouvrez-le et vérifiez l’outil que vous essayez d’exécuter. Si le fichier ne contient `"isRoot": true`pas d’entrée pour , puis vérifiez également plus loin dans la hiérarchie de fichiers pour les fichiers manifestes d’outils supplémentaires.

  Si vous essayez d’exécuter un outil .NET Core qui a été installé avec un chemin spécifié, vous devez inclure ce chemin lors de l’utilisation de l’outil. Un exemple d’utilisation d’un outil installé est :

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a>Temps d’exécution non trouvé

.NET Les outils de base sont [des applications dépendantes du cadre,](../deploying/index.md#publish-runtime-dependent)ce qui signifie qu’ils s’appuient sur un temps d’exécution .NET Core installé sur votre machine. Si le temps d’exécution prévu n’est pas trouvé, ils suivent les règles normales .NET Core runtime roll-forward telles que:

* Une application restaure par progression le correctif le plus élevé de la version principale et secondaire spécifiée.
* S’il n’y a pas de temps d’exécution correspondant avec un numéro de version majeur et mineur correspondant, la prochaine version mineure supérieure est utilisée.
* Une restauration par progression ne se produit pas entre des préversions du runtime ou entre des préversions et des versions finales. Ainsi, les outils .NET Core créés à l’aide de versions de prévisualisation doivent être reconstruits et republiés par l’auteur et réinstallés.

Roll-forward ne se produira pas par défaut dans deux scénarios courants :

* Seules des versions inférieures de l’exécution sont disponibles. Roll-forward ne sélectionne que les versions ultérieures de l’exécution.
* Seules des versions majeures supérieures du temps d’exécution sont disponibles. Roll-forward ne franchit pas les frontières des versions majeures.

Si une application ne peut pas trouver un temps d’exécution approprié, elle ne s’exécute pas et signale une erreur.

Vous pouvez savoir quels arrêts .NET Core sont installés sur votre machine à l’aide d’une des commandes suivantes :

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

Si vous pensez que l’outil doit prendre en charge la version en temps d’exécution que vous avez actuellement installé, vous pouvez contacter l’auteur de l’outil et voir s’ils peuvent mettre à jour le numéro de version ou multi-cible. Une fois qu’ils ont recompilé et réédité leur paquet d’outils à NuGet avec un numéro de version mis à jour, vous pouvez mettre à jour votre copie. Bien que cela ne se produise pas, la solution la plus rapide pour vous est d’installer une version du temps d’exécution qui fonctionnerait avec l’outil que vous essayez d’exécuter. Pour télécharger une version spécifique .NET Core runtime, visitez la [page de téléchargement .NET Core](https://dotnet.microsoft.com/download/dotnet-core).

Si vous installez le SDK core .NET à un emplacement `DOTNET_ROOT` non par défaut, `dotnet` vous devez définir la variable d’environnement à l’annuaire qui contient l’exécutable.

## <a name="net-core-tool-installation-fails"></a>l’installation d’outil de base de net-NET échoue

Il ya un certain nombre de raisons pour lesquelles l’installation d’un outil mondial ou local .NET Core peut échouer. Lorsque l’installation de l’outil échoue, vous verrez un message similaire à celui suivant :

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

Pour aider à diagnostiquer ces défaillances, les messages NuGet sont affichés directement à l’utilisateur, ainsi que le message précédent. Le message NuGet peut vous aider à identifier le problème.

### <a name="package-naming-enforcement"></a>Exécution de nommage de paquet

Microsoft a changé ses conseils sur l’ID package pour les outils, résultant en un certain nombre d’outils ne sont pas trouvés avec le nom prévu. La nouvelle orientation est que tous les outils Microsoft soient préfixés avec "Microsoft". Ce préfixe est réservé et ne peut être utilisé que pour les paquets signés avec un certificat autorisé par Microsoft.

Pendant la transition, certains outils Microsoft auront l’ancienne forme de l’ID paquet, tandis que d’autres auront le nouveau formulaire:

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

Au fur et à mesure que les identifiants de paquet sont mis à jour, vous devrez modifier le nouvel ID du paquet pour obtenir les dernières mises à jour. Les paquets avec le nom simplifié de l’outil seront dépréciés.

### <a name="preview-releases"></a>Extrait des versions

* Vous essayez d’installer une version de prévisualisation et n’avez pas utilisé l’option `--version` pour spécifier la version.

.NET Les outils de base qui sont en prévisualisation doivent être spécifiés avec une partie du nom pour indiquer qu’ils sont en prévisualisation. Vous n’avez pas besoin d’inclure l’aperçu complet. En supposant que les numéros de version sont dans le format prévu, vous pouvez utiliser quelque chose comme l’exemple suivant:

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-core-tool"></a>Le paquet n’est pas un outil .NET Core

* Un paquet NuGet de ce nom a été trouvé, mais ce n’était pas un outil .NET Core.

Si vous essayez d’installer un package NuGet qui est un paquet NuGet régulier et non un outil .NET Core, vous verrez une erreur similaire à ce qui suit:

> NU1212: Combinaison de projets invalides pour `<ToolName>`. Le style du projet DotnetToolReference ne peut contenir que des références du type DotnetTool.

### <a name="nuget-feed-cant-be-accessed"></a>L’alimentation NuGet ne peut pas être consultée

* Le flux NuGet requis ne peut pas être consulté, peut-être en raison d’un problème de connexion Internet.

L’installation d’outils nécessite l’accès à l’alimentation NuGet qui contient le paquet d’outils. Il échoue si le flux n’est pas disponible. Vous pouvez modifier `nuget.config`les flux `nuget.config` avec, demander un fichier `--add-source` spécifique, ou spécifier des flux supplémentaires avec le commutateur. Par défaut, NuGet lance une erreur pour tout flux qui ne peut pas se connecter. Le `--ignore-failed-sources` drapeau peut sauter ces sources non accessibles.

### <a name="package-id-incorrect"></a>Identifiant de paquet incorrect

* Vous avez mal interprété le nom de l’outil.

Une raison commune de l’échec est que le nom de l’outil n’est pas correct. Cela peut se produire en raison de mauvaisty, ou parce que l’outil a bougé ou a été déprécié. Pour les outils sur NuGet.org, une façon de s’assurer que vous avez le nom correct est de rechercher l’outil à NuGet.org et copier la commande d’installation.

## <a name="see-also"></a>Voir aussi

* [.NET Outils de base](global-tools.md)
