---
title: Créer une bibliothèque de classes .NET à l’aide de Visual Studio pour Mac
description: Découvrez comment créer une bibliothèque de classes .NET à l’aide de Visual Studio pour Mac.
ms.date: 11/30/2020
ms.openlocfilehash: 1b6b26de06d18d505fa6dde3ff9779a3dab3f1e6
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599297"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio-for-mac"></a>Didacticiel : créer une bibliothèque de classes .NET à l’aide de Visual Studio pour Mac

Dans ce didacticiel, vous allez créer une bibliothèque de classes qui contient une méthode de gestion de chaîne unique.

Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application. Si la bibliothèque cible .NET Standard 2,0, elle peut être appelée par n’importe quelle implémentation .NET (y compris .NET Framework) qui prend en charge .NET Standard 2,0. Si la bibliothèque cible .NET 5, elle peut être appelée par n’importe quelle application qui cible .NET 5. Ce didacticiel montre comment cibler .NET 5.

> [!NOTE]
> Vos commentaires sont extrêmement précieux. Il existe deux moyens de transmettre vos commentaires à l’équipe de développement sur Visual Studio pour Mac :
>
> - Dans Visual Studio pour Mac, sélectionnez **aide**  >  **signaler un problème** dans le menu ou **signaler un problème** dans l’écran d’accueil, qui ouvre une fenêtre pour l’enregistrement d’un rapport de bogue. Vous pouvez effectuer le suivi de vos commentaires dans le portail de la [communauté des développeurs](https://aka.ms/feedback/report?space=41).
> - Pour faire une suggestion, sélectionnez **aide**  >  **fournir une suggestion** dans le menu ou **fournissez une suggestion** sur l’écran d’accueil, qui vous amène à la [page Web de la communauté des développeurs Visual Studio pour Mac](https://aka.ms/feedback/suggest?space=41).

## <a name="prerequisites"></a>Prérequis

* [Installez Visual Studio pour Mac version 8,8 ou ultérieure](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Sélectionnez l’option d’installation de .NET Core. L’installation de Xamarin est facultative pour le développement .NET. Pour plus d’informations, consultez les ressources suivantes :

  * [Didacticiel : installer Visual Studio pour Mac](/visualstudio/mac/installation).
  * [Versions MacOS prises en charge](../install/macos.md).
  * [Versions .net prises en charge par Visual Studio pour Mac](/visualstudio/mac/net-core-support).

## <a name="create-a-solution-with-a-class-library-project"></a>Créer une solution avec un projet de bibliothèque de classes

Une solution Visual Studio sert de conteneur pour un ou plusieurs projets. Créez une solution et un projet de bibliothèque de classes dans la solution. Vous ajouterez ultérieurement des projets connexes à la même solution.

1. Démarrez Visual Studio pour Mac.

1. Dans la fenêtre Démarrer, sélectionnez **nouveau projet**.

1. Dans la boîte **de dialogue Choisir un modèle pour votre nouveau projet** , sélectionnez Bibliothèque de classes **Web et console**  >  **Library**  >  **Class Library**, puis sélectionnez **suivant**.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Boîte de dialogue Nouveau projet":::

1. Dans la boîte de dialogue **configurer votre nouvelle bibliothèque de classes** , choisissez **.net 5,0**, puis sélectionnez **suivant**.

1. Nommez le projet « StringLibrary » et la solution « ClassLibraryProjects ». Laissez **l’option créer un répertoire de projet dans le répertoire de la solution** sélectionnée. Sélectionnez **Create** (Créer).

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Options de la boîte de dialogue Nouveau projet dans Visual Studio pour Mac":::

1. Dans le menu principal, sélectionnez **Afficher**  >  la **solution**, puis sélectionnez l’icône d’ancrage pour maintenir le pavé ouvert.

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="Icône d’ancrage du panneau solution":::

1. Dans le panneau **solution** , développez le `StringLibrary` nœud pour afficher le fichier de classe fourni par le modèle, *Class1.cs*. <kbd>CTRL</kbd>+ cliquez sur le fichier, sélectionnez **Renommer** dans le menu contextuel, puis renommez le fichier *StringLibrary.cs*. Ouvrez le fichier et remplacez le contenu par le code suivant :

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. Appuyez sur <kbd>⌘</kbd><kbd>s</kbd> (<kbd>Command</kbd> + <kbd>s</kbd>) pour enregistrer le fichier.

1. Sélectionnez **Erreurs** dans la marge en bas de la fenêtre de l’IDE pour ouvrir le panneau **Erreurs**. Sélectionnez le bouton **Sortie de la build**.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="Marge inférieure de l’IDE Visual Studio pour Mac montrant le bouton Erreurs":::

1. **Build**  >  Dans le menu, sélectionnez Générer **générer tout** .

   La solution se génère. Le panneau de sortie de la build indique que la build a réussi.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="Volet Sortie de la build Visual Studio pour Mac du panneau Erreurs avec le message de réussite de la build":::

## <a name="add-a-console-app-to-the-solution"></a>Ajouter une application console à la solution

Ajoutez une application console qui utilise la bibliothèque de classes. L’application invite l’utilisateur à entrer une chaîne et signale si la chaîne commence par un caractère majuscule.

1. Dans le panneau **solutions** , cliquez sur la solution en <kbd>appuyant sur la touche Ctrl</kbd> `ClassLibraryProjects` . Ajoutez un nouveau projet d' **application console** en sélectionnant le modèle à partir des modèles d’application **Web et console**  >  **App** , puis sélectionnez **suivant**.

1. Sélectionnez **.net 5,0** comme **Framework cible** , puis cliquez sur **suivant**.

1. Nommez le projet **vitrine**. Sélectionnez **Créer** pour créer le projet dans la solution.

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="Ajouter un projet de démonstration":::

1. Ouvrez le fichier *Program.cs* . Remplacez le code par le code suivant :

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   Le programme invite l’utilisateur à entrer une chaîne. Il indique si la chaîne commence par une majuscule. Si l’utilisateur appuie sur la touche <kbd>entrée</kbd> sans entrer de chaîne, l’application se termine et la fenêtre de console se ferme.

   Le code utilise la variable `row` pour comptabiliser le nombre de lignes de données écrites dans la fenêtre de console. Lorsqu’il est supérieur ou égal à 25, le code efface la fenêtre de console et affiche un message à l’utilisateur.

## <a name="add-a-project-reference"></a>Ajouter une référence au projet

Initialement, le nouveau projet d’application console n’a pas accès à la bibliothèque de classes. Pour lui permettre d’appeler des méthodes dans la bibliothèque de classes, créez une référence de projet au projet de bibliothèque de classes.

1. Dans le panneau **solutions** , <kbd>cliquez</kbd>sur le nœud **dépendances** du nouveau projet **Showcase** . Dans le menu contextuel, sélectionnez **Ajouter une référence**.

1. Dans la boîte de dialogue **références** , sélectionnez **StringLibrary** , puis cliquez sur **OK**.

## <a name="run-the-app"></a>Exécuter l’application

1. <kbd>ctrl</kbd>cliquez sur le projet **Showcase** et sélectionnez **exécuter le projet** dans le menu contextuel.

1. Essayez le programme en entrant des chaînes et en appuyant sur <kbd>entrée</kbd>, puis appuyez sur <kbd>entrée</kbd> pour quitter.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="Fenêtre de console Visual Studio pour Mac montrant votre application en cours d’exécution":::

## <a name="additional-resources"></a>Ressources supplémentaires

* [Développer des bibliothèques avec l’interface CLI .NET](libraries.md)
* [Notes de publication de Visual Studio 2019 pour Mac](/visualstudio/releasenotes/vs2019-mac-relnotes)
* [.NET standard versions et les plateformes qu’ils prennent en charge](../../standard/net-standard.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez créé une solution et un projet de bibliothèque, et ajouté un projet d’application console qui utilise la bibliothèque. Dans le didacticiel suivant, vous allez ajouter un projet de test unitaire à la solution.

> [!div class="nextstepaction"]
> [Tester une bibliothèque de classes .NET à l’aide de Visual Studio pour Mac](testing-library-with-visual-studio-mac.md)
