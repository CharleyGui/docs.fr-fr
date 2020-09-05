---
title: Publier une application console .NET Core à l’aide de Visual Studio Code
description: La publication crée l’ensemble des fichiers nécessaires à l’exécution d’une application .NET Core.
ms.date: 07/04/2020
ms.openlocfilehash: 79c69546b79de3d702fb4bb6550e615d8d59fa74
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495523"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-code"></a>Didacticiel : publier une application console .NET Core à l’aide de Visual Studio Code

Ce didacticiel montre comment publier une application console afin que d’autres utilisateurs puissent l’exécuter. La publication crée l’ensemble des fichiers nécessaires à l’exécution d’une application. Pour déployer les fichiers, copiez-les sur l’ordinateur cible.

Le CLI .NET Core est utilisé pour publier l’application. vous pouvez donc suivre ce didacticiel avec un éditeur de code autre que Visual Studio Code si vous préférez.

## <a name="prerequisites"></a>Prérequis

- Ce didacticiel fonctionne avec l’application console que vous créez dans [créer une application console .net core à l’aide de Visual Studio code](with-visual-studio-code.md).

## <a name="publish-the-app"></a>Publier l’application

1. Démarrer Visual Studio Code

1. Ouvrez le dossier du projet *HelloWorld* que vous avez créé dans [créer une application console .net core à l’aide de Visual Studio code](with-visual-studio-code.md).

1. Choisissez **Afficher**  >  **Terminal** dans le menu principal.

   Le terminal s’ouvre dans le dossier *HelloWorld* .

1. Exécutez la commande suivante :

   ```dotnetcli
   dotnet publish --configuration Release
   ```

   La configuration de build par défaut est *Debug*. cette commande spécifie donc la configuration *Release* Build. La sortie de la configuration de build de mise en production possède des informations de débogage symboliques minimales et est entièrement optimisée.

   La sortie de commande ressemble à l’exemple suivant :

   ```output
   Microsoft (R) Build Engine version 16.7.0+b89cb5fde for .NET
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\HelloWorld.dll
     HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

## <a name="inspect-the-files"></a>Inspecter les fichiers

Par défaut, le processus de publication crée un déploiement dépendant du Framework, qui est un type de déploiement dans lequel l’application publiée s’exécute sur un ordinateur sur lequel le Runtime .NET Core est installé. Pour exécuter l’application publiée, vous pouvez utiliser le fichier exécutable ou exécuter la `dotnet HelloWorld.dll` commande à partir d’une invite de commandes.

Dans les étapes suivantes, vous allez examiner les fichiers créés par le processus de publication.

1. Sélectionnez l' **Explorateur** dans la barre de navigation de gauche.

1. Développez *bin/Release/netcoreapp 3.1/Publish*.

   :::image type="content" source="media/publishing-with-visual-studio-code/published-files-output.png" alt-text="Explorateur présentant les fichiers publiés":::

   Comme l’indique l’image, la sortie publiée comprend les fichiers suivants :

   * *HelloWorld.deps.json*

      Il s’agit du fichier de dépendances d’exécution de l’application. Il définit les composants .NET Core et les bibliothèques (y compris la bibliothèque de liens dynamiques qui contient votre application) nécessaires pour exécuter l’application. Pour plus d’informations, consultez [fichiers de configuration](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)de l’exécution.

   * *HelloWorld.dll*

      Il s’agit de la version de [déploiement dépendante du Framework](../deploying/deploy-with-cli.md#framework-dependent-deployment) de l’application. Pour exécuter cette bibliothèque de liens dynamiques, entrez `dotnet HelloWorld.dll` à l’invite de commandes. Cette méthode d’exécution de l’application fonctionne sur toutes les plateformes sur lesquelles le Runtime .NET Core est installé.

   * *HelloWorld.exe* (*HelloWorld* sur Linux, non créé sur MacOS.)

      Il s’agit de la version [exécutable dépendante du Framework](../deploying/deploy-with-cli.md#framework-dependent-executable) de l’application. Le fichier est spécifique au système d’exploitation.

   * *HelloWorld.pdb* (facultatif pour le déploiement)

      Il s’agit du fichier de symboles de débogage. Vous n’êtes pas obligé de déployer ce fichier avec votre application, même si vous devez l’enregistrer au cas où vous auriez à déboguer la version publiée de votre application.

   * *HelloWorld.runtimeconfig.json*

      Il s’agit du fichier de configuration au moment de l’exécution de l’application. Il identifie la version de .NET Core sur laquelle votre application doit être exécutée. Vous pouvez également y ajouter des options de configuration. Pour plus d’informations, consultez [paramètres de configuration du Runtime .net Core](../run-time-config/index.md#runtimeconfigjson).

## <a name="run-the-published-app"></a>Exécuter l’application publiée

1. Dans l' **Explorateur**, cliquez avec le bouton droit sur le dossier de *publication* (<kbd>CTRL</kbd>+ clic sur MacOS), puis sélectionnez **ouvrir dans Terminal**.

   :::image type="content" source="media/publishing-with-visual-studio-code/open-in-terminal.png" alt-text="Menu contextuel avec ouverture dans le terminal":::

1. Sur Windows ou Linux, exécutez l’application à l’aide de l’exécutable.

   1. Sur Windows, entrez `.\HelloWorld.exe` et appuyez sur <kbd>entrée</kbd>.

   1. Sur Linux, entrez `./HelloWorld` et appuyez sur <kbd>entrée</kbd>.

   1. Entrez un nom en réponse à l’invite, puis appuyez sur n’importe quelle touche pour quitter.

1. Sur n’importe quelle plateforme, exécutez l’application à l’aide de la  [`dotnet`](../tools/dotnet.md) commande :

   1. Entrez `dotnet HelloWorld.dll`, puis appuyez sur <kbd>Entrée</kbd>.

   1. Entrez un nom en réponse à l’invite, puis appuyez sur n’importe quelle touche pour quitter.

## <a name="additional-resources"></a>Ressources supplémentaires

- [Déploiement d’applications .NET Core](../deploying/index.md)

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez publié une application console. Dans le didacticiel suivant, vous allez créer une bibliothèque de classes.

> [!div class="nextstepaction"]
> [Créer une bibliothèque de .NET Standard à l’aide de Visual Studio Code](library-with-visual-studio-code.md)
