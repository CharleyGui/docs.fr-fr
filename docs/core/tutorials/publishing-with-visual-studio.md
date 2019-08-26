---
title: Publier votre application .NET Core Hello World avec Visual Studio 2017
description: La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: f8c37f47cc8dfb999f2371773a50c2dd91e074a5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660476"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio-2017"></a>Publier votre application .NET Core Hello World avec Visual Studio 2017

Dans [Générer une application C# Hello World avec .NET Core dans Visual Studio 2017](with-visual-studio.md) ou [Générer une application Visual Basic Hello World avec .NET Core dans Visual Studio 2017](vb-with-visual-studio.md), vous avez généré une application console Hello World. Dans [Déboguer votre application C# Hello World avec Visual Studio 2017](debugging-with-visual-studio.md), vous l’avez testée à l’aide du débogueur Visual Studio. Maintenant que vous savez qu’elle fonctionne comme prévu, vous pouvez la publier afin que les autres utilisateurs puissent l’exécuter. La publication crée l’ensemble des fichiers nécessaires pour exécuter votre application ; vous pouvez les déployer en les copiant sur une machine cible.

Pour publier et exécuter votre application : 

1. Vérifiez que Visual Studio génère la version release de votre application. Si nécessaire, modifiez le paramètre de configuration de la génération dans la barre d’outils de **Debug** en **Release**.

   ![Barre d’outils Visual Studio avec version Release sélectionnée](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Cliquez avec le bouton droit sur le projet **HelloWorld** (et non pas sur la solution HelloWorld) et sélectionnez **Publier** dans le menu. Vous pouvez également sélectionner **Publier HelloWorld** à partir du menu **Build** principal de Visual Studio.

   ![Menu contextuel Publier de Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)

   ![Fenêtre Publier de Visual Studio](media/publishing-with-visual-studio/publish-settings-window.png)

1. Ouvrez une fenêtre de console. Par exemple, dans la zone de texte **Tapez ici pour effectuer une recherche** dans la barre des tâches Windows, entrez `Command Prompt` (ou `cmd` en abrégé) et ouvrez une fenêtre de console en sélectionnant l’application de poste de travail **Invite de commandes** ou en appuyant sur Entrée si elle est sélectionnée dans les résultats de la recherche.

1. Accédez à l’application publiée dans le sous-répertoire `bin\release\PublishOutput` du répertoire de projet de votre application. Comme le montre l’illustration suivante, la sortie publiée comprend les quatre fichiers suivants :

      * *HelloWorld.deps.json*

         Fichier de dépendances de runtime de l’application. Il définit les composants .NET Core et les bibliothèques (dont la bibliothèque de liens dynamiques qui contient votre application) nécessaires pour exécuter votre application. Pour plus d’informations, consultez [Fichiers de configuration du runtime](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).
 
      * *HelloWorld.dll*

         Fichier qui contient votre application. Il s’agit d’une bibliothèque de liens dynamiques qui peut être exécutée en entrant la commande `dotnet HelloWorld.dll` dans une fenêtre de console. 

      * *HelloWorld.pdb* (facultatif pour le déploiement)

         Fichier qui contient des symboles de débogage. Vous n’êtes pas obligé de déployer ce fichier avec votre application, même si vous devez l’enregistrer au cas où vous auriez à déboguer la version publiée de votre application.

      * *HelloWorld.runtimeconfig.json*

         Fichier de configuration du runtime de l’application. Il identifie la version de .NET Core sur laquelle votre application doit être exécutée. Pour plus d’informations, consultez [Fichiers de configuration du runtime](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).  

   ![Fenêtre de console affichant les fichiers publiés](media/publishing-with-visual-studio/published-files-output.png)

Le processus de publication crée un déploiement dépendant du framework ; qui est un type de déploiement où l’application publiée s’exécute sur toutes les plateformes prises en charge par .NET Core, avec .NET Core installé sur le système. Les utilisateurs peuvent exécuter votre application en émettant la commande `dotnet HelloWorld.dll` à partir d’une fenêtre de console.

Pour plus d’informations sur la publication et le déploiement d’applications .NET Core, consultez [Déploiement d’applications .NET](../deploying/index.md).
