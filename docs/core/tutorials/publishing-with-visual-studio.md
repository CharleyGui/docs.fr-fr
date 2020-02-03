---
title: Publier votre application de Hello World .NET Core avec Visual Studio
description: La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: a82934fd2ea9568681a3bec82c3b15513decc926
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741567"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a>Publier votre application de Hello World .NET Core avec Visual Studio

Dans [créer une application Hello World avec .net core dans Visual Studio](with-visual-studio.md), vous avez créé une application console Hello World. Dans [déboguer votre application Hello World avec Visual Studio](debugging-with-visual-studio.md), vous l’avez testée à l’aide du débogueur Visual Studio. Maintenant que vous savez qu’elle fonctionne comme prévu, vous pouvez la publier afin que les autres utilisateurs puissent l’exécuter. La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application. Pour déployer les fichiers, copiez-les sur l’ordinateur cible.

## <a name="publish-the-app"></a>Publier l'application

1. Vérifiez que Visual Studio génère la version release de votre application. Si nécessaire, modifiez le paramètre de configuration de la génération dans la barre d’outils de **Debug** en **Release**.

   ![Barre d’outils Visual Studio avec version Release sélectionnée](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Cliquez avec le bouton droit sur le projet **HelloWorld** (et non pas sur la solution HelloWorld) et sélectionnez **Publier** dans le menu. (Vous pouvez également sélectionner **publier HelloWorld** dans le menu principal **générer** .)

   ![Menu contextuel Publier de Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)
   
1. Sur la page **choisir une cible de publication** , sélectionnez **dossier**, puis créer un **Profil**.

   ![Choisir une cible de publication dans Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)
   
1. Dans la page de **publication**, sélectionnez **Publier**.

   ![Fenêtre Publier de Visual Studio](media/publishing-with-visual-studio/publish-page.png)
   
## <a name="inspect-the-files"></a>Inspecter les fichiers

Le processus de publication crée un déploiement dépendant du Framework, qui est un type de déploiement dans lequel l’application publiée s’exécute sur n’importe quelle plateforme prise en charge par .NET Core avec .NET Core installé sur le système. Les utilisateurs peuvent exécuter l’application publiée en double-cliquant sur l’exécutable ou en lançant la commande `dotnet HelloWorld.dll` à partir d’une invite de commandes.

Dans les étapes suivantes, vous allez examiner les fichiers créés par le processus de publication.

1. Ouvrez une invite de commandes.

   Pour ouvrir une invite de commandes, vous pouvez entrer une **invite de commandes** (ou **cmd** pour Short) dans la zone de recherche de la barre des tâches Windows. Sélectionnez l’application de bureau d' **invite de commandes** ou appuyez sur **entrée** si elle est déjà sélectionnée dans les résultats de la recherche.

1. Accédez à l’application publiée dans le sous-répertoire *bin\Release\netcoreapp3.1\publish* du répertoire du projet de l’application.

   ![Fenêtre de console affichant les fichiers publiés](media/publishing-with-visual-studio/published-files-output.png)

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

## <a name="additional-resources"></a>Ressources supplémentaires

- [Déploiement d’applications .NET Core](../deploying/index.md)
