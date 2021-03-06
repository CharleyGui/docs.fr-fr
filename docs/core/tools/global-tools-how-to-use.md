---
title: 'Didacticiel : installer et utiliser un outil Global .NET'
description: Découvrez comment installer et utiliser un outil .NET comme un outil Global.
ms.topic: tutorial
ms.date: 02/12/2020
ms.openlocfilehash: 01b773516da92fb16fb0f67fc6617e0c70d17c9d
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633892"
---
# <a name="tutorial-install-and-use-a-net-global-tool-using-the-net-cli"></a>Didacticiel : installer et utiliser un outil .NET global à l’aide de l’interface de commande .NET

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

Ce didacticiel vous apprend à installer et à utiliser un outil Global. Vous utilisez un outil que vous créez dans le [premier didacticiel de cette série](global-tools-how-to-create.md).

## <a name="prerequisites"></a>Prérequis

* Effectuez le [premier didacticiel de cette série](global-tools-how-to-create.md).

## <a name="use-the-tool-as-a-global-tool"></a>Utiliser l’outil comme outil Global

1. Installez l’outil à partir du package en exécutant la commande [dotnet Tool install](dotnet-tool-install.md) dans le dossier du projet *Microsoft. botsay* :

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   Le `--global` paramètre indique à l’interface CLI .net d’installer les fichiers binaires de l’outil dans un emplacement par défaut qui est automatiquement ajouté à la variable d’environnement PATH.

   Le `--add-source` paramètre indique à l’interface CLI .net d’utiliser temporairement le répertoire *./nupkg* comme flux source supplémentaire pour les packages NuGet. Vous avez donné un nom unique à votre package pour vous assurer qu’il se trouve uniquement dans le répertoire *./nupkg* , pas sur le site NuGet.org.

   La sortie affiche la commande utilisée pour appeler l’outil et la version installée :

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. Appelez l’outil :

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > Si cette commande échoue, vous devrez peut-être ouvrir un nouveau terminal pour actualiser le chemin d’accès.

1. Supprimez l’outil en exécutant la commande de [désinstallation de l’outil dotnet](dotnet-tool-uninstall.md) :

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a>Utiliser l’outil comme outil Global installé dans un emplacement personnalisé

1. Installez l’outil à partir du package.

   Sur Windows :

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   Sur Linux ou macOS :

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   Le `--tool-path` paramètre indique à l’interface CLI .net d’installer les fichiers binaires de l’outil à l’emplacement spécifié. Si le répertoire n’existe pas, il est créé. Ce répertoire n’est pas automatiquement ajouté à la variable d’environnement PATH.

   La sortie affiche la commande utilisée pour appeler l’outil et la version installée :

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
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
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   Sur Linux ou macOS :

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a>Dépanner

Si vous obtenez un message d’erreur lors de la suite du didacticiel, consultez [résoudre les problèmes d’utilisation des outils .net](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez installé et utilisé un outil comme un outil Global. Pour installer et utiliser le même outil qu’un outil local, passez au didacticiel suivant.

> [!div class="nextstepaction"]
> [Installer et utiliser les outils locaux](local-tools-how-to-use.md)
