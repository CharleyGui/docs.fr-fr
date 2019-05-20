---
title: Guide pratique pour installer l’outil CLI ML.NET
description: Vue d’ensemble et installation de l’outil CLI ML.NET
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 869c443d519557c9d3976676047e63a4a072d2d3
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65065802"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a>Guide pratique pour installer l’outil CLI ML.NET

La CLI ML.NET est un outil que vous pouvez exécuter à partir de n’importe quelle invite de commandes (Windows, Mac ou Linux) pour générer des modèles ML.NET et du code source de qualité sur la base des jeux de données d’entraînement que vous fournissez.

> [!NOTE]
> Cette rubrique fait référence à l’interface CLI ML.NET et au moteur AutoML ML.NET, actuellement en préversion. Les ressources sont donc susceptibles d’être changées.

## <a name="pre-requisites"></a>Conditions préalables

- [SDK .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- (Facultatif) [Visual Studio 2017 ou 2019](https://visualstudio.microsoft.com/vs/)

Une fois les projets en C# générés, vous pouvez les exécuter à l’aide de la touche F5 dans Visual Studio ou de la commande `dotnet run` (CLI .NET Core).

Remarque : Si, après l’installation du [SDK .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2), la commande `dotnet tool` ne fonctionne pas, déconnectez-vous de Windows et reconnectez-vous.

## <a name="install"></a>Installez

L’interface CLI ML.NET est installée comme tout autre outil global dotnet. Vous utilisez la commande CLI .NET Core `dotnet tool install`. 

L’exemple suivant montre comment installer la CLI ML.NET à l’emplacement du flux NuGet par défaut :

```console
> dotnet tool install -g mlnet
```

Si l’outil ne peut pas être installé (autrement dit, s’il n’est pas disponible dans le flux NuGet par défaut), des messages d’erreur sont affichés. Assurez-vous que les flux attendus sont vérifiés.

Si l’installation réussit, un message s’affiche indiquant la commande utilisée pour appeler l’outil et la version installée, comme dans l’exemple suivant :

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

Vous pouvez vérifier que l’installation a réussi en tapant la commande suivante :

```console
> mlnet
```

Vous devez voir l’aide des commandes disponibles pour l’outil mlnet, telles que la commande « auto-train ».

## <a name="install-a-specific-release-version"></a>Installer une version spécifique

Si vous essayez d’installer une préversion ou une version spécifique de l’outil, vous pouvez spécifier le numéro de version au format suivant :

```console
> dotnet tool install -g <package-name> --version <version-number>
```

Vous pouvez également vérifier si le package est correctement installé en tapant la commande suivante :

```console
> dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a>Désinstaller le package de la CLI

Tapez la commande suivante pour désinstaller le package de votre ordinateur local :

```console
> dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a>Mettre à jour le package de la CLI

Tapez la commande suivante pour mettre à jour le package sur votre ordinateur local :

```console
> dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a>Configurer des suggestions pour la CLI (autocomplétion avec la touche Tab)

Étant donné que l’interface CLI ML.NET repose sur `System.CommandLine`, elle prend en charge l’autocomplétion à l’aide de la touche Tab.

L’animation suivante illustre le fonctionnement de l’autocomplétion à l’aide de la touche Tab :

![image](./media/cli-tab-completion.gif)

L’autocomplétion à l’aide de la touche Tab (suggestions de paramètre) fonctionne sur *Windows PowerShell* et *macOS/Linux bash*, mais pas sur *Windows CMD*.

Pour l’activer, dans la préversion actuelle, l’utilisateur final doit effectuer quelques étapes une fois par interpréteur de commandes, décrites ci-dessous. Une fois ces étapes effectuées, les complétions fonctionnent pour toutes les applications écrites à l’aide de `System.CommandLine` telles que l’interface CLI ML.NET.

Sur la machine où vous souhaitez activer la complétion, vous devez faire deux choses.

1. Installez l’outil global `dotnet-suggest` en exécutant la commande suivante :

    ```console
    > dotnet tool install dotnet-suggest -g
    ```

2. Ajoutez le script shim approprié au profil de votre interpréteur de commandes. Vous devrez peut-être créer un fichier de profil d’interpréteur de commandes. Le script shim transfère les demandes de complétion depuis votre interpréteur de commandes vers l’outil `dotnet-suggest`, qui délègue à l’application basée sur `System.CommandLine` appropriée.

    * Pour bash, ajoutez le contenu de [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) à `~/.bash_profile`.

    * Pour PowerShell, ajoutez le contenu de [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) à votre profil PowerShell. Vous pouvez trouver le chemin attendu de votre profil PowerShell en exécutant la commande suivante dans votre console :

    ```console
    > echo $profile
    ``` 

(Pour les autres interpréteurs de commandes, [recherchez](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) ou ouvrez un [problème](https://github.com/dotnet/System.CommandLine/issues).)

## <a name="installation-directory"></a>Répertoire d’installation

Il est possible d’installer la CLI ML.NET dans le répertoire par défaut ou à un emplacement spécifique. Les répertoires par défaut sont :

| Système d’exploitation          | Chemin d’accès                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Ces emplacements sont ajoutés au chemin de l’utilisateur lors de la première exécution du SDK, si bien que les outils globaux qui y sont installés peuvent être appelées directement.

Remarque : Les outils globaux sont propres à l’utilisateur, et non globaux pour la machine. Le fait d’être propre à l’utilisateur signifie que vous ne pouvez pas installer un outil global disponible pour tous les utilisateurs de la machine. L’outil est uniquement disponible pour chaque profil utilisateur dans lequel l’outil a été installé.

Les outils globaux peuvent également être installés dans un répertoire spécifique. Lors d’une installation dans un répertoire spécifique, l’utilisateur doit vérifier que la commande est disponible, en incluant ce répertoire dans le chemin, en appelant la commande avec le répertoire spécifié, ou en appelant l’outil à partir du répertoire spécifié.
Dans ce cas, CLI .NET Core n’ajoute pas automatiquement cet emplacement à la variable d’environnement PATH.

## <a name="see-also"></a>Voir aussi

- [Tutoriel sur la prise en main de l’outil CLI ML.NET](../tutorials/mlnet-cli.md)
- [Guide pratique pour entraîner automatiquement des modèles avec l’outil CLI ML.NET](../automate-training-with-cli.md)
- [Informations de référence sur la commande auto-train de la CLI ML.NET](../reference/ml-net-cli-reference.md) 
- [Télémétrie dans la CLI ML.NET](../resources/ml-net-cli-telemetry.md)
