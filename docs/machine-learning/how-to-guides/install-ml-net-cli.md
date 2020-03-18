---
title: Guide pratique pour installer l’outil CLI ML.NET
description: Apprenez à installer, mettre à niveau, déclasser et désinstaller l’outil ML.NET Interface de ligne de commandement (CLI).
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 9f678c7117d32bf817139951db7eef2c3d0f5eb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848637"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a>Guide pratique pour installer l’outil CLI ML.NET

Découvrez comment installer le ML.NET CLI (interface de commande) sur Windows, Mac ou Linux.

L’ML.NET CLI génère des modèles ML.NET de bonne qualité et du code source à l’aide d’un logiciel automatisé d’apprentissage automatique (AutoML) et d’un jeu de données de formation.

> [!NOTE]
> Cette rubrique fait référence à l’interface CLI ML.NET et au moteur AutoML ML.NET, actuellement en préversion. Les ressources sont donc susceptibles d’être changées.

## <a name="pre-requisites"></a>Conditions préalables

- [Kit SDK .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- (Facultatif) [Visual Studio 2017 ou 2019](https://visualstudio.microsoft.com/vs/)

Vous pouvez exécuter les projets de code `F5` Cmd `dotnet run` générés avec Visual Studio en appuyant sur la clé ou avec (.NET Core CLI).

Remarque : Si après l’installation [de .NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) la `dotnet tool` commande ne fonctionne pas, déconnectez-vous de Windows et connectez-vous à nouveau.

## <a name="install"></a>Installer

L’interface CLI ML.NET est installée comme tout autre outil global dotnet. Vous utilisez la commande CLI .NET Core `dotnet tool install`.

L’exemple suivant montre comment installer la CLI ML.NET à l’emplacement du flux NuGet par défaut :

```dotnetcli
dotnet tool install -g mlnet
```

Si l’outil ne peut pas être installé (autrement dit, s’il n’est pas disponible dans le flux NuGet par défaut), des messages d’erreur sont affichés. Assurez-vous que les flux attendus sont vérifiés.

Si l’installation réussit, un message s’affiche indiquant la commande utilisée pour appeler l’outil et la version installée, comme dans l’exemple suivant :

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

Vous pouvez vérifier que l’installation a réussi en tapant la commande suivante :

```console
mlnet
```

Vous devez voir l’aide des commandes disponibles pour l’outil mlnet, telles que la commande « auto-train ».

## <a name="install-a-specific-release-version"></a>Installer une version spécifique

Si vous essayez d’installer une version préliminaire ou une version spécifique de l’outil, vous pouvez spécifier [l’infrastructure](../../standard/frameworks.md) au format suivant :

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

Vous pouvez également vérifier si le package est correctement installé en tapant la commande suivante :

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a>Désinstaller le package de la CLI

Tapez la commande suivante pour désinstaller le package de votre ordinateur local :

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a>Mettre à jour le package de la CLI

Tapez la commande suivante pour mettre à jour le package sur votre ordinateur local :

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a>Configurer des suggestions pour la CLI (autocomplétion avec la touche Tab)

Étant donné que l’interface CLI ML.NET repose sur `System.CommandLine`, elle prend en charge l’autocomplétion à l’aide de la touche Tab.

L’animation suivante illustre le fonctionnement de l’autocomplétion à l’aide de la touche Tab :

![image](./media/cli-tab-completion.gif)

L’autocomplétion à l’aide de la touche Tab (suggestions de paramètre) fonctionne sur *Windows PowerShell* et *macOS/Linux bash*, mais pas sur *Windows CMD*.

Pour l’activer, dans la préversion actuelle, l’utilisateur final doit effectuer quelques étapes une fois par interpréteur de commandes, décrites ci-dessous. Une fois ces étapes effectuées, les complétions fonctionnent pour toutes les applications écrites à l’aide de `System.CommandLine` telles que l’interface CLI ML.NET.

Sur la machine où vous souhaitez activer la complétion, vous devez faire deux choses.

1. Installez l’outil global `dotnet-suggest` en exécutant la commande suivante :

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. Ajoutez le script shim approprié au profil de votre interpréteur de commandes. Vous devrez peut-être créer un fichier de profil d’interpréteur de commandes. Le script shim transfère les demandes de complétion depuis votre interpréteur de commandes vers l’outil `dotnet-suggest`, qui délègue à l’application basée sur `System.CommandLine` appropriée.

    - Pour bash, ajoutez le contenu de [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) à `~/.bash_profile`.

    - Pour PowerShell, ajoutez le contenu de [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) à votre profil PowerShell. Vous pouvez trouver le chemin attendu de votre profil PowerShell en exécutant la commande suivante dans votre console :

    ```console
    echo $profile
    ```

(Pour les autres interpréteurs de commandes, [recherchez](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) ou ouvrez un [problème](https://github.com/dotnet/System.CommandLine/issues).)

## <a name="installation-directory"></a>Répertoire d’installation

Il est possible d’installer la CLI ML.NET dans le répertoire par défaut ou à un emplacement spécifique. Les répertoires par défaut sont :

| Système d''exploitation          | Path                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
|  Windows     | `%USERPROFILE%\.dotnet\tools` |

Ces emplacements sont ajoutés au chemin de l’utilisateur lors de la première exécution du SDK, si bien que les outils globaux qui y sont installés peuvent être appelées directement.

Remarque : Les outils globaux sont propres à l’utilisateur, et non globaux pour la machine. Le fait d’être propre à l’utilisateur signifie que vous ne pouvez pas installer un outil global disponible pour tous les utilisateurs de la machine. L’outil est uniquement disponible pour chaque profil utilisateur dans lequel l’outil a été installé.

Les outils globaux peuvent également être installés dans un répertoire spécifique. Lors d’une installation dans un répertoire spécifique, l’utilisateur doit vérifier que la commande est disponible, en incluant ce répertoire dans le chemin, en appelant la commande avec le répertoire spécifié, ou en appelant l’outil à partir du répertoire spécifié.
Dans ce cas, CLI .NET Core n’ajoute pas automatiquement cet emplacement à la variable d’environnement PATH.

## <a name="see-also"></a>Voir aussi

- [vue d’ensemble de ML.NET CLI](../automate-training-with-cli.md)
- [Tutorial: Analyser le sentiment avec le ML.NET CLI](../tutorials/sentiment-analysis-cli.md)
- [Informations de référence sur la commande auto-train de la CLI ML.NET](../reference/ml-net-cli-reference.md)
- [Télémétrie dans la CLI ML.NET](../resources/ml-net-cli-telemetry.md)
