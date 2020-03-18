---
title: 'Tutorial: Installer et utiliser un outil mondial .NET Core'
description: Apprenez à installer et à utiliser un outil .NET comme outil global.
ms.date: 02/12/2020
ms.openlocfilehash: 9f8378e50fd2544eedbbaaeffb89d67800ec6880
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156736"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a>Tutorial: Installer et utiliser un outil mondial .NET Core en utilisant le CLI CLI .NET Core

**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures

Ce tutoriel vous apprend à installer et à utiliser un outil global. Vous utilisez un outil que vous créez dans le [premier tutoriel de cette série](global-tools-how-to-create.md).

## <a name="prerequisites"></a>Conditions préalables requises

* Compléter le [premier tutoriel de cette série](global-tools-how-to-create.md).

## <a name="use-the-tool-as-a-global-tool"></a>Utilisez l’outil comme outil global

1. Installez l’outil à partir du paquet en exécutant la commande [d’installation d’outil dotnet](dotnet-tool-install.md) dans le dossier de projet *microsoft.botsay* :

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   Le `--global` paramètre indique au CLI core .NET d’installer les binaires d’outils dans un emplacement par défaut qui est automatiquement ajouté à la variable de l’environnement PATH.

   Le `--add-source` paramètre indique à l’ECC Core .NET d’utiliser temporairement le répertoire *./nupkg* comme source supplémentaire pour les paquets NuGet. Vous avez donné à votre paquet un nom unique pour s’assurer qu’il ne sera trouvé dans le répertoire *./nupkg,* pas sur le site Nuget.org.

   La sortie montre la commande utilisée pour appeler l’outil et la version installée :

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. Invoquez l’outil :

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > Si cette commande échoue, vous devrez peut-être ouvrir un nouveau terminal pour rafraîchir le PATH.

1. Retirez l’outil en exécutant [l’outil dotnet désinstaller](dotnet-tool-uninstall.md) la commande :

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a>Utilisez l’outil comme outil global installé dans un emplacement personnalisé

1. Installez l’outil à partir de l’emballage.

   Sur Windows :

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   Sur Linux ou macOS :

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   Le `--tool-path` paramètre indique à l’RTC de base .NET d’installer les binaires d’outils à l’emplacement spécifié. Si le répertoire n’existe pas, il est créé. Ce répertoire n’est pas automatiquement ajouté à la variable d’environnement PATH.

   La sortie montre la commande utilisée pour appeler l’outil et la version installée :

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. Invoquez l’outil :

   Sur Windows :

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   Sur Linux ou macOS :

   ```console
   ~/bin/botsay hello from the bot
   ```

1. Retirez l’outil en exécutant [l’outil dotnet désinstaller](dotnet-tool-uninstall.md) la commande :

   Sur Windows :

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   Sur Linux ou macOS :

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a>Dépanner

Si vous obtenez un message d’erreur tout en suivant le tutoriel, voir [Troubleshoot .NET Core problèmes d’utilisation de l’outil](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez installé et utilisé un outil comme un outil global. Pour installer et utiliser le même outil qu’un outil local, passez au tutoriel suivant.

> [!div class="nextstepaction"]
> [Installer et utiliser des outils locaux](local-tools-how-to-use.md)
