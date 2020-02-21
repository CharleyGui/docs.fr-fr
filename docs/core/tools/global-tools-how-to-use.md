---
title: 'Didacticiel : installer et utiliser un outil Global .NET Core'
description: Découvrez comment installer et utiliser un outil .NET comme un outil Global.
ms.date: 02/12/2020
ms.openlocfilehash: 65047af9d8a7f2fd4c1a07f65af3a6ddbf870c5d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543872"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a>Didacticiel : installer et utiliser un outil Global .NET Core à l’aide de l’CLI .NET Core

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

Ce didacticiel vous apprend à installer et à utiliser un outil Global. Vous utilisez un outil que vous créez dans le [premier didacticiel de cette série](global-tools-how-to-create.md).

## <a name="prerequisites"></a>Conditions préalables requises

* Effectuez le [premier didacticiel de cette série](global-tools-how-to-create.md).

## <a name="use-the-tool-as-a-global-tool"></a>Utiliser l’outil comme outil Global

1. Installez l’outil à partir du package en exécutant la commande [dotnet Tool install](dotnet-tool-install.md) dans le *nom botsay-\<>* dossier du projet :

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg botsay-<name>
   ```

   Le paramètre `--global` indique à l’CLI .NET Core d’installer les fichiers binaires de l’outil dans un emplacement par défaut qui est automatiquement ajouté à la variable d’environnement PATH.

   Le paramètre `--add-source` indique à l’CLI .NET Core d’utiliser temporairement le répertoire *./nupkg* comme flux source supplémentaire pour les packages NuGet. Vous avez donné un nom unique à votre package pour vous assurer qu’il se trouve uniquement dans le répertoire *./nupkg* , pas sur le site NuGet.org. 

   La sortie affiche la commande utilisée pour appeler l’outil et la version installée :

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
   ```

1. Appelez l’outil :

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > Si cette commande échoue, vous devrez peut-être ouvrir un nouveau terminal pour actualiser le chemin d’accès.

1. Supprimez l’outil en exécutant la commande de [désinstallation de l’outil dotnet](dotnet-tool-uninstall.md) :

   ```dotnetcli
   dotnet tool uninstall -g botsay-<name>
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a>Utiliser l’outil comme outil Global installé dans un emplacement personnalisé

1. Installez l’outil à partir du package.

   Sur Windows :

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg botsay-<name>
   ```

   Sur Linux ou macOS :

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg botsay-<name>
   ```

   Le paramètre `--tool-path` indique à l’CLI .NET Core d’installer les fichiers binaires de l’outil à l’emplacement spécifié. Si le répertoire n’existe pas, il est créé. Ce répertoire n’est pas automatiquement ajouté à la variable d’environnement PATH.

   La sortie affiche la commande utilisée pour appeler l’outil et la version installée :

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
   ```

1. Appelez l’outil :

   Sur Windows :

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   Sur Linux ou macOS :

   ```console
   ~/bin/botsay hello from the bot
   ```

1. Supprimez l’outil en exécutant la commande de [désinstallation de l’outil dotnet](dotnet-tool-uninstall.md) :

   Sur Windows :

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools botsay --add-source ./nupkg botsay-<name>
   ```

   Sur Linux ou macOS :

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin botsay-<name>
   ```

## <a name="troubleshoot"></a>Dépanner

Si vous obtenez un message d’erreur lors de la suite du didacticiel, consultez [résoudre les problèmes d’utilisation de l’outil .net Core](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez installé et utilisé un outil comme un outil Global. Pour installer et utiliser le même outil qu’un outil local, passez au didacticiel suivant.

> [!div class="nextstepaction"]
> [Installer et utiliser les outils locaux](local-tools-how-to-use.md)
