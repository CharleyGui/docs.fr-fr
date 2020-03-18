---
title: Publiez votre application .NET Core Hello World avec Visual Studio
description: La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bdd6e28713bdece2bd144e6763bd84d719e91449
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156632"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a>Publiez votre application .NET Core Hello World avec Visual Studio

Dans [Créer une application Hello World avec .NET Core dans Visual Studio](with-visual-studio.md), vous avez construit une application de console Hello World. Dans [Debug votre application Hello World avec Visual Studio](debugging-with-visual-studio.md), vous l’avez testée à l’aide du debugger Visual Studio. Maintenant que vous savez qu’elle fonctionne comme prévu, vous pouvez la publier afin que les autres utilisateurs puissent l’exécuter. La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application. Pour déployer les fichiers, copiez-les sur la machine cible.

## <a name="publish-the-app"></a>Publier l’application

1. Vérifiez que Visual Studio génère la version release de votre application. Si nécessaire, modifiez le paramètre de configuration de la génération dans la barre d’outils de **Debug** en **Release**.

   ![Barre d’outils Visual Studio avec version Release sélectionnée](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Cliquez à droite sur le projet **HelloWorld** (pas la solution HelloWorld) et **sélectionnez Publier** dans le menu. (Vous pouvez également sélectionner **Publish HelloWorld** à partir du menu **Main Build.)**

   ![Menu contextuel Publier de Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)

1. Sur la **page Cible Pick,** sélectionnez **Folder,** puis sélectionnez **Create Profile**.

   ![Choisissez une cible de publication dans Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. Dans la page de **publication**, sélectionnez **Publier**.

   ![Fenêtre Publier de Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a>Inspecter les fichiers

Le processus de publication crée un déploiement dépendant du cadre, qui est un type de déploiement où l’application publiée s’exécute sur n’importe quelle plate-forme prise en charge par .NET Core avec .NET Core installé sur le système. Les utilisateurs peuvent exécuter l’application publiée en cliquant à deux clics sur l’exécutable ou en émettant la `dotnet HelloWorld.dll` commande à partir d’une invite de commande.

Dans les étapes suivantes, vous examinerez les fichiers créés par le processus de publication.

1. Ouvrez une invite de commandes.

   Une façon d’ouvrir une invite de commande est d’entrer **Command Prompt** (ou **cmd** pour faire court) dans la boîte de recherche sur la barre des tâches Windows. Sélectionnez l’application de bureau **Command Prompt,** ou appuyez **sur Enter** si elle est déjà sélectionnée dans les résultats de recherche.

1. Naviguez vers l’application publiée dans la *sous-direction* de l’annuaire du projet de l’application.

   ![Fenêtre de console affichant les fichiers publiés](media/publishing-with-visual-studio/published-files-output.png)

   Comme le montre l’image, la sortie publiée comprend les fichiers suivants :

      * *HelloWorld.deps.json*

         Il s’agit du fichier de dépendances en temps d’exécution de l’application. Il définit les composants .NET Core et les bibliothèques (y compris la bibliothèque de lien dynamique qui contient votre application) nécessaires pour exécuter l’application. Pour plus d’informations, voir [fichiers de configuration Runtime](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

      * *HelloWorld.dll*

         Il s’agit de la version de [déploiement dépendante](../deploying/deploy-with-cli.md#framework-dependent-deployment) du cadre de l’application. Pour exécuter cette bibliothèque `dotnet HelloWorld.dll` de lien dynamique, entrez à une invite de commande.

      * *HelloWorld.exe*

         Il s’agit de la version [exécutable dépendante](../deploying/deploy-with-cli.md#framework-dependent-executable) du cadre de l’application. Pour l’exécuter, entrez `HelloWorld.exe` à une invite de commande.

      * *HelloWorld.pdb* (facultatif pour le déploiement)

         C’est le fichier des symboles de débogé. Vous n’êtes pas obligé de déployer ce fichier avec votre application, même si vous devez l’enregistrer au cas où vous auriez à déboguer la version publiée de votre application.

      * *HelloWorld.runtimeconfig.json*

         Il s’agit du fichier de configuration du temps d’exécution de l’application. Il identifie la version de .NET Core sur laquelle votre application doit être exécutée. Vous pouvez également y ajouter des options de configuration. Pour plus d’informations, voir [paramètres de configuration .NET Core run-time](../run-time-config/index.md#runtimeconfigjson).

## <a name="additional-resources"></a>Ressources supplémentaires

- [.NET Déploiement d’applications de base](../deploying/index.md)
