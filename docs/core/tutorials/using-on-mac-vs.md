---
title: Bien démarrer avec .NET Core à l’aide de Visual Studio pour Mac
description: Cette rubrique vous guide lors de la création d’une application console simple à l’aide de Visual Studio pour Mac et de .NET Core.
ms.date: 12/19/2019
ms.openlocfilehash: 4cd7e311411bce62698e291e763227496877ea39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740494"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Bien démarrer avec .NET Core sur macOS à l’aide de Visual Studio pour Mac

Visual Studio pour Mac fournit un environnement de développement intégré (IDE) complet pour le développement d’applications .NET Core. Cet article vous guide à travers la construction d’une application de console simple en utilisant Visual Studio pour Mac et .NET Core.

> [!NOTE]
> Vos commentaires sont extrêmement précieux. Il existe deux moyens de transmettre vos commentaires à l’équipe de développement sur Visual Studio pour Mac :
>
> * Dans Visual Studio for Mac, sélectionnez **Help** > **Report a Problem** du menu ou **signalez un problème** à partir de l’écran De bienvenue, qui ouvrira une fenêtre pour le dépôt d’un rapport de bogue. Vous pouvez effectuer le suivi de vos commentaires dans le portail de la [communauté des développeurs](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Pour faire une suggestion, sélectionnez **Aide** > **Fournir une suggestion** dans le menu ou fournir une **suggestion** à partir de l’écran de bienvenue, qui vous mènera au studio visuel pour Mac Developer Community [page Web](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Conditions préalables requises

Voir l’article [.NET Core dependencies and requirements.](../install/dependencies.md?pivots=os-macos)

Consultez l’article [.NET Core Support](/visualstudio/mac/net-core-support) pour vous assurer que vous utilisez une version prise en charge de .NET Core.

## <a name="get-started"></a>Bien démarrer

Si vous avez déjà installé les composants requis et Visual Studio pour Mac, ignorez cette section et passez à la [création d’un projet](#creating-a-project). Suivez ces étapes pour installer les composants requis et Visual Studio pour Mac :

Téléchargez le [programme d’installation de Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Exécutez le programme d’installation. Lisez et acceptez le contrat de licence. Pendant l’installation, sélectionnez l’option d’installation de .NET Core. Vous avez la possibilité d’installer Xamarin, une technologie de développement d’application mobile multiplateforme. L’installation de Xamarin et de ses composants associés est facultative pour le développement .NET Core. Pour obtenir une vue d’ensemble du processus d’installation de Visual Studio pour Mac, consultez la [documentation de Visual Studio pour Mac](/visualstudio/mac/). Une fois l’installation terminée, démarrez l’IDE Visual Studio pour Mac.

## <a name="creating-a-project"></a>Création d'un projet

1. Sélectionnez **Nouveau** sur la fenêtre de départ.

   ![Bouton Nouveau sur l’écran Démarrer de Visual Studio pour Mac](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. Dans la boîte de dialogue **Nouveau projet**, sélectionnez **App** dans le nœud **.NET Core**. Sélectionnez le modèle **Application console** puis **Suivant**.

   ![Liste des modèles Nouveau projet](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. Si plusieurs versions de .NET Core sont installées, sélectionnez le framework cible pour votre projet.

1. Tapez « HelloWorld » comme **nom de projet**. Sélectionnez **Créer**.

   ![Boîte de dialogue de configuration de votre nouvelle application console](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. Attendez la restauration des dépendances du projet. Le projet comporte un seul fichier C#, *Program.cs*, contenant une classe `Program` avec une méthode `Main`. L’instruction `Console.WriteLine` affichera « Hello World! » dans la console lorsque l’application est exécutée.

   ![Fenêtre principale avec le fichier Program.cs ouvert](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a>Exécuter l’application

Exécutez l’application en mode débogage à l’aide de ⌘ ↵ (commande + entrée) ou en mode mise en production en utilisant ⌥ ⌘ ↵ (option + commande + entrée).

![Le volet de sortie de l’application affiche Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a>Étape suivante

La rubrique [Génération d’une solution .NET Core complète sur macOS à l’aide de Visual Studio pour Mac](using-on-mac-vs-full-solution.md) vous montre comment créer une solution complète .NET Core qui inclut une bibliothèque réutilisable et un test unitaire.
