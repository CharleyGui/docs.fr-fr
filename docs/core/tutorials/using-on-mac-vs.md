---
title: Bien démarrer avec .NET Core sur macOS à l’aide de Visual Studio pour Mac
description: Cette rubrique vous guide lors de la création d’une application console simple à l’aide de Visual Studio pour Mac et de .NET Core.
author: mairaw
ms.date: 07/11/2019
ms.custom: seodec18
ms.openlocfilehash: a6d58d2a54ce9742542a3f7e5c9378be89b8f89a
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870542"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Bien démarrer avec .NET Core sur macOS à l’aide de Visual Studio pour Mac

Visual Studio pour Mac fournit un environnement de développement intégré (IDE) complet pour le développement d’applications .NET Core. Cette rubrique vous guide lors de la création d’une application console simple à l’aide de Visual Studio pour Mac et de .NET Core.

> [!NOTE]
> Vos commentaires sont extrêmement précieux. Il existe deux moyens de transmettre vos commentaires à l’équipe de développement sur Visual Studio pour Mac :
> * Dans Visual Studio pour Mac, sélectionnez **Aide** > **Signaler un problème** dans le menu ou **Signaler un problème** sur l’écran d’accueil, ce qui ouvre une fenêtre permettant de soumettre un rapport de bogue. Vous pouvez effectuer le suivi de vos commentaires dans le portail de la [communauté des développeurs](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Pour soumettre une suggestion, sélectionnez **Aide** > **Faire une suggestion** dans le menu ou **Faire une suggestion** sur l’écran d’accueil, ce qui vous amène à la [page web de la communauté des développeurs Visual Studio pour Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Prérequis

Consultez la rubrique [Prérequis de .NET Core sur Mac](../../core/macos-prerequisites.md).

Consultez le guide de [support de .NET Core](https://docs.microsoft.com/visualstudio/mac/net-core-support?view=vsmac-2019) pour vous assurer que vous utilisez une version prise en charge de .NET Core.

## <a name="get-started"></a>Prise en main

Si vous avez déjà installé les composants requis et Visual Studio pour Mac, ignorez cette section et passez à la [création d’un projet](#creating-a-project). Suivez ces étapes pour installer les composants requis et Visual Studio pour Mac :

Téléchargez le [programme d’installation de Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Exécutez le programme d’installation. Lisez et acceptez le contrat de licence. Pendant l’installation, sélectionnez l’option d’installation de .NET Core. Vous avez la possibilité d’installer Xamarin, une technologie de développement d’application mobile multiplateforme. L’installation de Xamarin et de ses composants associés est facultative pour le développement .NET Core. Pour obtenir une vue d’ensemble du processus d’installation de Visual Studio pour Mac, consultez la [documentation de Visual Studio pour Mac](/visualstudio/mac/). Une fois l’installation terminée, démarrez l’IDE Visual Studio pour Mac.

## <a name="creating-a-project"></a>Création d'un projet

1. Sélectionnez **Nouveau** dans la fenêtre Démarrer.

   ![Bouton Nouveau sur l’écran Démarrer de Visual Studio pour Mac](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. Dans la boîte de dialogue **Nouveau projet**, sélectionnez **App** dans le nœud **.NET Core**. Sélectionnez le modèle **Application console** puis **Suivant**.

   ![Liste des modèles Nouveau projet](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. Si plusieurs versions de .NET Core sont installées, sélectionnez le framework cible pour votre projet.

1. Tapez « HelloWorld » comme **nom de projet**. Sélectionnez **Créer**.

   ![Boîte de dialogue de configuration de votre nouvelle application console](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. Attendez la restauration des dépendances du projet. Le projet comporte un seul fichier C#, *Program.cs*, contenant une classe `Program` avec une méthode `Main`. L’instruction `Console.WriteLine` affichera « Hello World! » dans la console lorsque l’application est exécutée.

   ![Fenêtre principale avec le fichier Program.cs ouvert](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a>Exécuter l'application

Exécutez l’application en mode débogage à l’aide de ⌘ ↵ (commande + entrée) ou en mode mise en production en utilisant ⌥ ⌘ ↵ (option + commande + entrée).

![Le volet de sortie de l’application affiche Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a>Étape suivante

La rubrique [Génération d’une solution .NET Core complète sur macOS à l’aide de Visual Studio pour Mac](using-on-mac-vs-full-solution.md) vous montre comment créer une solution complète .NET Core qui inclut une bibliothèque réutilisable et un test unitaire.
