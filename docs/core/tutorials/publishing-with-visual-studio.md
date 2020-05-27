---
title: Publier votre application de Hello World .NET Core avec Visual Studio
description: La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: e4ef8c12f3e52faa7cf09058a98abae65b0dcfce
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005091"
---
# <a name="tutorial-publish-a-net-core-console-application-with-visual-studio"></a>Didacticiel : publier une application console .NET Core avec Visual Studio

Ce didacticiel montre comment publier une application console afin que d’autres utilisateurs puissent l’exécuter. La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application. Pour déployer les fichiers, copiez-les sur l’ordinateur cible.

## <a name="prerequisites"></a>Prérequis

- Ce didacticiel fonctionne avec l’application console que vous créez dans [créer une application console .net core dans Visual Studio 2019](with-visual-studio.md).

## <a name="publish-the-app"></a>Publier l’application

1. Vérifiez que Visual Studio génère la version release de votre application. Si nécessaire, modifiez le paramètre de configuration de la génération dans la barre d’outils de **Debug** en **Release**.

   ![Barre d’outils Visual Studio avec version Release sélectionnée](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Cliquez avec le bouton droit sur le projet **HelloWorld** (et non sur la solution HelloWorld) et sélectionnez **publier** dans le menu.

   ![Menu contextuel Publier de Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)

1. Dans l’onglet **cible** de la page **publier** , sélectionnez **dossier**, puis cliquez sur **suivant**.

   ![Choisir une cible de publication dans Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. Dans l’onglet **emplacement** de la page **publier** , sélectionnez **Terminer**.

   ![Onglet emplacement de la page de publication de Visual Studio](media/publishing-with-visual-studio/publish-page-loc-tab.png)

1. Sous l’onglet **publier** de la fenêtre **publier** , sélectionnez **publier**.

   ![Fenêtre Publier de Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a>Inspecter les fichiers

Le processus de publication crée un déploiement dépendant du Framework, qui est un type de déploiement dans lequel l’application publiée s’exécute sur l’ordinateur sur lequel le Runtime .NET Core est installé. Les utilisateurs peuvent exécuter l’application publiée en double-cliquant sur l’exécutable ou en exécutant la `dotnet HelloWorld.dll` commande à partir d’une invite de commandes.

Dans les étapes suivantes, vous allez examiner les fichiers créés par le processus de publication.

1. Dans **Explorateur de solutions**, sélectionnez **Afficher tous les fichiers**.

1. Dans le dossier du projet, développez *bin/Release/netcoreapp 3.1/Publish*.

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="Explorateur de solutions l’indication des fichiers publiés":::

   Comme l’indique l’image, la sortie publiée comprend les fichiers suivants :

      * *HelloWorld.deps.json*

         Il s’agit du fichier de dépendances d’exécution de l’application. Il définit les composants .NET Core et les bibliothèques (y compris la bibliothèque de liens dynamiques qui contient votre application) nécessaires pour exécuter l’application. Pour plus d’informations, consultez [fichiers de configuration](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)de l’exécution.

      * *HelloWorld.dll*

         Il s’agit de la version de [déploiement dépendante du Framework](../deploying/deploy-with-cli.md#framework-dependent-deployment) de l’application. Pour exécuter cette bibliothèque de liens dynamiques, entrez `dotnet HelloWorld.dll` à l’invite de commandes.

      * *HelloWorld. exe*

         Il s’agit de la version [exécutable dépendante du Framework](../deploying/deploy-with-cli.md#framework-dependent-executable) de l’application. Pour l’exécuter, entrez `HelloWorld.exe` à l’invite de commandes.

      * *HelloWorld.pdb* (facultatif pour le déploiement)

         Il s’agit du fichier de symboles de débogage. Vous n’êtes pas obligé de déployer ce fichier avec votre application, même si vous devez l’enregistrer au cas où vous auriez à déboguer la version publiée de votre application.

      * *HelloWorld.runtimeconfig.json*

         Il s’agit du fichier de configuration au moment de l’exécution de l’application. Il identifie la version de .NET Core sur laquelle votre application doit être exécutée. Vous pouvez également y ajouter des options de configuration. Pour plus d’informations, consultez [paramètres de configuration du Runtime .net Core](../run-time-config/index.md#runtimeconfigjson).

## <a name="run-the-published-app"></a>Exécuter l’application publiée

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le dossier de *publication* , puis sélectionnez **copier le chemin d’accès complet**.

1. Ouvrez une invite de commandes et accédez au dossier de *publication* . Entrez `cd` , puis collez le chemin d’accès complet. Par exemple :

   ```
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. Exécutez l’application à l’aide de l’exécutable :

   1. Entrez `HelloWorld.exe` et appuyez sur entrée.

   1. Entrez un nom en réponse à l’invite, puis appuyez sur n’importe quelle touche pour quitter.

1. Exécutez l’application à l’aide de la `dotnet` commande :

   1. Entrez `dotnet HelloWorld.dll` et appuyez sur entrée.

   1. Entrez un nom en réponse à l’invite, puis appuyez sur n’importe quelle touche pour quitter.

## <a name="additional-resources"></a>Ressources supplémentaires

- [Déploiement d’applications .NET Core](../deploying/index.md)

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez publié une application console. Dans le didacticiel suivant, vous allez créer une bibliothèque de classes.

> [!div class="nextstepaction"]
> [Créer une bibliothèque .NET Standard dans Visual Studio](library-with-visual-studio.md)
